---
title: "[SOLVED] So long, sudo..."
date: 2008-03-17
forum: Security Discussions
---

### Post by Fate Reconciled on 2008-03-17
Alright, I know this wasn't a good idea from the start. However, I'll think twice next time before experimenting with the only user account I have set up.

I'm running Kubuntu 7.10 and was editing user my only user profile through the Kcontrol GUI. I wanted to set up an account with full root privileges in order to eliminate the constant use of 'sudo'. I basically dove in without reading any documentation beforehand and now have to pay the price of having no root or administrative privileges whatsoever. This is what I did to come to this:

-Opened up User Management and selected the account I was using.
-Changed the accounts Primary Group to 'root' and left the Secondary Group blank. 

These are the ONLY changes I made. I even left the UID at 1000 whereas now I see the UID for root is 0.

I now have:
-No sound
-No use of sudo
-No ability to login as root in console
-Probably more problems that I'm afraid to discover.

I can't even use Administrator Mode to change the mistakes I made. I've read about making changes in /etc/sudoers but the folder doesn't even exist and I can't edit the file anyway because I have no root privileges! 

Any help with this would be greatly appreciated...

---

### Post by Dr Small on 2008-03-17
Well the simplist way to solve this would probably be to boot into Recovery Mode, startx and fix things.

---

### Post by Fate Reconciled on 2008-03-17
Alright, I wasn't sure if Recovery Mode would be a simple and foolproof method of fixing this. I'll try it out and post the outcome shortly.

---

### Post by SanderVermolen on 2008-03-17
You probably unsubscribed from all groups and subscribing to root only. You can revert this by becoming member of the following groups again:

adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
and as primary group the one that has the same name as your login name

You can use the usermod command to do this. 

Of course you DO not to be root user to execute this (by using su, sudo or a regular root login). This is still possible right?

BTW, do not try to setup an account with root access, this is useless, you already have the root user! If you do not want to type sudo all the time, use "sudo bash" instead.

---

### Post by leg on 2008-03-17
You can always just write "sudo su" in the terminal if you get annoyed at having to keep typing the sudo command.

---

### Post by miggols99 on 2008-03-17
**Don't** use sudo su!! Use
```
sudo -i
```

---

### Post by jken146 on 2008-03-17
You can fix things in recovery mode.  Remove your user from the group *root* and add yourself to the group *admin*.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) might be worth reading.

---

### Post by aysiu on 2008-03-17
> **leg said:**
> You can always just write "sudo su" in the terminal if you get annoyed at having to keep typing the sudo command.

> **miggols99 said:**
> **Don't** use sudo su!! Use
```
sudo -i
``` Neither of these solutions will help in this case, as the OP cannot use *sudo* any more: [quote=Fate Reconciled]I now have:
-No use of sudo[/quote]

---

### Post by Fate Reconciled on 2008-03-17
Alright, I started in recovery mode and the problem is fixed. 
Apparently manual access to an Ubuntu system is the worst security breach out there, haha...

Thanks for all the future suggestions about the sudo command. Having a user account with root privileges is a bad idea in the first place.

---

### Post by p_quarles on 2008-03-17
> **Fate Reconciled said:**
> Apparently manual access to an Ubuntu system is the worst security breach out there, haha...
Very much so. This is, in fact, true of any computer. Even cheap home routers.

---

### Post by Dr Small on 2008-03-18
> **p_quarles said:**
> Very much so. This is, in fact, true of any computer. Even cheap home routers.
That's why I added a password on my GRUB recovery entry.

---

### Post by p_quarles on 2008-03-18
It's very easy to either bypass or overwrite the MBR, so protecting GRUB entries isn't going to hinder a serious attacker (who has physical access). Slightly more secure would be to password protect the BIOS itself, but there are ways of getting around that as well. 

The best defense against physical attacks is encrypting any sensitive data you might have. Once the data is securely encrypted, it needs to be manually decrypted, which is an enormous task. Pretty much every other security measure depends on the integrity of the hardware, and once that hardware is out of your control, it has no integrity.

---

### Post by Dr Small on 2008-03-18
No of course not. If he is from the NSA, there is literally no way to stop him. But all the rest is trival stuff to keep your friends and family from wrecking the system :)

---

