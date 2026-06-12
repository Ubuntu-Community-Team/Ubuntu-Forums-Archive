---
title: "Is this a security flaw"
date: 2005-07-07
forum: Server Platforms
---

### Post by coolclassic on 2005-07-07
Having just used the rescue mode in ubuntu 5.04 I was able to get access to the full system without a password. This must be a major flaw!

---

### Post by codejunkie on 2005-07-07
[QUOTE=coolclassic]Having just used the rescue mode in ubuntu 5.04 I was able to get access to the full system without a password. This must be a major flaw![/QUOTE]
no it's there for a reason just incase you need to have root access and you can't use sudo su because something is wrong with your user account.

---

### Post by LordHunter317 on 2005-07-07
And if you run sudo -s, you can do the same.  Not so much a flaw as a limit of UNIX's security model.

---

### Post by coolclassic on 2005-07-07
The point in having passwords is to restrict people having access to your computer, files,bankaccount, ect otherwise whats the point in having a password.

---

### Post by LordHunter317 on 2005-07-07
[QUOTE=coolclassic]The point in having passwords is to restrict people having access to your computer, files,bankaccount, ect otherwise whats the point in having a password.[/QUOTE]Yes, it is.

But it's not that simple.  What if the person who had the password forgot it?  Or what if they die?  Or what if the password database gets corrupted?

You always have to have a backdoor in.  Every operating system has them.  Every one has some way to bypass the normal privilege checks that occur.  In the case of Linux, it just happens to be pretty easy to do that.

---

### Post by Seq on 2005-07-07
[QUOTE=coolclassic]Having just used the rescue mode in ubuntu 5.04 I was able to get access to the full system without a password. This must be a major flaw![/QUOTE]

If somebody has physical access to your machine, then you've lost all security anyway. Booting from a live cd would allow you to mount the filesystem as well.

---

### Post by nocturn on 2005-07-08
First of, you can disable this (I often do).

But unless you lock down your bios (disallow booting from removable media, add passwords), anyone with physical access can just boot a liveCD and copy your data.

To be really safe, you would need an encrypted filesystem.

---

### Post by LordHunter317 on 2005-07-08
[QUOTE=nocturn]But unless you lock down your bios (disallow booting from removable media, add passwords),[/quote]Overriding the BIOS, even with a password, will take a competent attacker about 60 seconds unless you've also physically secured the machine (i.e., padlocked the case).  Even then, they still may be able to do it, as some BIOSes still have backdoor passwords.

---

### Post by coolclassic on 2005-07-08
My point is if you don't need a password to access root what is the point of having a password as user. You might as well have microsoft.

---

### Post by LordHunter317 on 2005-07-08
Because 99% of the time, the password is an effective measure.

Most attacks can't take advantage of the fact that if you're physically present at the machine, you can get root by rebooting into single user mode.

Just because it's problem in some cases doesn't mean it's a problem in all cases.

---

### Post by Mr. Electric Wizard on 2005-07-08
Or Knoppix

---

