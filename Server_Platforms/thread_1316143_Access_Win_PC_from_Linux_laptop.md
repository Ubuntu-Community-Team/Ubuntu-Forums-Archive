---
title: "Access Win PC from Linux laptop?"
date: 2009-11-05
forum: Server Platforms
---

### Post by sailthesea on 2009-11-05
Hi I hope this is right place to post this question.
 I want to remotely access my Home PC ( wired internet XP studio machine ) to use files in my user account. I want to do this from a laptop running Mint 7 on the wireless connection of the same machine
 What is the easiest way? I don't want to have admin access just get to my account 
 Any ideas thanks!

---

### Post by awclemen on 2009-11-05
Samba is your best bet:

[http://ubuntuforums.org/showthread.php?t=807747](http://ubuntuforums.org/showthread.php?t=807747)

actually this one might be best:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by cariboo on 2009-11-05
If all you want to do is access the XP computer you don't have to install anything. Just go to Places-->Network, if you have sharing set up properly on the XP system they should show up in the Window. You may have to change the workgroups to match, which is fairly easy on the XP system.

---

### Post by sailthesea on 2009-11-06
Thanks for the tips guys 
Will have to try using the home network Kinda thought it wouldn't work cross platform 
Samba could be the way to go if I am ever away from home

Cheers!

---

### Post by GCoffee on 2009-11-06
VNC (Such as TightVNC) could be a viable option here. It gives you remote viewing & control of your desktop, as if you were in front of it.

Ubuntu also has a VNC Client built in I think.

---

### Post by Tony Ricena on 2009-11-06
Well if he is trying to connect to an xp machine via a linux machine, terminal server client is the answer if you want to remote desktop.  But installing samba on linux and making sure that your windows xp machine and your linux machine is on the same workgroup will do the trick.

---

