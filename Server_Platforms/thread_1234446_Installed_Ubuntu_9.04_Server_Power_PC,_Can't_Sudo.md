---
title: "Installed Ubuntu 9.04 Server Power PC, Can't Sudo"
date: 2009-08-07
forum: Server Platforms
---

### Post by silvervein on 2009-08-07
Recently I installed *Ubuntu 9.04 Server Power PC* on a mac mini. I loaded file server and print server modules during the installation. I created my user name silvervein and the installation completed. 

I rebooted my mini and logged in as silvervein. I tried to sudo to download a desktop environment (for those that don't know the Power PC version does not come with a desktop environment). When I try to sudo I get the following error:

silvervein is not in the sudoers file. This incident will be reported.

I know for a fact the password is being entered in correctly. I've seen other forms that tell you to boot into grub and then edit the sudoers file. However this machine is not duel boot so I didn't load grub. 

I have also re-installed incase it was a bad install. Still same problem. 

Thanks for your time and assistnace.

---

### Post by bmathis on 2009-08-07
I dont know why it didnt add your user to the sudoers group, but you can try this. Restart the computer and boot into recovery mode. This will drop you into the root shell where you can add your username to the admin group with the following command:

> adduser silvervein admin

reboot and see if it works.

---

### Post by silvervein on 2009-08-08
Ok,

How do I boot into recovery mode? I tried to follow this [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode). However it assumes I have grub on my mini. 

When I boot this is what I see.

First Stage of Ubuntu bootstrap

Press: 
i for GNU/Linux,
                    c for CDROM

boot:

(after about 2 seconds it automatically moves to the next screen)

Welcome to yaboot version 1.13.13

Enter "help" to get some basic usage information

boot:

Entering "help" tells you about setting up what device or file to boot from in a basic way, but also tells you to hit <TAB>. This shows 2 options to boot into

Linux 
                                Old

I'm thinking I have a few more issues to work out in this equation other than the sudo problem but. One issue at a time. (one reason I say this is because on boot after the 2 before mentioned screens the next line in the boot up sequence says:

[    1.354491] radeonfb 0000:00:10.0: Invalid ROM contents]

But as I said before one issue at a time. 

Any new suggestions?

---

### Post by silvervein on 2009-08-13
Well everything I've found says to boot into some recovery mode that I don't see. I see the options on my PC (which is dual boot Kubuntu/XP) but not for the server.
 
With that, I've reloaded Debian. Thanks Bmathis for trying :)
 
closing this thread.

---

### Post by Iowan on 2009-08-15
Oops, a bit late to suggest [this]("http://www.psychocats.net/ubuntu/fixsudo") one...

---

