---
title: "Firewall killed my Remote Desktop!"
date: 2011-08-01
forum: Security
---

### Post by kyral210 on 2011-08-01
I have been using Remote desktop on Windows 7 to view and control my Ubuntu machine in the office quite happily over the office network. No problems there. I wanted to access it from my home connection so I read that I could do this by opening a port on the ubuntu machine's firewall. So I installed a firewall. Didnt see any way to open a port easily so I uninstalled it and installed another one. Same issue so I uninstalled that and then left it. I then tried to Remote Desktop the Ubuntu machine from my Windows 7 laptop and ERROR I can no longer connect. 
 
Why is this and how can I fix it?
 
Chris

---

### Post by spiky001 on 2011-08-01
Hi you would also have to allow port forwarding on the router, if there is a router between. The router can be blocking external connections as well, Gufw is a firewall which is easy to configure.

---

### Post by doas777 on 2011-08-01
> **kyral210 said:**
> I have been using Remote desktop on Windows 7 to view and control my Ubuntu machine in the office quite happily over the office network. No problems there. I wanted to access it from my home connection so I read that I could do this by opening a port on the ubuntu machine's firewall. So I installed a firewall. Didnt see any way to open a port easily so I uninstalled it and installed another one. Same issue so I uninstalled that and then left it. I then tried to Remote Desktop the Ubuntu machine from my Windows 7 laptop and ERROR I can no longer connect. 
 
Why is this and how can I fix it?
 
Chris

just to confirm, it is the Ubuntu remote desktop (Vino Vnc server) that you wish to access from home?

This is a very very very unsafe configuration and I would guess that you would be hacked within hours of opening the router ports. VNC is not safe to expose to the web.

Instead consider using SSH + VNC or even better, using FreeNX.

---

### Post by uRock on 2011-08-01
Moved to "*Security Discussions*"

---

### Post by kyral210 on 2011-08-01
So how would I set up my Ubuntu PC to allow me to connect to it and control is via SSH? 
 
Once I install a firewall how do I configure it to let me connect to the machine from Windows 7 over the LAN and then over the internet?

---

### Post by doas777 on 2011-08-01
ok, the general idea is that VNC will only be accessible from the lan, whereas ssh will be accessible from the WAN. once you have connected over the internet to ssh, then you will be virtually "on the lan", so you can then access VNC.

to make it all work, all you really need to do is configure your router firewall to forward your ssh port. to strengthen SSH, look into changing it to a non-default port, using Keys instead of passwords, and fail2ban/denyhosts to prevent bruteforce attacks. 
you can find instructions on port forwarding for your make and model of router here:
[http://portforward.com/](http://portforward.com/)

Here are some instructions for using vnc over ssh:
[https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH](https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH)
it covers connection from both linux and windows clients (using PuTTY).

---

### Post by kyral210 on 2011-08-02
Ok, in desperation I ran 'updates' and then rebooted the PC. The LAN connection now works. I will get onto IT in the office to see if they will let me tinker with their router.
 
Thank you so much for your help!

---

