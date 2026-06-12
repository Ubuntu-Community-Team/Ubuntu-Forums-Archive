---
title: "Terminal Server"
date: 2006-09-01
forum: Server Platforms
---

### Post by alecjw on 2006-09-01
Is there an Ubuntu terminal server?
If so, how do I get it?

---

### Post by richardward101 on 2006-09-01
What exactly is it you want to do, I assume that you want to have a ubuntu server that allows people to log in like with RDP on windows, if not then sorry for the following.

AFAIK there is no implementation of 'Terminal Services' as such as its a proprietary microsoft thing, but there are plenty of ways to log into a ubuntu server and run programs on it.

Theres VNC, which allows an existing session on the server to be logged into, and you get a window in which is displayed the desktop of the server, in a manner similar to Microsoft's Remote Desktop.

Also there is XDMCP, which allows you to access the login screen of a server and login so that it seems to you as though your actually at the server (I.e, its full screen) or there is an XDMCP client built into the 'terminal server client' program in gnome. you can enable XDMCP from the 'login screen' program in the administration menu in ubuntu, however, this is NOT secure, the transport isn't encrypted.

Also, If you run an ssh client, then you can log into it from a machine running cygwin or linux (or a couple of other X implementations on windows, eg Exceed), and then when you run, eg, firefox from the ssh session, then the gui for firefox will appear on your screen as if you were running firefox, but it'll actually be executing on the server, just displaying on the local machine. IMO this is the best, its secure because of ssh, and beter than vnc as you don't have to have a pre-existing x session on the server.

Hope some of that helped, if not post back with exactly what you need.

---

### Post by iduriduridur on 2006-09-01
Actually there is a RDP like software that tunnels securely over SSH. 

 [http://code.2x.com/linuxterminalserver](http://code.2x.com/linuxterminalserver)

 [www.nomachine.com](www.nomachine.com) 

 and freeNX

 [http://developer.berlios.de/projects/freenx/](http://developer.berlios.de/projects/freenx/)

 All use nomachine's GPL software to tunnel a desktop over SSH.

---

### Post by alecjw on 2006-09-04
So this is like the terminal server which windoze xp pro logs in to?

---

### Post by alecjw on 2006-09-05
Hello? Anyone? I'm going to try and convert my school's £500,000 ICT department to Ubuntu. Won't be easy, but as long as they know that Ubuntu has the same features of windoze but free, I'm sure that they'll show some vauge interest...

---

### Post by richardward101 on 2006-09-05
Yes essentially it is. You run the NX server on one machine and you run the NX client software as if it were the RDP client on windows. However, client machines must have the NX client installed (linux and windows), they can't connect with the normal RDP client (although the reverse can happen, i.e ubuntu machines connecting to RDP windows server).

However there is a web client available, I.E. you can visit a web page that has a java app in it that connects to the server, i.e rdp in your browser! naturally this works on any system without additional installs.

---

### Post by bluefrog on 2006-09-06
Install LTSP on top of Ubuntu and you have a terminal server.
then you can use thin clients to connect to the terminal server
Of course you can also have thick clients.

You don't want/don't know how to do that, install edubuntu and you have a terminal server out of the box.

It all depends on what you want to do, what are your specs and so on...

James

---

### Post by toelen on 2006-09-06
There is also [http://xrdp.sourceforge.net](http://xrdp.sourceforge.net), an rdp server for Linux which uses the same codebase as the rdp client installed on ubuntu.

I haven't seen packages for ubuntu, so you should compile it for yourself (or ask the developers kindly to provide them)

---

### Post by richardward101 on 2006-09-06
just followed the link, the sourceforge page actually does have a .deb package.

---

### Post by fnjordy on 2006-09-09
The Ubuntu wiki has several articles, here's an index:

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

And here's a more comprehensive all-in-one on 5.10:

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

---

### Post by pt123 on 2006-10-01
> **richardward101 said:**
> 
Also there is XDMCP, which allows you to access the login screen of a server and login so that it seems to you as though your actually at the server (I.e, its full screen) or there is an XDMCP client built into the 'terminal server client' program in gnome. you can enable XDMCP from the 'login screen' program in the administration menu in ubuntu, however, this is NOT secure, the transport isn't encrypted.

I am able to use XDMCP to connect to a remote machine (its on the LAN) when I am logged out of my local machine. But I wanted to connect using XDMCP using Ubuntu's Terminal Server Client app ( I want it in a window), but the XDMCP option is greyed out i.e. I can't select it. I can only swlect RDP or VNC. 

How do I get it to select XDMCP?

---

### Post by Peter76 on 2006-10-01
pt123, install xnest, and it will work

---

### Post by pt123 on 2006-10-01
Thanks. 

Sadly it wasn't doing what I was expecting it too. I wanted to be able to have it display output shown also on the monitor of the remote machine. I guess I will hae to fidle with VNC's resumable sessions.

---

