---
title: "Ubuntu 9.10 Server - how do setup Remote Desktop / VNC via SSH + command line"
date: 2010-02-21
forum: Server Platforms
---

### Post by o6uoq on 2010-02-21
Hi,

I am playing around with the idea of being able to use a cloud or instance based service to install Ubuntu 9.10 Server. This will enable me to have remote access via SSH command line.

So far, I've installed Ubuntu 9.10 Server + Ubuntu Desktop to a virtual machine. I can access this via SSH and locally via the desktop. However, in the real environment the only access I am going to have initially is via SSH.

I would like to be able to connect using Windows Remote Desktop or VNC (whichever is easier and most importantly - most secure) to the machine.. even though the desktop is on there, I need to somehow configure the remote access all from the command line.

I've had a read of various forums and have been trawling support forums for days but can't find a working solution for 9.10 Server or that fits my situation above where I will not have any physical access to the desktop or machine to configure remote desktop. It all has to be done via SSH/command line.

Any help is greatly appreciated :)

---

### Post by o6uoq on 2010-02-21
I've found a way of accessing it installing FreeNX Server on the box, then using the NX NoMachine client.. this connects over SSH on port 22, and is secure.

This will do me fine unless there is a way to do it which allows me to use Windows RDP as the client? and I configure/setup the box via SSH/command line to begin with?

Many thanks.

---

### Post by joberly on 2010-02-21
If you *really* want to use the windows RDP client, you need a solution like [XRDP]("http://xrdp.sourceforge.net/"). Is there any specific reason why you have to use the Windows RDP client? Just curious, because there are many other options out there if you can simply use another protocol like VNC instead. (Like you have done with FreeNX)

---

### Post by o6uoq on 2010-03-02
I want RDP just for simplicity..

---

### Post by alienConcept on 2010-03-12
Hi,

Have you looked at ssh X forwarding and port forwarding ?

ssh has the ability to forward X requests and ports from the local server to your local.

If for example you had [webmin]("http://www.webmin.com") running on the server limited to localhost only (for security reasons) you could login with the following:

ssh [ip of machine] -L 10000:127.0.0.1:10000

then use [https://localhost:10000](https://localhost:10000) to get to the webmin interface as you have mapped port 10000 of [ip of machine] to your localport 10000.

([puTTY]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/") supports port forwarding if you are on windows)

also if you use X forwarding any command you issue on the remote machine that requires an X server will display on your local X server.

([Xming]("http://www.straightrunning.com/XmingNotes/") is an X server for windows)

There are a few arguments about not running a gui on servers, but sometimes it is handy :-) ([https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI))

If you use freeNX (or the non free version) the speed is better than VNC - possibly better than RDP when you consider that all traffic is encrypted using ssh, this is the best option if you want to a remote desktop. Install instructions here [http://www.ubuntugeek.com/how-to-install-freenx-server-and-client-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-freenx-server-and-client-in-ubuntu-9-10-karmic.html)

---

