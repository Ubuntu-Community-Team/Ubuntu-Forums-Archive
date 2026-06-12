---
title: "how to secure harddisk"
date: 2010-09-19
forum: Security
---

### Post by m-r-r on 2010-09-19
hello,
is there any way to secure harddisk accessbility ?
i want encrypt my hard disk, and partitions that ubuntu installed on that.

is there a way ? i want deny all access to hard disk, just my own root account can have access to all.

---

### Post by serverfarm on 2010-09-19
Well its unclear what you want, so correct me if this isn't what your looking for, but truecrypt encrypts your whole hard drive and requires a password at boot to boot.  I would check it out though, its a cool program and its open source! [http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by Rubi1200 on 2010-09-19
Encryption is all good and well but don't forget that physical access = root access

---

### Post by bodhi.zazen on 2010-09-19
> **m-r-r said:**
> hello,
is there any way to secure harddisk accessbility ?
i want encrypt my hard disk, and partitions that ubuntu installed on that.

is there a way ? i want deny all access to hard disk, just my own root account can have access to all.

Ubuntu offers several options. The standard desktop install disk allows you to encrypt your home directory (ecryptfs) and that may work well for some.

Alternately use the Alternate CD and encrypt the entire install, this uses LUKS. With LUKS only /boot is un-encrypted. You can use ecryptfs with LUKS as well if yo u wish.

[http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

While you can install truecrypt, truecrypt (last time I looked) can not be used to encrypt the entire Ubuntu installation (that option is only supported for windows, not Linux).

---

### Post by serverfarm on 2010-09-19
> **bodhi.zazen said:**
> 

While you can install truecrypt, truecrypt (last time I looked) can not be used to encrypt the entire Ubuntu installation (that option is only supported for windows, not Linux).
I stand corrected, I never encrypted my main drive except in windows, sorry for the mix up.

---

### Post by bodhi.zazen on 2010-09-19
> **serverfarm said:**
> I stand corrected, I never encrypted my main drive except in windows, sorry for the mix up.

NP, it is a common misunderstaning as truecrypt is a nice option and it is popular.

FYI : you can mount a LUKS crypt on Windows if you ever wanted to switch.

[FreeOTFE - Windows LUKS]("http://www.freeotfe.org/")

---

### Post by m-r-r on 2010-09-20
thanks all for help.

look, here i have one PC, now on this system i have installed ubuntu 10.04 server to doing my work on it. but my friends appear to want knowing my information on this system, when the system powered down or not logged in, it's secure, but i want do some work to secure hard disk from access. 
for example if someone, moved my hardd disk and connected it to her system, nothing viewd to him,
this system, doing a little webserver and should powered up allways, so, whene power line dissconnect and connect again, system will comming up automaticly, and making password for boot time, denied this action.

what should i do to solve this ?

thanks again.

---

### Post by rookcifer on 2010-09-20
> **m-r-r said:**
> thanks all for help.

look, here i have one PC, now on this system i have installed ubuntu 10.04 server to doing my work on it. but my friends appear to want knowing my information on this system, when the system powered down or not logged in, it's secure, but i want do some work to secure hard disk from access. 
for example if someone, moved my hardd disk and connected it to her system, nothing viewd to him,
this system, doing a little webserver and should powered up allways, so, whene power line dissconnect and connect again, system will comming up automaticly, and making password for boot time, denied this action.

what should i do to solve this ?

thanks again.

As was stated above you will need to reinstall the OS from the alternate CD and encrypt the installation.

---

### Post by m-r-r on 2010-09-20
> **rookcifer said:**
> As was stated above you will need to reinstall the OS from the alternate CD and encrypt the installation.

and how it can possible ?

---

### Post by bodhi.zazen on 2010-09-20
> **m-r-r said:**
> and how it can possible ?

Follow the link I gave you in my first post.

---

