---
title: "Installing muliple Ubuntu 12.04 Servers on same Machine"
date: 2012-07-14
forum: Server Platforms
---

### Post by chiefguerra on 2012-07-14
Hello everyone,

Is it possible and is it hard to install multiple Ubuntu servers on the same machine?

I'm currently running 12.04 LTS on a server running 8GB RAM, Raid-1 (2TB drives), 2 Quad core processors and want to take advantage of my hardware but wanting to know if it's possible to do.

If so, I appreciate any input on how to do this. I would assume it would have to do something with partitioning.

Thanks,
Ben

---

### Post by sandyd on 2012-07-14
> **chiefguerra said:**
> Hello everyone,

Is it possible and is it hard to install multiple Ubuntu servers on the same machine?

I'm currently running 12.04 LTS on a server running 8GB RAM, Raid-1 (2TB drives), 2 Quad core processors and want to take advantage of my hardware but wanting to know if it's possible to do.

If so, I appreciate any input on how to do this. I would assume it would have to do something with partitioning.

Thanks,
Ben
You will want to use some kind of virtualization, such as Xen or KVM.

If you have no experience with virtualization and/or are too lazy to learn about it, check out Proxmox VE

---

### Post by chiefguerra on 2012-07-14
I forgot to mention I do have Xen installed, whether if I know how to use it to do this will be another story. 

Any help is appreciated.

Ben

---

### Post by papibe on 2012-07-14
Hi chiefguerra.

As sandyd mentioned, you need visualization. Besides the suggestion already made, take a look at Virtualbox because it can also be used on a headless server,

Check this tutorial: [VBoxHeadless - Running Virtual Machines With VirtualBox 3.0 On A Headless Ubuntu 9.04 Server]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.0-on-a-headless-ubuntu-9.04-server").

Also take a look at this episode of the Linux Action Show: [Virtualbox tips for Pros and Beginners]("http://www.jupiterbroadcasting.com/12691/virtualbox-pros-and-beginners-las-s18e10/"). The first part of the broadcast is Tech and Linux news. The VirtualBox talk start around half through the end.

I hope that points you in the right direction.
Regards.

---

### Post by chiefguerra on 2012-07-15
So I installed virtualbox and appropriate extension, added a server (12.04 iso) but when I go to start it all I get is VRDE server is listening on port 3389. port is open.

How can I make sure the iso is installed and the server is running, access the server to configure it ,etc..?

I've using Virtualbox on my Mac and know how to use it in GUI mode but using it in Ubuntu server is what's getting me.

Any ideas?

Ben

---

### Post by papibe on 2012-07-16
Check the 2nd page of the tutorial I linked.

You connect to the virtual machine using 'remote desktop'.

Regards.

---

### Post by chiefguerra on 2012-07-16
How will this work if my actual physical server is at a colo data center? Is this possible over SSH? Or how can I access over the web if I haven't actually ran the install process of actually installing the server in virtualbox.

I hope I explained it at best.

Ben

---

### Post by papibe on 2012-07-16
You can certainly use remote desktop over ssh by mapping the proper ports into a ssh tunnel. Here is good guide to do that: [SSH/OpenSSH/PortForwarding]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding").

Take special attention to the section called: [Remote Port Forwarding]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Remote_Port_Forwarding"), where there's an specific example on how to use it with remote desktop.

Hope it helps.
Regards.

---

### Post by chiefguerra on 2012-07-16
I really appreciate all the help!!

Thank you.

---

### Post by chiefguerra on 2012-07-18
I tried to follow procedures below, but for some reason I cant get it to work.. I'm not how to understand the 5900 portion and also portion of  [FONT=monospace][/FONT]guest@joes-pc . What would I have to use on my end?

----------------
**Remote Port Forwarding**

 Remote port forwarding lets you connect from the *remote*  SSH server to another server.  To use remote port forwarding, you need  to know your destination server, and two port numbers.  You should  already know your destination server, and for basic uses of port  forwarding, you can usually use the port numbers in Wikipedia's [list of TCP and UDP port numbers]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers"). 
For  example, say you wanted to let a friend access your remote desktop,  using the command-line SSH client.  You would use port number 5900 (the first *VNC* port), and destination server *localhost*: 

ssh -R 5900:localhost:5900 guest@joes-pcThe -R option specifies *remote*  port forwarding.  For the duration of the SSH session, Joe would be  able to access your desktop by connecting a VNC client to port 5900 on  his computer (if you had set up a shared desktop).

---

### Post by chiefguerra on 2012-07-20
Any help out there on how to do this?

---

### Post by papibe on 2012-07-20
I would take one step at a time.

First make sure the remote-desktop connection is working, without ssh or any port mapping.

Then, I would try to test the connection over ssh.

Let us know how it goes.
Regards.

---

