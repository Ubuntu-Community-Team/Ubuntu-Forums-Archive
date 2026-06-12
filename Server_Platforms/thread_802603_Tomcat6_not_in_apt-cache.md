---
title: "Tomcat6 not in apt-cache"
date: 2008-05-21
forum: Server Platforms
---

### Post by MarioFromBelgium on 2008-05-21
Hi,

I need to install TOMCAT 6 but it is not in my apt-cache.
What am I doing wrong?

Best regards

---

### Post by MarioFromBelgium on 2008-05-23
Me again,

does this mean that it isn't yet put in the package. and that I will have to download the files and compile the stuff myselves?

Or so I have to add a source for apt-get to look in?

Mario

---

### Post by Asham on 2008-07-03
Yes, I believe that is correct. Don't know why it hasn't been updated to version 6. It's been out for some quite time now.

---

### Post by MarioFromBelgium on 2008-07-04
Thx.

I have downloaded the tar and installed it myself.
I think the tomcat-guys should make sure the up to date version is available in apt-get for debian.

I know there (are?) have been some problems with versions 5 that were installed through apt-get. Maybe thats the reason why ver6 is delayed.

Since I installed the server myself and got it running I can't imaging what the problem could be with apt-get. A basic Tomcat-server is easy to install and configure!??

---

### Post by Asham on 2008-07-04
I must be some incompatibility issue or perhaps version 6 has stability issues? Not that I've noticed any. 
Maybe for next Ubuntu release Tomcat 6 will be available from apt-get! :)

---

### Post by Asham on 2008-10-30
Update: 

Tomcat 6 *is* in the repositories for Ubuntu 8.10!! =D> :-)

---

### Post by MarioFromBelgium on 2008-10-31
Hi Asham,

thanks for the info.
I'm migrating (big word for my small testserver) to new (actually its older) hardware. I will be using 8.10 but planned to install from TAR.

Have you tested the Tomcat-install form apt-get? Did it work?
I know there were some issues with Tomcat 5 (or something) when installed from apt-get.

Mario

---

### Post by Asham on 2008-10-31
Hello Mario,

Yes, I've successfully installed Tomcat 6 with apt-get on my Kubuntu box. With that said, I've only tested that it serves JSPs, which it does. I haven't deployed or tried anything else besides the standard installation files yet.

/Adam

---

