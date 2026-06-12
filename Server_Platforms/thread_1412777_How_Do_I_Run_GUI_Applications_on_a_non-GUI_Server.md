---
title: "How Do I Run GUI Applications on a non-GUI Server"
date: 2010-02-21
forum: Server Platforms
---

### Post by decatur-linux on 2010-02-21
If I install an Ubuntu server as an **Application server** and install the applications [such as OpenOffice, Skype, etc.] on the server and access that server with a **thin client**, how do these applications work if the server has no **Desktop** or **GUI** installed?

---

### Post by stlsaint on 2010-02-21
Im not sure your fully tracking how an [application server]("http://en.wikipedia.org/wiki/Application_server") would work in this particular situation. You are wanting a [LTSP]("http://en.wikipedia.org/wiki/Ltsp") setup.

---

### Post by cariboo on 2010-02-21
I have iso's of many install disks for Windows programs, I just mount the iso in a shared directory, then just navigate to the directory and double click the setup file.

---

### Post by decatur-linux on 2010-02-21
> **stlsaint said:**
> Im not sure your fully tracking how an [application server]("http://en.wikipedia.org/wiki/Application_server") would work in this particular situation. You are wanting a [LTSP]("http://en.wikipedia.org/wiki/Ltsp") setup.

You are correct, stlsaint.  The Linux Terminal Server Project [LTSP] server is what I want...and what I meant by **Application server**.  I have not researched it, but it appears to be software that would be added to a standard Ubuntu server...or could be installed at once using the Alternate CD.  I see that it provides for the installation of X, which would provide the GUI for the applications.

Question: instead of hard-wiring the terminals through a switch, could you not login using SSH/VNC, and be able to access the server remotely?

Thanks for your assistance.

---

### Post by stlsaint on 2010-02-22
> 

Question: instead of hard-wiring the terminals through a switch, could you not login using SSH/VNC, and be able to access the server remotely?

Thanks for your assistance.

in a ltsp setup im not sure but i would think not considering you would have to setup a wireless network in which im not sure thin clients have that capability but again i have not used it myself so im not sure. Now if you were to use a normal system (not think client) than yes you may.

---

### Post by haddog on 2010-04-07
> **decatur-linux said:**
> You are correct, stlsaint.  The Linux Terminal Server Project [LTSP] server is what I want...and what I meant by **Application server**.  I have not researched it, but it appears to be software that would be added to a standard Ubuntu server...or could be installed at once using the Alternate CD.  I see that it provides for the installation of X, which would provide the GUI for the applications.

Question: instead of hard-wiring the terminals through a switch, could you not login using SSH/VNC, and be able to access the server remotely?

Thanks for your assistance.

Check this out: Thin Clients Booting over a Wireless Bridge

[http://www.linuxjournal.com/article/9850](http://www.linuxjournal.com/article/9850)

---

### Post by tgalati4 on 2010-04-07
Yes, you can install gui apps on the server.  Xorg dependencies  will get installed. Just use ssh with x-forwarding:


ssh -2 -Y decatur@alabama

---

