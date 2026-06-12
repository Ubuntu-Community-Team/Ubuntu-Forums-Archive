---
title: "Whats the paradigm behind openstack,maas juju and MySQL workings?"
date: 2014-10-08
forum: Ubuntu Cloud and Juju
---

### Post by lightman2 on 2014-10-08
I have been tasked to demonstrate database as a service using openstack now i am not familiar with a lot things starting with ubuntu server itself however i have managed to setup the server and installed Maas although importing boot images has been failling.I just want to know how best i make this demonstration work.

---

### Post by slickymaster on 2014-10-08
*Moved to the ***Ubuntu Cloud and Juju*** sub-forum*

---

### Post by tgalati4 on 2014-10-08
Abstraction comes to mind.  The end user can purchase a database as a service and not worry about what hardware it runs on.  It's cloud computing on steroids.  Instead of buying a virtual machine in the cloud, you are now just buying the service without care of the machine.  So now services are abstracted from the virtual machines they run on which are abstracted from the actual metal (bare server hardware) that they run on.  It's abstraction^2.  Some call it [Service Orchestration]("https://help.ubuntu.com/community/Orchestra/Overview").  Others think we are moving toward [Skynet]("http://en.wikipedia.org/wiki/Skynet_%28Terminator%29").  I have a nice, purple tee shirt that shows the paradigm.  Anyone have a graphic of that?

Regarding your question (and this sounds like a homework assignment), there is a lot of reading involved.  Have you gone through the [MAAS]("https://help.ubuntu.com/community/UbuntuCloudInfrastructure") documentation?

Have you described a Use Case as to how a (simple) user could purchase a database service using this infrastructure?  I think that is what is being asked.

---

### Post by lightman2 on 2014-10-08
Thanks so much for your explanation it really mind opening.Yes i have gone through the Maas documentation and have done as suggested but i can not still import the boot images,my main concern is how to picture the all the environment and the application that shall offer the service to the user.it is a undergraduate project am working on.Atleast am getting to be familiar with the ubuntu and its commands.I normally work in windows using Wamp server.

---

### Post by tgalati4 on 2014-10-08
Fortunately, nothing in Windows will help you with this.

What are the specific error messages that you are getting?  What exactly are these boot images of?

---

### Post by lightman2 on 2014-10-08
Some cluster controllers are missing boot images.  Either the import task has not been initiated (for each cluster, the task must be [initiated by hand]("http://10.10.16.231/MAAS/clusters/") the first time), or the import task failed.

---

### Post by bmullan2 on 2014-10-26
Maybe you have already looked at this but if not read thru it and give it a spin:

[https://github.com/Ubuntu-Solutions-Engineering/openstack-installer](https://github.com/Ubuntu-Solutions-Engineering/openstack-installer)

---

