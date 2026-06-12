---
title: "Winxp home repair install, need admin password? :("
date: 2007-12-11
forum: Windows
---

### Post by lunaz on 2007-12-11
I'm trying to repair a winxp install on friend's old hp laptop, and it asks me for the admin pw. I don't know it, and using blank pw didn't work either. How do I find it, or is there a better way to fix the install? I have a winxp home and knoppix cd available.

---

### Post by evil316 on 2007-12-11
There are all kinds of utilities to recover or change a forgotten password that are free.  NT recovery, BART, etc.  Just google for them, burn to disc and you're set.

---

### Post by got awesome? on 2007-12-13
Yep, it's fairly easy, I used this (it won't work with encrypted filesystem, probably not an issue unless you're on a corporate domain):

[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

Just go to the bootdisk download link, grab the .zip file, extract the .iso, burn it to CD, then:

Load CD
Change boot sequence in BIOS
Boot the CD
Follow the text prompts

Note that it loads default parameters, I've not had to change them so you can pretty much just press enter all the way through (a few prompts require you to hit "y" for yes). The main one to look for is where you change the password, just make it BLANK and then change it back to something else once you're in Windows again.

The final prompt is to write your changes to the registry, you need to change the "n" to a "y" (this is so you don't do it accidentally), and then just reboot, change your BIOS back to HDD boot and you're all set.

Hope that helps!

---

### Post by nikanone on 2008-08-06
Hello everybody, recently we bought a house and decided to remodel it. Building was extended above the right of way. The land owner demanded an amount to be paid for the building extension since the above of the right of way was consumed? I can’t understand the actual rule. I need your help. Is it legal to build building extension above right of way? Thanks a lot.

---

