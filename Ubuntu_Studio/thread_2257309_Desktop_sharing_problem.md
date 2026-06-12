---
title: "Desktop sharing problem"
date: 2014-12-18
forum: Ubuntu Studio
---

### Post by simon d w on 2014-12-18
When I search for desktop sharing it is always standard ubuntu help. I can't find desktop sharing preferences to enable desktop sharing. I want to be able to fix another computer not on my network. I have the IP address. I've tried typing it in to remote desk top viewer and it comes back connection closed after a few mins. I'm sure i need to enable sharing of desktops(allow other used to access your desktop) but cant find the graphic interface and don't know the commands. 

Help!

---

### Post by QIII on 2014-12-18
Hello!

Is desktop sharing enabled on the host ("target") machine?  What remote desktop protocol is that? What security model/protocol is in place on the host?  What protocol are you using on your local machine?

---

### Post by simon d w on 2014-12-18
This is just 2 personal home computers, i just installed studio on both nothing added no security except what ever comes as standard. Protocol ssh. Im asking how do you enable sharing on studio? There is no options in the setting menu. One is at a friends house and she knows nothing about ubuntu and is always messing setting up. I need to access here computer remotely , i have the passwords and user name.

---

### Post by steeldriver on 2014-12-18
Since afaik Ubuntu Studio is based on the xfce4 desktop, it wouldn't normally come with the (gnome-based) vino-server that provides "Desktop Sharing" in regular Ubuntu. Distros based on xfce4 typically use x11vnc for desktop sharing, however you really should set it up with SSH tunnelling if you go down that route.

---

### Post by simon d w on 2014-12-19
Where can I learn about that stuff i am not an expert. I was thinking it was something to do with that! I know I could use team viewer but I like to know how to use the ubuntu built in features. im going to try Remmina Remote Desktop Client

---

### Post by DanielkUSAF on 2014-12-19
Hey there simon! I have been setting up a server in my home using SSH to remote in to it over internet. I have been working the same desire to use a vnc/rdp setup for some GUI interfacing. I googled a bunch of associated terms, and perused the forums here, lots of information and walkthroughs. As steeldriver said, if you do this and are going over an internet connection to opt in to your friend's desktop at her house, use tunneling so as to prevent eavesdropping on your connection. I also have mine set up to use certificates and disabled password login via SSH so as to help prevent brute-force and port-scanning from computers "in the wild". Good luck!

[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)
[http://ubuntuforums.org/showthread.php?t=2041469](http://ubuntuforums.org/showthread.php?t=2041469)

---

### Post by simon d w on 2014-12-23
thank you!

---

