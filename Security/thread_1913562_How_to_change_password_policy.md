---
title: "How to change password policy?"
date: 2012-01-22
forum: Security
---

### Post by SchneiderIS on 2012-01-22
It would appear the someone, in their absolute winsome, has once again decided to cram their ideas down everyones throat.  Specifically the password policies and not allowing simple words.  I can get that this would be important to some corporation hell bent on keeping thing secure but for the average home user with a box that is not exposed to the internet this has absolutely no benefit!!!  

What is worse is that it was deployed via a service patch and without warning which is now costing me several hours worth of error correction to get cleaned up.

Actually it gets even worse!  I can't find anywhere to actually change this criteria and the new Unity interface is proving itself just as useless on this front as all others.

It is coming down to trying to decide how much time would be burned up fixing all these issues vs just changing to Mint or some other distribution.

---

### Post by emiller12345 on 2012-01-22
I don't want to mess things up worse, but have you tried using the command
```
$ sudo passwd username
```where username is the name of the user, whose password you want to change?
I've tried it on my Lucid i386 Server and it has no problems with short passwords

---

### Post by SchneiderIS on 2012-01-22
> **emiller12345 said:**
> I don't want to mess things up worse, but have you tried using the command
```
$ sudo passwd username
```where username is the name of the user, whose password you want to change?
I've tried it on my Lucid i386 Server and it has no problems with short passwords

I did and eventually I got to a point where at least I have things working.  There is still a problem though in that the admin account can't have a simple password.  All others can but not the primary account of the machine.  This was not the case when I installed 11.10 before Christmas but it is now.

---

### Post by SchneiderIS on 2012-01-24
I spoke to soon.

Somehow the system, which has been working for over 24 hours, suddenly reverted back!  It now doesn't reboot based on menu selections and it won't accept connections via VNC or from my MythTV fronted.  I had to reboot through the command line with "sudo reboot" and then it was responding again.

Arg!!!

---

