---
title: "Ubuntu Vs Windows SBS 2003"
date: 2009-07-20
forum: Server Platforms
---

### Post by naiku on 2009-07-20
I am currently setting up a small network, the server I have came loaded with Windows SBS 2003, and it is working fine for what I want it to do. 

However, I am debating switching over to using Ubuntu server (and possibly using Ubuntu on the client machines as well). But, I have a few questions about what the Ubuntu server software can do. These are the things that I need:

1: Fax handling, in SBS2003 I can connect the server to my fax line, and have it either print, email, save the faxes, can Ubuntu do this?
2: Remote Desktop (I believe it has a Terminal Services client, but just wondering if it had Remote Desktop).
3: SBS2003 has Outlook Web Access, does Ubuntu have something similar?

In a nutshell, is there anything that I can do with SBS2003, that I would not be able to do with Ubuntu? 

Thanks.

---

### Post by Cheesemill on 2009-07-20
If you want to take advantage of group policy then there is no substitute for Windows Server.

---

### Post by HermanAB on 2009-07-20
Windows SBS 2003 is a good system, provided that you do not ever change anything.  If you do have to change a record in active directory for whatever reason, create a new record and then delete the old one.  

If you edit or move a record, the wizards will change some things and some things not.  The result is that you will end up chasing the most weird and wonderful bugs.

If you have already futzed around with it and changed schtuff - do yourself a favour and re-install the machine from scratch, then follow the above never change anything rule.  Also, the best way to run Win2003 is on VMware, so that you can easily back up the whole thing to a DVD and when it screws up, roll back in a few minutes to the last working version, because repairing a screwed up version is impossible.

If you really want to replace it, then you have to go to the Samba web site and start reading.

---

### Post by wineman on 2009-07-20
> **naiku said:**
> 
1: Fax handling, in SBS2003 I can connect the server to my fax line, and have it either print, email, save the faxes, can Ubuntu do this?
2: Remote Desktop (I believe it has a Terminal Services client, but just wondering if it had Remote Desktop).
3: SBS2003 has Outlook Web Access, does Ubuntu have something similar?


The only you can't do with ubuntu is use rubbish :)

ok im not too sure about the fax services (although ubuntu has plenty, i think cups can do it), but remote desktop can be accessed through VNC (which, in my opinion, is better) and Vinagre (its VERY similar to RDC, except that it supports ANY remote client medium :D Bonus with the boss!)
In term of SBS03's OWA... i don't think squirrelmail compares, but then thats not really the only solution. Squirrelmail is one of the best webmail apps on ubuntu, but it needs a SMTP and POP server (i presume you're running those separately, probably exchange servers?) if they aren't separate then you'll need to setup a postfix or sendmail server to handle the emails (they're the easiest to configure, although not the only solutions).

basically, anything you can do in SBS2003 you can do in ubuntu, it just might take a little longer to setup.

Good luck and i hope this helps

PS - if you're running an Active domain login system, and you REALLY want to swap, try SAMBA - its the windows networking component of Ubuntu, but setting up Primary Domain Controllers / Backup controllers is _very_ advanced, so you might want to stick with a windows PDC and have the ubuntu box as a backup.

hope this helps

---

### Post by naiku on 2009-07-20
Thanks for the replies, I have experienced the problems with SBS2003 when changing one thing and it screwing up several other things!! When I first set it up, I changed the name of the server, easy enough to do, little did I know that it then screwed up pretty much everything else.

I think what I might do for now, is set up a different machine and install Ubuntu on there and use it to practice. When I feel comfortable using it, and that it can do all I need, then I may switch.

---

