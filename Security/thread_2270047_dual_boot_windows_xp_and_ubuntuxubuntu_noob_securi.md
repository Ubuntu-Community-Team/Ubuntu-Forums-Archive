---
title: "dual boot windows xp and ubuntu/xubuntu noob security question"
date: 2015-03-19
forum: Security
---

### Post by Pat_Foc on 2015-03-19
Hi, so Im about to try ubuntu or xubuntu not sure rly yet on my old laptop which used windowx XP, now I would like to keep the XP (if something doesnt work or whatever) and install there ubuntu or xubuntu as dual boot, from what I have seen I could acces the files from windows through the linux system, now my question is, is it safe to dual boot? I mean couldnt somehow my linux get exploited if there's windows installed aswell maybe like someone accesing my windows and taking linux files or vice-versa? Thanks in advance

---

### Post by oldfred on 2015-03-19
Most Windows virus' will not work with Linux.
But if in Windows to run a virus that erases the entire hard drive  or even partition table that would cause issues with everything.

Best not to run XP on Internet any more. But I used to use it with firewall, virus software and behind a router to isolate it. But the maintenance of all that and all the reboots were just too much. Ubuntu could reboot in 40 seconds on old XP system, where XP was 5 minutes. After a chkdsk and issues fixed, it did improve to only 3 minutes, but every update needed a reboot.

---

### Post by Pat_Foc on 2015-03-19
Thanks for reply sir! Few more questions, if you can... say I am logged on ubuntu/xubuntu and using unprotected wifi couldnt there be somehow gained access to windows files or windows used to gain files from ubuntu/xubuntu? 

Also if I choose "Encrypt the new Ubuntu/xubuntu installation for security" during installation does this helps me prevent from such threats? I have read its kinda slowing the system, but how much "slower" is it? is it some major thing that can be "felt" or not big difference at all?

---

### Post by oldfred on 2015-03-19
Slowness will depend on system. Both hard drive speed and processor speed to unencrypt the files.

Once you are in system, you have unencrypted it, so it is not different than a standard system when you are using it.

You can access Windows NTFS partitions from Linux with its NTFS driver. But Windows has limited drivers to access Linux partitions. Standard Windows does not even see Linux partitions.
You can set Linux to hide the NTFS partitions, but if you have physical access no system is secure.

---

### Post by Pat_Foc on 2015-03-19
So only booting the system takes longer time than normally or the installation? Or is it slower even when im using the system? I just want to be sure ;) Thanks again sir!! Have a nice day! :)

---

### Post by Pat_Foc on 2015-03-19
Oh 1 very last question if I decide to do this encryption and the hardware fails or the system wont boot or something(but hard drive would be ok), is there chance to save the files which was stored of hard drive or is it lost? Thanks again! :)

---

### Post by cariboo on 2015-03-20
> **Pat_Foc said:**
> Oh 1 very last question if I decide to do this encryption and the hardware fails or the system wont boot or something(but hard drive would be ok), is there chance to save the files which was stored of hard drive or is it lost? Thanks again! :)

As long as you remember the passphrase, you can put the hard drive in another computer and run it just like in the broken system. Most of the drivers needed for most systems are included with the kernel, and are automagically loaded when the hardware is detected.

---

### Post by oldfred on 2015-03-20
But because it is encrypted, you may get issues with encryption. Best to have a really good backup procedure, which you should have anyway with any system. Hard drives fail, users make mistakes and "stuff" happens.

I have never used encryption. I think you either need it or not. And if you need it then you live with whatever speed loss you have. Very new systems may be so fast to do not notice, but an old XP system may not be that fast. You can easily install Linux one way and time it and then the other way. Not all that difficult to reinstall.

---

### Post by Pat_Foc on 2015-03-20
Thanks a lot guys!

---

### Post by bashiergui on 2015-03-20
> **Pat_Foc said:**
> say I am logged on ubuntu/xubuntu and using unprotected wifi couldnt there be somehow gained access to windows files or windows used to gain files from ubuntu/xubuntu?That would be the least of your worries assuming you mean free public wifi. Yes if you have sharing enabled and no firewall blocking shares, then anyone on the same network could browse your shared files. Other problems are that any web surfing could be intercepted and/or manipulated by someone on the same network.

If you have to use free public wifi then don't use XP, use a VPN, and force HTTPS everywhere.

---

### Post by gordintoronto on 2015-03-21
Encrypting your hard drive helps if someone steals your computer (or hard drive) and you have important personal information stored there. It has no other value.

---

