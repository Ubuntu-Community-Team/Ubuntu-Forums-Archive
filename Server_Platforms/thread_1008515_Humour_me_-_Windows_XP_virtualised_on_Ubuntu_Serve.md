---
title: "Humour me - Windows XP virtualised on Ubuntu Server 8.10?"
date: 2008-12-11
forum: Server Platforms
---

### Post by Nunnsby on 2008-12-11
So, I have an intriguing question and something that I would like to try figure out . . . 

Can I install Windows XP on Ubuntu Server 8.10?

Immediately I see a glaring issue here:

* How to see the graphical interface of the VM if running on server, as there is are no graphics, only a terminal. So, I am not too sure if the terminal can actually run the VM without some sort of graphics engine (X - I imagine) being installed.

Secondly I am connecting to the server remotely over SSH. So, if it is possible to run the VM via some sort of X-install, can I install VNC on the server, which should thoeretically put me on the console and then run the VM through that?

Just a random question - don't ask :) - if anyone can help me there?

Otherwise, I do have a need to install VNC-Server on the box, to replicate being on the console. Can this be done on server, and what is required?

Any help - or tips - as always, much appreciated.

Regards

---

### Post by |{urse on 2008-12-11
You need an X server running to see the virtual machine.

---

### Post by CrucifiedEgo on 2008-12-11
You could use VMWare Server, and use the remote console to connect to it from another PC and set it up, then use Remote Desktop to access the XP machine from then on.

---

### Post by pdtpatrick on 2008-12-11
Lets just say it defeats the purpose of running a server. It's like buying a mercedes and then strip the engine and put a daewoo engine in it :)  ....

---

### Post by koenn on 2008-12-12
It can be done, and in fact, it is the way it should be done.

Install vmware server or a similar hypervisor on your server, 
connect to it from a VMware console or the vmware server web interface, or simply export the GUI to a desktop pc (ssh -x user@server vmware )
 as you now have the vmware GUI on your desktop, there is no problem using or installing systems that require a GUI. The vmware software and the virtual machines remain on your server, only the display is transferred to your desktop.

---

### Post by lykwydchykyn on 2008-12-12
The "non-open source" version of VirtualBox can do this as well, it starts the machines with remote desktop enabled.  You can connect to them via rdp.

VirtualBox has a very robust command line interface, so it's good for this situation.  I've tried vmware too, it works a bit slower IMO but has a web interface instead.

---

### Post by koenn on 2008-12-12
> **lykwydchykyn said:**
> The "non-open source" version of VirtualBox can do this as well, it starts the machines with remote desktop enabled.  You can connect to them via rdp.

VirtualBox has a very robust command line interface, so it's good for this situation.  I've tried vmware too, it works a bit slower IMO but has a web interface instead.

What i meant is you export the vmware console's gui, giving you access to all installed vm's at once, as opposed to rdp-ing to each individual guest system's desktop separately.

---

### Post by HermanAB on 2008-12-12
This is commonly done to run accounting programs on a Windows VM.  

Enable Remote Desktop Protocol on XP and use rdesktop to connect to it over port 3389/tcp.

Cheers,

Herman

---

### Post by lykwydchykyn on 2008-12-12
> **koenn said:**
> What i meant is you export the vmware console's gui, giving you access to all installed vm's at once, as opposed to rdp-ing to each individual guest system's desktop separately.

Sure you could.  I wasn't really responding to your post.  But your idea is good too.

Lots of ways to approach this.

---

### Post by Nunnsby on 2008-12-12
Cheers all, good to know I might be able to do what I am trying to.

Thanks for all your help and advice. I'm using Vbox already, on an XP host, but will give it try remotely then on the Server. Just wasn't exactly sure of the process. 

Cheers for your time.

---

