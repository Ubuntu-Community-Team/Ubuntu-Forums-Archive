---
title: "Error trying to join a ubunut machin to a windows server 2003 ads."
date: 2007-07-11
forum: Server Platforms
---

### Post by foxhound_oki on 2007-07-11
Hi, I am a school administrator and I have installed ubuntu for the client computer and have windows server 2003 active directory setup.  I followed how to join ubunut/samba to a windows 2003 acitve directory domain wiki and got stuck on the last part, setp 5.  I got it to join to the domain very well and I can see the computer in the active directory.  but when it came down to testing kebros it errors out with the following command line "kinit [email]administrator@kbhs.com[/email]"  It says kinit(v5): KDC reply did not match expectations while getting initial credentials

Can anyone tell me what this means and how can I get this to work.  I need help bad and quickly.  This is a project that had to be done before school starts up again and have only a month and half to go.  I still need to image over 600 machines still.

---

### Post by rickyjones on 2007-07-11
I'm not sure on how current the wiki article is that you followed but I followed the guide in the how-to forum step by step and it worked perfectly for me. My environment is all in Vmware - the domain controller is running Windows Server 2003 SP2 w/ all updates and the client is Ubuntu 7.04 (latest desktop ISO download).

Link: [http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

Hope it helps!

-Richard

---

