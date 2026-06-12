---
title: "Remote Desktop Access"
date: 2008-08-21
forum: Virtualisation
---

### Post by liquidfunk on 2008-08-21
I'm not sure if this is the right Forum for this question, but here goes.

 At the place I work, they use a medical program called EMIS. I am moving away to go to University soon, and my boss told me that if there are any minor jobs that need doing, I can do them by using LogMeIn. However, as far as I know that is Windows/ Mac only, and you have to pay for it.

 Is there any way of getting a similar program, so that it can log into a machine, and display it in a virtual window, so that I can work on that? 

 I've heard of VNC, but I'm unsure of how to set it up.

 Any help would be great.

---

### Post by KatBuntu on 2008-08-21
Give a try to NoMachine, [http://www.nomachine.com]("http://www.nomachine.com"):lolflag:

---

### Post by HermanAB on 2008-08-22
Set the Windows machine at work to allow Remote Desktop (You need Win XP Pro or a Server version).  Configure the company router to forward port 3389/tcp to the desktop machine.  Then run rdesktop on your Linux machine and connect to the IP address of the company router, which will forward to the desktop.

Alternatively, if you cannot change the company router settings, use a reverse VNC 'Helpdesk' system like Bozteck one click VNC:
[http://www.bozteck.com/vncscan/downloads.html](http://www.bozteck.com/vncscan/downloads.html)

With this solution the connection is made from the 'inside out' which allows it to get through a NAT firewall.

Cheers,

Herman

---

