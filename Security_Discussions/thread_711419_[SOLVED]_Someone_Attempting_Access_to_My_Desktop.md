---
title: "[SOLVED] Someone Attempting Access to My Desktop"
date: 2008-02-29
forum: Security Discussions
---

### Post by ububaba on 2008-02-29
For last few days I get a pop message that an IP is asking for
permission to access my [COLOR="Blue"]Desktop[/COLOR]. I click on [COLOR="Blue"]Refuse[/COLOR] obviously.
Has someone else been through this? I have never experienced 
this before. Would like to know, whether something more sinister 
has happened to the computer?

How can one get rid of it? Thanks.

---

### Post by Het Irv on 2008-02-29
You might want to change your IP address, I know how to do this in windows (ipconfig /release /renew).  How is this done in Ubuntu?

---

### Post by ububaba on 2008-02-29
> **Het Irv said:**
> You might want to change your IP address, I know how to do this in windows (ipconfig /release /renew).  How is this done in Ubuntu?
Do you mean simply manipulate it so that it reads as a different one
or ask ISP to provide a new one? Which I believe would be more
complicated and may even cost money,  don't know.

---

### Post by Het Irv on 2008-02-29
sorry I am thinking in terms of a large scale network...ignore first post.
Firestarter is a firewall, you can try blocking the offending ip address in it.   Firestarter is available in the repos.

---

### Post by harold4 on 2008-02-29
Are you behind a router, or have a firewall active?

Do you this feature for allowing people to access your desktop?

Chances are someone was scanning ip addresses and found that you're listening for remote connections.

---

### Post by ububaba on 2008-02-29
> **harold4 said:**
> Are you behind a router, or have a firewall active?

Do you this feature for allowing people to access your desktop?

Chances are someone was scanning ip addresses and found that you're listening for remote connections.

No, am not behind a router. I haven't manipulated the setting for 
ages. I have never knowingly allowed anyone to access my Desktop.
However, I use KTorrent for **p2p** downloading.

---

### Post by harold4 on 2008-02-29
You can always disable the feature since you don't use it.  

Your router has a built-in firewall, which is why you forward ports for things like ktorrent.


I'd suggest looking into using a software firewall to go along with being behind a router firewall.

---

### Post by ububaba on 2008-02-29
> **Het Irv said:**
> sorry I am thinking in terms of a large scale network...ignore first post.
Firestarter is a firewall, you can try blocking the offending ip address in it.   Firestarter is available in the repos.
I must restart  Firestarter and block these IP addresses. Thanks.

---

### Post by ububaba on 2008-02-29
> **harold4 said:**
> You can always disable the feature since you don't use it.  

Your router has a built-in firewall, which is why you forward ports for things like ktorrent.


I'd suggest looking into using a software firewall to go along with being behind a router firewall.

I have started Firestarter and hoping that it would take care 
of the problem. Thanks for all the help.

---

### Post by ung/xunil on 2008-02-29
This popups are happening, first of all, because you have enabled "Remote desktop" sometime in the past. This enables the VNC server.

If you don't use VNC for remote administration, disable it again (it is disabled when you install Ubuntu). To disable it, go to the menu System > Preferences > Remote Desktop and unmark the first checkbox.

---

### Post by ububaba on 2008-02-29
> **ung/xunil said:**
> This popups are happening, first of all, because you have enabled "Remote desktop" sometime in the past. This enables the VNC server.

If you don't use VNC for remote administration, disable it again (it is disabled when you install Ubuntu). To disable it, go to the menu System > Preferences > Remote Desktop and unmark the first checkbox.

Thanks ung/Xunil. You were right. I was trying to connect a TV screen a few days back, in that process I enabled "Remote desktop". How foolish of me. Thanks a mill.

---

### Post by harold4 on 2008-02-29
> **harold4 said:**
> You can always disable the feature since you don't use it.  

 

;)

---

### Post by ububaba on 2008-02-29
As a token of thanks, please enjoy these 9 examples of Engrish.

---

### Post by vsiege on 2008-03-01
Regarding remote desktop:
If you require the person trying to access this feature use a password, is this secure enough? I have it on as something I might have to use one day, with a password.

Besides the router logs, where are the logs for attempts from the outside world trying to access your server (and which ports)?

---

### Post by ububaba on 2008-03-01
I ended up in this situation by carelessness. Have never been interested in
allowing anyone else to access my **Desktop**, thus have never tried to look
into the matter ever. These were **popup** requests to allow others, which I 
refused. I do not have a router. I solved the problem by following the advice 
of ung/xunil above.
Sorry, can't be of much help.

---

### Post by vsiege on 2008-03-01
No biggie.... maybe someone else will know... i was just being curious.

---

### Post by Het Irv on 2008-03-03
Passwords can be hacked, but it you use a complex password and change it about every three months, you should be okay.

Not sure about the logs.

---

### Post by vsiege on 2008-03-06
Well, hopefully there is a way to see where vulnerabilities are.

---

### Post by BlueKoala on 2008-04-02
I've been having similar problems.

I used to have it set for password only and every once in a while, vino server would go haywire and my network usage in sys monitor looked like the rockies. So I decided to switch from password to prompt to allow. Now I see all the addresses of people trying to VNC into my machine. It's quite annoying really. Although I wonder if anyone was ever successful in cracking my password and entering my machine in the past?? Oh well. I guess I'll have to start taking a deeper look into this whole "security" thing. It hinders my ability to frag online when someone tries to hack my box.

---

### Post by ububaba on 2008-04-02
mmm

---

### Post by stefangr1 on 2008-04-02
What you could do if you are connected trough a router is stop forwarding the port u use for vnc, and in stead use ssh and port forwarding. An additional advantage of that is having your network traffic encrypted

It's not very difficult to set up, and I believe ssh is very secure as long as you use strong passwords.

---

