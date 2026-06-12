---
title: "Un-encrypting /home directory in Jaunty"
date: 2009-05-28
forum: Security
---

### Post by AstraCD08 on 2009-05-28
When I installed Jaunty, I mistakenly didn't realise that auto login feature in Ubuntu would not work together.

Could someone please shed some light on how I can decrypt my home directory so that I can use the auto login feature?

I should have realised that encrypting the home directory and using auto login defeats the purpose, but I didn't click with all the excitement of installing Jaunty.

Thanks in advance. ::D

---

### Post by Perkins on 2009-05-30
I have never done it.  But in theory it is fairly simple.  First, make a tar file of everything in your encrypted home directory.  Store it somewhere *not* in your home directory.  Then use your favourite search tool (eg. grep) to find where the command to mount your home directory as encfs is hiding.  Remove that command, unmount your home directory, delete all the encrypted files, and extract your tarball back into your home directory.

Please note, I have *never* done this with an encrypted home directory, only encrypted directories I had created myself.  I cannot make any promises about how well it will work.  It *should* work, but there might be something sticky that I know nothing about which could screw it up.  I highly recommend backing up your system before you start.

---

