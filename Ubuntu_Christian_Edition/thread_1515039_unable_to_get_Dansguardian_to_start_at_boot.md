---
title: "unable to get Dansguardian to start at boot"
date: 2010-06-21
forum: Ubuntu Christian Edition
---

### Post by rossdav on 2010-06-21
OK, I've been through the forums, and have tried several things, and now come for help.

I had everything working fine with Ubuntu / Karmic (Dansguardian, et al from Ubuntu CE).  I upgraded my OS to Lucid early last week, and lost my CE additions.  After some research, I have reworked my repositories and all, and successfully reinstalled the Dansguardian components (DG, Tinyproxy, Ubuntu_ce_firewall, DG-GUI).  

Here's my procedure that works each and every time:

When I boot, DG-GUI indicates all OFF.
Reset DG/TinyProxy
Stop DG
Start DG
Everything works fine  - CEfw, DG, TinyProxy.  I can logout/login, and no problems - the DG component is in place, I can surg and am protected

However, if I reboot, I lose everything - I am basically having to restart the processes manually each and every boot of the computer.  I think it might be a timing conflict with network manager / wlan initialization / TP/DG/UbuntuFW, but I cannot seem to nail it down.

I have checked my /etc/init.d directories, have the three scripts for DG / TP / ubuntu_ce_fw.  I have links in rc5.d for each - I've even tried moving them to the bottom (S91tinyproxy / S92ubuntu_ce_firewall / S93dansguardian).  I can start the manually from the command line or using the GUI.  I cannot for the life of me figure why the scripts are not kicking things off at boot - any insight is welcome.

i am a long-time RH/Fedora user, fairly new to Ubuntu for this home system.

Thanks all

---

### Post by rossdav on 2010-06-22
As an update and clarification, my current situation is this:

If I boot the computer, I can launch the three services in order, using the /etc/init.d scripts, and browsing/protection work fine.  (tinyproxy / ubuntu_ce_firewall / dansguardian)  No other changes or reset are necessary.

So, I know the startup scripts should be working, but they simply do not at boot.  I am considering just adding a script to all my user account logins to launch those, but that requires opening up some of the security.  Otherwise, I have to be around to launch those for them, which is not going to happen... :)  This is a home computer, and the users are my wife and three teenage boys.

thanks again for any insight.

---

### Post by stlsaint on 2010-06-22
I am not at my home system so i cannot fully test out this issue but i belive i had the same issue but it should be an easy fix. It will come down to editing an init config (i think) but DK can explain better. Welcome to Ubuntu!! :guitar:

---

### Post by david_kt on 2010-06-22
> **rossdav said:**
> As an update and clarification, my current situation is this:

If I boot the computer, I can launch the three services in order, using the /etc/init.d scripts, and browsing/protection work fine.  (tinyproxy / ubuntu_ce_firewall / dansguardian)  No other changes or reset are necessary.

So, I know the startup scripts should be working, but they simply do not at boot.  I am considering just adding a script to all my user account logins to launch those, but that requires opening up some of the security.  Otherwise, I have to be around to launch those for them, which is not going to happen... :)  This is a home computer, and the users are my wife and three teenage boys.

thanks again for any insight.

I do not know what happen to the init script, it might be there is some leftoever in the rc directory that preventing those three to load. You could search the ones started with k and remove it. Alternatively, you could do below as a quick hack:

```
gksudo gedit /etc/rc.local 
```

Copy and paste below line BEFORE/ABOVE exit 0

```
/etc/init.d/ubuntu_ce_firewall restart 
/etc/init.d/tinyproxy start
/etc/init.d/dansguardian start 
```

Reboot you computer and see whether it works.

DK

---

### Post by rossdav on 2010-06-23
Still no joy - I did find that Ubuntu and runlevels are quite different from other distributions - I was working in the rc5.d directory, but it appears that Ubuntu uses 2 as it's default, and the inittab file is now optional.

Made the same changes in order in the rc2.d directory, and no luck. Adding them to rc.local did not fix the problem either.

Again, I can run the scripts manually after boot, and everything is fine.  They just are not loading at boot!  Oddest thing - I've worked on *NIX systems off & on the past 20 years, but get stumped with an OS trying to be user-friendly.  I have a feeling that Ubuntu is doing something in the background along the way to 'help' me, but is instead getting in the way (kinda like MS Word auto-capitalization many times). 

I am leaning toward network manager as the culprit - I have a feeling that it is doing something before/after these scripts try to run at boot and is messing things up.  Being a home system, I don't plan to labor too hard over this, since I can go ahead and setup permissions and a shortcut on the desktop for each family member to 'fix' DG each time they log in.  Kinda simple - they can't get on the web without this running, so they are filtered either way.. :)  

I am game to try other things as well if there are other ideas.

---

