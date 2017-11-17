![Logo](https://github.com/redhatdemocentral/rhcs-destinasia-rules-demo/blob/master/docs/demo-images/destinasia-logo.png)

Destinasia Travel Rules Demo
============================
Ready to get hands-on with AppDev in the Cloud with container based services? 

Experience the wonders of Red Hat's open technologies for cloud-based container application development by integrating multiple services in to a polyglot cloud solution. In this project you're a developer working for Destinaisa, a travel agency that needs to setup its online bookings applications backend services. Using the OpenShift Container Platform for deploying this solution, start by installing JBoss BRMS to work on the Destinasia travel discount rules. Once deployed, you leverage Ansible playbooks to see infrastructure automation in action. Each playbook deploys a new container-based service to support flight, hotel, car and discount rule queries from your application. In total this integration projects running 6 container-based applications or services and final testing is done with a REST client. Validation is sending a booking message to the integration end-point and verifying the discounts provided by the integrated services.

Need hands-on, step-by-step instructions? Experience the [free online workshop](http://appdevcloudworkshop.github.io).

This demo is also available on the [Red Hat Product Demo System](https://rhpds.redhat.com) for partners with access and found in
'Catalog' -> 'AppDev in the Cloud' -> 'Agile Cloud Integration with Destinasia'.


Step 1: Install OpenShift Container Platform
--------------------------------------------
This demo is to install JBoss BRMS with Destinasia Travel discount rules in the Cloud based on leveraging any Red Hat OpenShift container based platform, such as:

 - [Red Hat Container Platform (OCP)](https://github.com/redhatdemocentral/ocp-install-demo)

This delivers a fully configured container platform with all the available product streams and templates.

Another option is:

 - [Red Hat Container Development Kit (CDK) using Minishift](https://developers.redhat.com/products/cdk/overview)
  
This requires adding ASP.NET core stream manually, a task outside the scope of this project.


Step 2: Install JBoss BRMS on OpenShift
---------------------------------------
1. First ensure you have an OpenShift container based installation, such as one of the following installed first:

  - [OCP Install Demo](https://github.com/redhatdemocentral/ocp-install-demo)

  - or your own OpenShift installation.

2. [Download and unzip this demo.](https://github.com/redhatdemocentral/rhcs-destinasia-rules-demo/archive/master.zip)

3. Download JBoss EAP & JBoss BRMS, add to installs directory (see installs/README).

4. Run 'init.sh' or 'init.bat' file. 'init.bat' must be run with Administrative privileges:
```
   # The installation needs to be pointed to a running version
   # of OpenShift, so pass an IP address such as:
   #
   $ ./init.sh 192.168.99.100  # example for OCP.
```

Now log in to JBoss BRMS and start developing containerized rules projects (the address will be generated by the init script):

  - http://destinasia-rules-demo-appdev-in-cloud.192.168.99.100.nip.io/business-central ( u:erics / p:jbossbrms1! )


Step 3: Ansible Playbooks for Automated Service Deployment on OpenShift
-----------------------------------------------------------------------
Click on [link to instructions for Ansible Playbooks Service Deployment](https://github.com/redhatdemocentral/rhcs-destinasia-rules-demo/blob/master/support/playbooks/deploy-ocp-services/README.md) to deploy:

1. Rules from container JBoss BRMS to xPaaS Decision Server

2. .Net service to container

3. Java service to xPaaS EAP Server

4. PHP service to container

5. Fuse service to xPaaS Integration Server


Notes
-----
This project can be installed on any OpenShift platform, such as the OpenShift Container Platform. It's possible to install it on any available installation by pointing this installer to an OpenShift IP address:
```
  $ ./init.sh IP
```

-----

The rule test you find in the project is BROKEN... guess what, you need to fix that! Hint for the fix is that the flights are all
Asian destinations, but the test uses an unknown destination for the rules. Can you fix it?

-----

To clone a repository in the running container, the following actions would need to occur from a developer's machine.

1. Execute port forwarding through the OpenShift CLI. This will open a tunnel between the developer's machine and the pod through the OpenShift API pod proxy. The command window will block while the session is open:

   ```
   # Read-write access to repo on port 8001.
   #
   $ oc port-forward $(oc get pod -l=deploymentconfig=destinasia-rules-demo --template='{{ range .items }} {{ .metadata.name }} {{ end }}') 9418:9418
   ```

2. Clone the repository. In another window, clone the remote repository:

   ```
   # Read access to repo on port 9418.
   #
   $ git clone git://localhost:9418/destinasia 
   ```

-----


Supporting Articles
-------------------
- [AppDev in the Cloud self-paced, free, online workshop](http://www.schabell.org/2017/06/appdev-cloud-self-paced-free-online-workshop.html)

- [Boston JUG - Evening of AppDev in the Cloud Workshop](http://www.schabell.org/2017/06/boston-jug-evening-of-appdev-cloud-workshop.html)

- [Get hands-on with AppDev Cloud free online workshop.](http://appdevcloudworkshop.github.io)

- [App Dev in the Cloud, a Red Hat Cloud Suite workshop](https://appdevcloudworkshop.github.io/#/)

- [App Dev in the Cloud: How To Run JBoss BRMS in a Container](http://www.schabell.org/2016/12/appdev-cloud-howto-run-jboss-brms-in-container.html)

- [Real App Dev in the Cloud with JBoss BRMS Install Demo](http://www.schabell.org/2016/03/real-appdev-in-cloud-jboss-brms-install-demo.html)


Released versions
-----------------
See the tagged releases for the following versions of the product:

- v1.4 - JBoss BRMS 6.4.0, JBoss EAP 7.0.0 with Destinasia Travel discount rules running on any given OpenShift installation, Ansible playbooks for automation of service deployments (PHP, Java, Rules, .Net, Fuse) and available on CDK with Minishift.

- v1.3 - JBoss BRMS 6.4.0, JBoss EAP 7.0.0 with Destinasia Travel discount rules running on any given OpenShift installation, Ansible playbooks for automation of service deployments (PHP, Java, Rules, .Net, Fuse) and available on RHPDS.

- v1.2 - JBoss BRMS 6.4.0, JBoss EAP 7.0.0 with Destinasia Travel discount rules running on any given OpenShift installation and Ansible playbooks for automation of service deployments (PHP, Java, Rules, .Net, Fuse).

- v1.1 - JBoss BRMS 6.4.0, JBoss EAP 7.0.0 with Destinasia Travel discount rules running on any given OpenShift installation and port forwarding for git repo access configured.

- v1.0 - JBoss BRMS 6.4.0, JBoss EAP 7.0.0 with Destinasia Travel discount rules running on any given OpenShift installation.


![Pods](https://github.com/redhatdemocentral/rhcs-destinasia-rules-demo/blob/master/docs/demo-images/destinasia-brms-pods.png)

![Rules](https://github.com/redhatdemocentral/rhcs-destinasia-rules-demo/blob/master/docs/demo-images/destinasia-travel-discount-rules.png)

![Deployments](https://github.com/redhatdemocentral/rhcs-destinasia-rules-demo/blob/master/docs/demo-images/destinasia-services-deployments.png)

![RHPDS](https://github.com/redhatdemocentral/rhcs-destinasia-rules-demo/blob/master/docs/demo-images/rhpds-destinasia.png)

![Cloud Suite](https://github.com/redhatdemocentral/rhcs-destinasia-rules-demo/blob/master/docs/demo-images/rhcs-arch.png)
