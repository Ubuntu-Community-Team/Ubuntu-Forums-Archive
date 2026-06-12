---
title: "[SOLVED] Logging in uncompleted = Virus?"
date: 2008-11-20
forum: Security
---

### Post by Camilia on 2008-11-20
I logged into this forum and saw the welcome but didn't get logged in. Tried it 3x. Thus decided to reboot with the ubuntu disk. Could this have been due to a virus?

Ran rkhunter and found this:
/usr/bin/ldd                                             [ Warning ] 

 Checking /dev for suspicious file types                  [ Warning ] 
    Checking for hidden files and directories                [ Warning

---

### Post by Dr Small on 2008-11-20
What browser are you using? Sounds like it isn't storing cookies correctly.

---

### Post by Camilia on 2008-11-20
I am using firefox. I was able to log in 1 time. Then went to link in forum was logged out and unable to log in again.

---

### Post by benny bronx on 2008-11-20
Are you using NoScript.  You may have to allow both ubuntu and yahooapis in the NoScript menu, or you may be blocking iframes (under plugins).  Just a shot in the dark.

---

### Post by Camilia on 2008-11-20
I had NoScript removed it and still had a problem logging in.

---

### Post by styxcoverbnd on 2008-11-20
> **Camilia said:**
> I logged into this forum and saw the welcome but didn't get logged in. Tried it 3x. Thus decided to reboot with the ubuntu disk. Could this have been due to a virus?

Ran rkhunter and found this:
/usr/bin/ldd                                             [ Warning ] 

 Checking /dev for suspicious file types                  [ Warning ] 
    Checking for hidden files and directories                [ Warning

The above rkhunter results shouldn't affect you logging into this site, but (so you know what the results mean)have you recently ran updates, if so this might be a false positive for /user/bin/ldd ? 

Open a terminal and type: sudo gedit (text editor). In gedit open the rkhunter.log which is in /var/log and let us know what the info for your warnings on /usr/bin/ldd, /dev and hidden files are (mostly likely false positives, but it's good to know what exactly is going on on your system)

---

### Post by aysiu on 2008-11-20
Boot the live CD and try to log into the forums. If there is a rootkit installed, it can't be on the CD session.

---

### Post by Camilia on 2008-11-20
[FONT="Verdana"][SIZE="2"]I am not having any problems since reinstalled unbuntu. Just trying to undestand what happened.[/SIZE][/FONT]

rootkit installed, it can't be on the CD session. I don't think so.

The only thing I do that allow a virus to get onto my computer is copy info from page on line and paste in word processor sheet.

---

