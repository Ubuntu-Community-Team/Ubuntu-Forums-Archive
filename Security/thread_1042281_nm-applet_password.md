---
title: "nm-applet password"
date: 2009-01-17
forum: Security
---

### Post by daveandsheripetersen on 2009-01-17
I'm new to ubuntu. I have an ethernet connection that works fine, but when I try to use my wireless connection, I get an error of "nm-applet needs default keyring (/usr/bin/nm-applet" and asks for a password. I put in my system password and it won't take it.  I made sure my file and the root file are the same. I'm running 8.04.  This card worked in windows, so its not the card/router.

---

### Post by MaindotC on 2009-01-17
You need to enter the password for the current account you are using.  Typically this is not the password for the root account.

---

### Post by daveandsheripetersen on 2009-01-17
I'm sorry, guess I didn't say it right.  Both my user and root passwords don't work.  I tried saying deny, the link seems to function normally, I just don't want to leave myself open to "attacks".
Dave

---

### Post by MaindotC on 2009-01-18
What do you need help with?

---

### Post by daveandsheripetersen on 2009-01-19
I want to know how to set my keyring password, or will I have to deny permission to get my wireless to work.  Sorry about the questions, I'm new to forums.
Dave

---

### Post by MaindotC on 2009-01-20
It's ok, Dave.  I didn't get those cups without my share of bruises, and I'll get more as the days go by.  Try the directions in this post [http://ubuntuforums.org/showpost.php?p=2089860&postcount=2](http://ubuntuforums.org/showpost.php?p=2089860&postcount=2)

---

### Post by daveandsheripetersen on 2009-01-20
Alan,
After checking in my keyring file I found I don't have a default keyring and I didn't think I should delete my login one. So what's next?
Dave

---

### Post by daveandsheripetersen on 2009-03-08
Alan,
I installed 8.10 with the card in the laptop and I don't have any password issues on 8.10 either. Thanks for all your help.  I'm starting to look at modifying my apparmor, but that will be a slow process.  Again thanks!

Dave

---

### Post by MaindotC on 2009-03-09
You should create a backup image of your installation so in the future if you have any issues you can restore to a state where everything is working for you (which I assume now you don't have any problems).

---

### Post by daveandsheripetersen on 2009-03-16
Alan,
I'm playing with an old laptop to get use to Ubuntu, so I didn't have anything to loose.  I appreciate the suggestion of a backup, I'll make sure I do that when I get to changing the "main" desktop over.  Thannnks for all your help.

Dave

---

### Post by MaindotC on 2009-03-17
Put links to your hardware in your sig like mine. It makes troubleshooting and helping others a lot easier.  Glad I could help (if I did) :D

---

