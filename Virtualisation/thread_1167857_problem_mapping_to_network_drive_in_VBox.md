---
title: "problem mapping to network drive in VBox"
date: 2009-05-23
forum: Virtualisation
---

### Post by kenny99 on 2009-05-23
Hi, i've read loads of tutorials and forum posts on this topic but still can't find out where i'm going wrong. I'm running Windows XP in VirtualBox 2.1.4 on Ubuntu Intrepid 8.10. I have installed Guest Additions and created my shared folder (with full access allowed) via the VBox GUI, I then click on Map Network Drives in XP, which shows my shared folder under Virtual Box Shared Folders -> \\VBOXSVR\home. So everything seems to be fine at this point, however, when I select the home folder and click on OK, I get the "Attempting to connect to \\VBOXSVR\home..." message followed by "The network path \\VBOXSVR\home could not be found". Similarly, if i try to connect via command line, using "net use z:\\vboxsvr\home" - I get "The network name cannot be found".

Grateful if anyone can help me sort this out as i can't see what the problem is.

---

### Post by roman_platonov on 2009-05-24
to resolve you trouble you need to create shared folder in you home, not in common /home(restricted to read by default for vbox) or make full access to youself

---

