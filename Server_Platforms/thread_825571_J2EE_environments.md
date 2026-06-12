---
title: "J2EE environments"
date: 2008-06-11
forum: Server Platforms
---

### Post by leg on 2008-06-11
Hi,

   I need to set up and use a J2ee environment so that I can practice developing with it. What is the best way to get j2ee set up and running with Ubuntu. I have looked in the repositories but the version in there seems to be running a little behind the current release. I also want to install the Spring framework and have a look at that also. Basically I want to become aquainted with as much of this area as possible. I am a fairly proficcient Java programmer not certified at the moment but taking the exam again soon and I am looking to add the server element to that knowledge.

I have installed NetBeans, which I love, and wonder how easy it is to use Tomcat with it. Apache and MySql are installed and working nicely and I currently develop php backed sites.

Any help/advice/links are greatly appreciated.

---

### Post by molotov00 on 2008-06-11
Use the repositories. If you encounter problems ppl will be able to help. Also, they have been tested... but I assumed you knew that.

---

### Post by leg on 2008-06-12
ok I have installed tomcat and it is working but I think I have done something wrong. To start tomcat I had to change the permissions of the file logs/catilina.out before the server would start. Should I have had to do that or have I made an error in the installation.

---

### Post by leg on 2008-06-13
I have just come across a module called JServ for apache. Does this  add a servlet container to Apache. I would install and test but I am not on my Linux machine at the moment.

---

### Post by sgordon on 2008-06-13
Hi

JServ is (was) a connector to allow Apache to talk to a servlet container, such as Tomcat (so you need both). This has now been superceeded by mod_jk.
For a simple deployment (during dev and even some production layouts) Tomcat should be fine on its own.

  Si

---

### Post by leg on 2008-06-13
> **sgordon said:**
> Hi

JServ is (was) a connector to allow Apache to talk to a servlet container, such as Tomcat (so you need both). This has now been superceeded by mod_jk.
For a simple deployment (during dev and even some production layouts) Tomcat should be fine on its own.

  SiThanks for answering sgordon but I was wondering about this and maybe you can explain it for me. Tomcat seems to be perfectly fine on its own and can serve http requests itself. So my question is why would you want to connect it to Apache server in the first place? Is it because of all the other available functionality Apache has?

---

### Post by wbrown on 2008-06-13
Greetings leg:

Apache is more effecient for serving static content (static html pages, images and files without java code).  Tomcat should be used to serve all java files (jsp's and servlets).  You usually run apache in front of tomcat and use mod_jk or mod_proxy to serve dynamic java content from tomcat.  mod_jk seems to be the preferred choice for setting this up.  Here is the official link to the tutorials.  [http://tomcat.apache.org/connectors-doc/index.html](http://tomcat.apache.org/connectors-doc/index.html) .  It did take me several attempts to get the setup working but now that I have apache serving static content and tomcat serving dynamic java content, my pages load very quickly.  

HTH
Bill.

---

### Post by windependence on 2008-06-14
> **leg said:**
> Hi,

   I need to set up and use a J2ee environment so that I can practice developing with it. What is the best way to get j2ee set up and running with Ubuntu. I have looked in the repositories but the version in there seems to be running a little behind the current release. I also want to install the Spring framework and have a look at that also. Basically I want to become aquainted with as much of this area as possible. I am a fairly proficcient Java programmer not certified at the moment but taking the exam again soon and I am looking to add the server element to that knowledge.

I have installed NetBeans, which I love, and wonder how easy it is to use Tomcat with it. Apache and MySql are installed and working nicely and I currently develop php backed sites.

Any help/advice/links are greatly appreciated.

Remember, you can always install the official Sun packages if you want. You can even compile them yourself and they will be optimized for your machine. You don't have to use the Ubuntu packages.

-Tim

---

### Post by leg on 2008-06-14
Thanks for all the comments they are useful. I am currently struggling with the set up of Tomcat and getting errors when it tries to compile so it is back to the docs for me.
[edit]
Well I am up and running now and my problems were related to file permissions on the work and log directories which I solved by giving my user account access to. I can't help that I have done this incorrectly and that I should have a tomcat user/group to add my user name to instead. Oh well I will keep investigating and see what I can find.

---

