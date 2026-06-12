---
title: "Sophos AV GUI"
date: 2010-08-09
forum: Security
---

### Post by GrumpyBum on 2010-08-09
Hello All,

I have downloaded a trial of Sophos Anti Virus for Linux and I am having issues accessing the GUI for this system.
I can access the GUI on the Ubuntu KDE desktop, but I am also running a web server and do not want to install KDE on this but want access to the GUI.

The GUI is [http://localhost:8081/](http://localhost:8081/) and I am trying to access this on the Ubuntu 10.04 server from a Ubuntu 9.04 Desktop.

If anyone has experience with this then please help.....

Firstly, I am running Shorewall on this server with the following entry to cater for this,
*ACCEPT  net  $FW  tcp  8081  8081*
However I cannot access [http://ubuntuserver:8081](http://ubuntuserver:8081)
This is also un-accessible if I stop (turn off) the firewall on the server.

Note, there is only 1 network adapter on this server. Currently I am able to access tcp ports 22, 25, and 80 without fault.

Can can confirm that the port tcp/8081 is open on the systems I try to access the server from, been the Ubuntu 9.04 desktop as well as a Windows 7 desktop.

At this time, I cannot even confirm the AntiVirus is working properly without accessing this GUI using a web browser.

I have downloaded and accessed the Sophos admin guide from [www.sophos.com](www.sophos.com) but this holds characters not compatible with EN-AU language package. This is unreadable from both my Ubuntu desktop and Windows desktop.

Sophos is install and running but I need to access the GUI to get additional data on this.
As there is a graphical system on this GUI it will be great to get access with the capabilities of the localhost.

**Your help is much appreciated. Thank you.**

---

### Post by OpSecShellshock on 2010-08-09
Could you establish an ssh session first and then view the page locally once you're in?

---

### Post by Jeroensum on 2010-08-09
You need to check if sophos is accepting connections from other hosts than localhost on 8081, the fact that the port is open and you can telnet to it doesn't always mean the application behind it will accept the connection.

If you are on a lan and the bandwith will allow it, try to run the kde app trough ssh (from a linux box):

ssh -YC ubuntuserver

Then run the desktopclient binary and wait a while, remote X is not the fastest (or best) solution as far as running remote apps goes, but may help you to troubleshoot this problem quickly :-)

---

### Post by GrumpyBum on 2010-08-10
Hi All,

Thank you for your replies, currently I have accessed this via SSH and installed the Lynx browser to the server. This has given my the information I need from Sophos.

I am still working on getting full GUI access to this instead of using the text based browser, but I now have some more options to look into with the information you have provided.

Many thanks, I will post a full solution soon once I have improved on this one.
Your responses have been a huge help.

---

### Post by GrumpyBum on 2010-08-11
Hello All,

For anyone else with this issue, Sophos is setup to access this remotely via port 8082.
Port 8081 will only work from the localhost.

I have opened port 8082 in the firewall and this is running great.  :D

More information here, [http://www.sophos.com/support/knowledgebase/article/14587.html](http://www.sophos.com/support/knowledgebase/article/14587.html)

Thanks again everyone.

---

