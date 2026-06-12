---
title: "Commands/Programs Listening on Ports 5800 &amp; 5900?"
date: 2011-02-02
forum: Security
---

### Post by AW603 on 2011-02-02
I wonder if anyone can advise on the following.    Net Activity Viewer shows two commands constantly listening on Ports 5800 & 5900.    

They are:

```
(PID)   (Program) (Command)
2368    ica       ica -noshm -isdport 5800 -ivsport 5900 -role other   
2315    ica      /usr/bin/ica -rx11vs -nosel -nosetclipboard -rfbport 5900 -rx11vs -isdport 5800 -role other   
```The searches I've made seem to suggest that they made part of iTALC (?) through Edubuntu, parts of which are installed on the machine (games and so on).  As far as I can understand, it is some form of remote monitoring/teaching tool.  

Although I've always had Preferences>Remote Desktop Preferences set not to allow Remote access, I only just found out about Preferences>Start Up Applications>Remote Desktop, which I have unchecked.  Also, I don't if it makes a difference but my iptables is set to Policy Drop on both Chain Input and Chain Forward

Can anyone tell me if it is safe for these programs/commands to be listening on these ports, or do I need to be worried?  Thanks

---

### Post by HermanAB on 2011-02-02
Hmm, apparently you played with VNC at some point.  It is the favourite way to get your Ubuntu system hacked.  Kill VNC.

---

### Post by AW603 on 2011-02-03
Thanks for the advice.    I wasn't aware that I'd made any such modification to system, and after a bit of further digging I was surprised to learn that parts of Italc are installed by default in Edubuntu:

[https://wiki.edubuntu.org/iTalc](https://wiki.edubuntu.org/iTalc)  

I've removed Italc via Synaptic, and the entries are no longer seen on Net Activity Viewer and I've done a manual search for files related to ica, and they seem to have gone. From other searches it's clear that many other users are also shocked to find that their system becomes seemingly susceptible to attacks from what they assume is a trusted software. 

I have enjoyed the learning curve of using Ubuntu, but I must confess that I do wish that more of the applications/software could more conscious of the skills of the novice, especially when security is involved.

As for VNC, I've the following entries marked installed in the Synaptic Manager:

> vino                             VNC server for GNOME 
tsclient                         VNC client for the GNOME Desktop 
libgtk-vnc-1.0-0     front-end     A VNC viewer widget for GTK+ (runtime libraries) 
vinagre                        front-end for viewing of remote desktops in GNOME Is it safe to uninstall these via Synaptic without affecting the system, and will this kill VNC?

Thanks.

---

### Post by CharlesA on 2011-02-03
You can remove vino VNC server for GNOME.

The others are just clients.

---

