---
title: "Concerns over Samba."
date: 2010-09-26
forum: Security
---

### Post by Stormsy on 2010-09-26
Hi there,

I have Ubuntu 10.04 installed on my laptop which is wirelessly connected to the router.  I have a PC which is Windows XP that is connected wired to the router.

Now - I understand that Ubuntu is secure out of the box and so there is no need to worry about configurations.  However, a past couple of updates in Ubuntu and I am seeing updates for Samba.

I understand that Samba is used for file transfer between Windows and Linux. 

Is Samba **turned off by defult** when Ubuntu is installed - despite having a WinXP computer connected to the router? 

Is there any way to make sure that Samba is **turned off** on my Ubuntu laptop?

I **don't** want to transfer any files between my laptop and WinXP.  If Samba is enabled, then a Firewall is needed to be configured (I assume), and to me that is sort of pointless with Ubuntu. 

For arguments sake, if Samba *was* enabled on my Ubuntu laptop - what would happen to my security?

Thanks for you help,
Stormsy.

PS: I love Ubuntu! It's fantastic, no firewalls, no antivirus, quick and a solid OS. I've recommended it to a lot of my friends and they love it too! ^_^

---

### Post by HermanAB on 2010-09-26
Howdy,

In Linux, you can always easily see what is running:
$ ps -e|grep smbd

and you can easily test for listeners:
$ telnet localhost 445

---

### Post by Fafler on 2010-09-26
Samba is split up in two parts, the server and the client, and the client is installed as part of the default Ubuntu configuration. The server is not. All samba related updates is related to the client, samba-common, samba-common-bin, smbclient and possible others.

Download a portscanner on you XP machine and portscan the Ubuntu machine. Then you'll know for sure ;-) I think theres a Windows version of nmap available.

Having samba the samba server enable wouldn't automatically introduce security issues, you'd still have to specify what to share in the configuration file. The default is nothing.

I you feel like blocking some ports after portscanning, look at this howto: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

