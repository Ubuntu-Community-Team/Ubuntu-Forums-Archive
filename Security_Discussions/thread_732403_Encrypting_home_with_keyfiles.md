---
title: "Encrypting /home with keyfiles"
date: 2008-03-22
forum: Security Discussions
---

### Post by update_manager on 2008-03-22
When I move to hardy, I'd like to have my /home/<user> directory encrypted with a keyfile. The keyfile will be on a CD. 

I think the way to do this would be to use truecrypt, or maybe ccrypt.

So to encrypt:
ccrypt -rR -e -k /dev/sdc0/key /home/<user> 

and to decrypt:
ccrypt -rR -e -k /dev/sdc0/key /home/<user> 

This seems to work, although truecrypt may be faster.


If I did this, where should I put these commands (or scripts) at? I was thinking /etc/init.d/gdm would be a good place, but a GDM update could wipe 'em out.

Any ideas? Anyone think ccrypt will be too slow?

---

### Post by ubernoob on 2008-03-22
You would probably like to have the script in /etc/rc.local

I don't know ccrypt and truecrypt. But from google it seems like ccrypt encrypts files?

Have you had a look at dm-crypt and Luks (Linux Unified Key Setup)? That is pretty straight forward, and you will find documentation in the ubuntu wiki. 
The package name: cryptsetup

---

### Post by update_manager on 2008-03-22
> **ubernoob said:**
> You would probably like to have the script in /etc/rc.local

I don't know ccrypt and truecrypt. But from google it seems like ccrypt encrypts files?


Yes, ccrypt encrypts files. The -r flag tells it do it recursively, which makes if useful in this case.

Truecrypt makes a container, then decrypts the container. 

> 
Have you had a look at dm-crypt and Luks (Linux Unified Key Setup)? That is pretty straight forward, and you will find documentation in the ubuntu wiki. 
The package name: cryptsetup

I couldn't find any easy way to encrypt my home directory with a keyfile. Please don't let me reinvent the wheel.... :-D


I don't think /etc/rc.local will work - it only runs at startup (?)

---

