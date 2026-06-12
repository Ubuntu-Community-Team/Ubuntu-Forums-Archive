---
title: "Someone is accessing my machine"
date: 2016-07-26
forum: Security
---

### Post by Len_Lyle on 2016-07-26
I have noticed that every morning when I get up, I have multiple browser (chrome) windows open, half of them with failed logins to my accounts (godaddy, amazon, paypal, etc).  I had briefly enabled remote desktop, but had since disabled it.  I have blocked root ssh to my box, as am seeing thousands of failed logins (dictionary attack, I am guessing).  I have since just removed remmina completely 

```
sudo apt-get autoremove --purge remote-login-service vino remmina remmina-common
```

Does anyone have any suggestions to what else I can do to lock my box down, as I am concerned that the attacker could have installed malware such as a keylogger, as I have changed my password several times.  I would like to avoid having to wipe and reinstall if at all possible, but that is my next option.  Any suggestions greatly appreciated.

---

### Post by QIII on 2016-07-26
You may have "disabled remote access" -- except for whatever back doors an intruder has opened.  Take it off the web yesterday.

It is my humble opinion that the only recourse when your machine has been compromised (assuming your description is accurate, it surely has) is euthanasia, followed by putting the dead carcass on a pyre. Nuke it hard and start over.  That is the only option I would consider. You simply cannot trust that you can find every evil thing in every corner and remove it.  

I'm sure you have been keeping regular backups of your important data, have you not?

Do you have a roommate, by chance?

---

### Post by DuckHook on 2016-07-26
> **Len_Lyle said:**
> I would like to avoid having to wipe and reinstall if at all possible…-1

> **QIII said:**
> …the only recourse when your machine has been compromised (assuming your description is accurate, it surely has) is euthanasia, followed by putting the dead carcass on a pyre. Nuke it hard and start over.  That is the only option I would consider.+1> …you have been keeping regular backups of your important data, have you not?If not, still take your computer off line. Install a new system on another disk, even an external USB stick if you have to. Then salvage whatever data you need from your old install ***making sure not to boot into it***. Also, make sure that it is pure data only&#8213;photos, music, text, etc. No apps, scripts, system files or config files permitted. Zilch. Nada. Resist that urge to salvage the games directory, for example. Then read the stickies at the top of this Security sub-forum. After that, read this: [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)> Do you have a roommate, by chance?:-k

I cannot stress this enough: listen to QIII. There is no longer any way you can trust your install. You have been owned and the only reliable way to get back in control is to nuke and start over. Once you have a new and reliably hardened install, change your passwords to everything. Inform your bank and other important institutions. Assume that everything you connect to has been compromised. This is an occasion for tinfoil hats and aliens-are-everywhere-level paranoia.

---

### Post by gordintoronto on 2016-07-27
Remmina is a remote desktop client, not a remote desktop host. It helps you access other computers, it does not let other computers access your computer.

If you are connected to the Internet through a router, you shouldn't be seeing these things. At the same time as you nuke-and-pave, get a router and insert it between your modem and your computer. And don't set up any port forwarding on the router!

---

### Post by Habitual on 2016-07-27
Rule #1 in Security.
There is no security without physical security. <--- Roommates is a good Q.
Have a router?
Password protect the BIOS and the bootup processes.
If they can touch it, they can own it. Google "Evil Maid" sometime and casually 
think about how often you leave your computer unattended, or even unlocked?

[Disable ssh Password Authentication]("https://help.ubuntu.com/community/StricterDefaults#Disable_Password_Authentication") and [Disable root Login via ssh]("https://help.ubuntu.com/community/StricterDefaults#SSH_Root_Login").

Does your desktop need the sshd server if **you** aren't connecting to it?

The fail2ban package in a repo "near you" inhibits these brute force/account guessing nonsense **out of the box**.
I highly recommend it.

```
sudo apt-get install fail2ban
```

Some good references on fail2ban:
[How Fail2Ban Works to Protect Services on a Linux Server]("https://www.digitalocean.com/community/tutorials/how-fail2ban-works-to-protect-services-on-a-linux-server")
 [How To Protect an Apache Server with Fail2Ban on Ubuntu 14.04 - DigitalOcean]("https://www.digitalocean.com/community/tutorials/how-to-protect-an-apache-server-with-fail2ban-on-ubuntu-14-04") 
 [How To Protect SSH with Fail2Ban on Ubuntu 14.04 - DigitalOcean]("https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-14-04")


[LIST=1]
[*]Disable sshd on your localhost if you don't connect from "Out there" to where ever your computer is. 
[*]Password Protect the BIOS and control the start up "boot order". 
[*]Disable or inhibit booting of removable media in the BIOS. 
[*]Consider fail2ban. 
[*]Consider ssh keys and disabling root via-ssh and password logins via-ssh 
[*]Combine that with a router that is configured not to allow remote administration. 
[*]Change sshd port to non-standard (anything "but 22"...) 
[/LIST]

Be Safe out there.

---

