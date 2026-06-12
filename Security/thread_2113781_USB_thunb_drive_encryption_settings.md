---
title: "USB thunb drive encryption settings"
date: 2013-02-08
forum: Security
---

### Post by gendolookin on 2013-02-08
Hello all, 

I've tried googling this, and I can't find a decent answer.  I have a thumb drive that I use to store personal information. I have an encrypted filesystem on it using the LUKS encryption filesystem. 

The problem I have is that it only prompts me for the passphrase on the first mount.  Every time I mount it after that it doesn't ask for the passphrase.  

Is there a way to change the settings so it prompts for the pass every time I plug it in?  

Thanks all!

---

### Post by gendolookin on 2013-02-08
Nevermind, sorry I wasted everyones time LOL.  I just had to go in and delete the keyring password.  I had forgotten that i installed the gnome-encfs plugin. 

Problem solved.

---

