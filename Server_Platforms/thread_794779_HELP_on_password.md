---
title: "HELP on password"
date: 2008-05-14
forum: Server Platforms
---

### Post by kinter614 on 2008-05-14
why wont my computer take my password for start uo on ubuntu server 7.10 any help would be appreciated

---

### Post by cdtech on 2008-05-15
> **kinter614 said:**
> why wont my computer take my password for start uo on ubuntu server 7.10 any help would be appreciated

Did you set up a user during install? Your not trying to use root as a user are you? It wont work...

You have to have created a valid user during install.

You also need to pay attention to upper and lower case typeset.

---

### Post by maiadestinee on 2008-05-15
Hey...

  Password is case sensitive....

please try with carefully......Password can be changed by you....

So use only rememberable password.....:popcorn:

---

### Post by hyper_ch on 2008-05-15
username is also case sensitive.

user != User != USER

---

### Post by MaindotC on 2008-05-15
kinter - if you're still having trouble you can reset the password following the instructions at [this thread]("http://ubuntuforums.org/showthread.php?t=792432&highlight=strAlan").  Here's a synopsis:

Pressing esc at the grub prompt.
Press e for edit.
Highlight the line that begins kernel <kernel number>, press e
Go to the very end of the line, add rw init=/bin/bash
Press enter, then press b to boot your system.
Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
Type in passwd <username>. Set your password.
Type in reboot.

---

### Post by kinter614 on 2008-05-15
it is still not working is it possible for anyone to do it for me i will give you the hard drive and the disk :rolleyes::confused:

---

### Post by MaindotC on 2008-05-15
Kinter if the directions I listed and the post I listed does not help you solve your problem then your operating system is not adhering to the standards set in Ubuntu and moreso the included Linux kernel as well.  You are running a rogue version of Ubuntu and I advise you back up your date and reinstall the operating system.  Good luck!

---

