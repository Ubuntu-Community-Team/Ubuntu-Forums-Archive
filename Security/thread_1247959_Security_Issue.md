---
title: "Security Issue"
date: 2009-08-23
forum: Security
---

### Post by JoshStrobl on 2009-08-23
Ok, so I made an account for my dad on my Ubuntu laptop. I locked my computer and he somehow found a backdoor. Is there anyway I can lock all my programs and files? Don't know why he is so snoopy, but I like privacy.

---

### Post by bodhi.zazen on 2009-08-23
I am guessing your problem is physical access.

To some extent this is going to be an issue an issue to be worked out between you and your father. The ultimate privacy is to move out on your own and for you to get your own computer.

---

### Post by Chemical Imbalance on 2009-08-23
I would suggest encrypting your partition.

This isn't fool-proof.  But it's what I'd do.

---

### Post by ddrichardson on 2009-08-23
Are you sure you don't just have an easily guessed password? If you do, an encrypted partition is as much use as a chocolate fireguard.

---

### Post by JoshStrobl on 2009-08-23
bodhi.zazen- I'm 15, I wont be able to move out anytime soon. So that poses a problem. Also, this is MY computer, I bought it with MY MONEY, I set up an account FOR HIM yet he refuses to use it and uses mine.
ddrichardson- My password is 18 characters long and has nothing to do with anything. It is a mix of numbers and letters.

Encrypted partition? Would that protect him from accessing my programs and computer files? If so, how can I do so?

---

### Post by ddrichardson on 2009-08-23
18 letters means nothing if he knows it, which if he insists on using your account would imply.

---

### Post by JoshStrobl on 2009-08-23
> **ddrichardson said:**
> 18 letters means nothing if he knows it, which if he insists on using your account would imply.

he doesn't know any of my passwords, because I never save them. He is not familiar with Ubuntu, yet he still is able to access my files. I need a folder protection software or something. Any advice.

---

### Post by SunnyRabbiera on 2009-08-23
I wonder how he does it, in any case get encryption it will help.

---

### Post by aesis05401 on 2009-08-23
Set your bios and grub passwords.

Edit: P.S. This is useless unless you disable booting from cd-rom, USB,and network.  IF you need to boot in any of these manners then reenable the method in BIOS only long enough to accomplish your task.

---

### Post by ddrichardson on 2009-08-23
Well, your folder's standard permissions are not readable by anyone other than you and the root account. You're not being very clear as to how you're currently configured.

---

### Post by fela on 2009-08-23
Make your home folder only readable by you (or a certain group if you want). You can do this most easily by right clicking it in nautilus and making everything except yourself have 'no access'. Make sure to click 'apply to all folders within' or whatever it's called.

Then make a secure password and don't tell your dad it. He can always access your files with a livecd, unless you encrypt your home directory aswell.

---

### Post by aesis05401 on 2009-08-23
> **fela said:**
> Make your home folder only readable by you (or a certain group if you want). You can do this most easily by right clicking it in nautilus and making everything except yourself have 'no access'. Make sure to click 'apply to all folders within' or whatever it's called.

Then make a secure password and don't tell your dad it. He can always access your files with a livecd, unless you encrypt your home directory aswell.

:) Encryption makes everything harder - especially disaster recovery.  Use boot process control instead to combat the livecd issue.

---

### Post by JoshStrobl on 2009-08-23
when I locked my screen so he couldn't get into my account, somehow he was able to get in.

I know there is a backdoor through boot, so what program should I use to password lock my folders. I clear my history and everything on firefox so I'm not worried about or my programs just my files.

Is there some sort of password protector for folders like on Windows except for Linux?

---

### Post by scorp123 on 2009-08-23
> **JoshStrobl said:**
>  Is there some sort of password protector for folders like on Windows except for Linux?

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by aesis05401 on 2009-08-23
> **JoshStrobl said:**
> when I locked my screen so he couldn't get into my account, somehow he was able to get in.

I know there is a backdoor through boot, so what program should I use to password lock my folders. I clear my history and everything on firefox so I'm not worried about or my programs just my files.

Is there some sort of password protector for folders like on Windows except for Linux?

It is built-in.  Every file and folder has permissions, owners and grouping capabilities.  If he is logging into your account without using a boot-time vector or guessing your password then you have bigger problems.  

I would nuke the install personally.  You should present him with a bill for your time to recover your sense of security following his immature shenanigans ;)  Seriously, though, unauthorized use of a computer is not cool on any level unless you are trying to survive a zombie attack or trying to pass an unpassable StarFleet test.

You should find a good way to let him know.

---

### Post by JoshStrobl on 2009-08-23
set up new password, changed user privilages for  my dad's account, changed security for lock screen.

---

### Post by lisati on 2009-08-23
> **aesis05401 said:**
> 

You should find a **good way** to let him know.

**_Very important:_** foster a good relationship with your parents and any other "responsible adults" in your life. That way it will be easier to have a sensible discussion with them about respecting your privacy and about discovering why your Dad insists on looking at your data. 
Hopefully it will turn out to be something innocent like being concerned that you're not getting yourself into trouble with your gear.

---

