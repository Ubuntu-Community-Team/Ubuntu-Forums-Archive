---
title: "Security Issue in Jaunty"
date: 2009-05-11
forum: Security
---

### Post by ierpe on 2009-05-11
Im having problems with my graphic driver and so I booted in recovery mode.

What surprised me is when you ask for a root shell, it doesnt ask you for a password!!?

Means that anyone can just come, start my computer in recovery mode and have a root access?

What a ****? :p

---

### Post by sisco311 on 2009-05-11
> **ierpe said:**
> 
What surprised me is when you ask for a root shell, it doesnt ask you for a password!!?



That is because the root password is locked by default.

[thread=989517]Physical access is root access[/thread]

---

### Post by ubersolid on 2009-05-11
Anyone with physical access to any machine can do just about anything to it. If you want it more "secure" set a BIOS password + a GRUB password. And disable booting from USB and CD. This goes for any OS. And it still wouldn't be totally secure.

---

### Post by ierpe on 2009-05-11
> **ubersolid said:**
> Anyone with physical access to any machine can do just about anything to it. If you want it more "secure" set a BIOS password + a GRUB password. And disable booting from USB and CD. This goes for any OS. And it still wouldn't be totally secure.

Ok fair enough, its true. But I have a bios password and booting is disabled. Means that its actually not that easy anymore.

And then if you want to leave limited access to other users you're not gonna put a grub password. 

So I still think that asking for a password when you start in recovery mode would be better than not asking for it.

---

### Post by cdenley on 2009-05-11
> **ierpe said:**
> Ok fair enough, its true. But I have a bios password and booting is disabled. Means that its actually not that easy anymore.

And then if you want to leave limited access to other users you're not gonna put a grub password. 

So I still think that asking for a password when you start in recovery mode would be better than not asking for it.

Probably the most common reason for using recovery mode is because the user forgot their password. The only other reason I can think of is if xserver fails in a way that prevents you from dropping to the terminal (ctrl+alt+f1).

---

### Post by ashmew2 on 2009-05-11
> **ierpe said:**
> Im having problems with my graphic driver and so I booted in recovery mode.

What surprised me is when you ask for a root shell, it doesnt ask you for a password!!?

Means that anyone can just come, start my computer in recovery mode and have a root access?

What a ****? :p

wow..thats a loophole as far as i know..I mean the *root* can up*root* your data..

---

### Post by bodhi.zazen on 2009-05-11
This is a recurring discussion and so I am going to close this thread now.

Physical access = bad news, regardless of OS.

You can do things such as setting a BIOS password or a grub password, but those techniques are easily defeated.

You can set a root password if you wish, but there are disadvantages of that option as well, including opening other security holes.

Physical access allows one to boot a live CD and or pull the hard drive and full system access is not far behind.

The only thing you can do to protect your data is to encrypt the data and / or limit physical access.

---

