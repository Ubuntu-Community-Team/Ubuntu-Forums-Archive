---
title: "Chroot without internet connection"
date: 2010-10-26
forum: Security
---

### Post by wyrdrat on 2010-10-26
Hi

I was hoping to set up a Kubuntu 10.04 Chroot on a PC with no internet access (I only have dialup anyway, not Broadband).  All the information I have been able to find refers to downloading debootstrap in order to do this.

I purchased a set of DVDs with all of the Ubuntu packages on them and created a single repository of them on my harddrive.

Is there some way that I can create the Chroot using the packages on my hard drive without having to access the internet to download stuff as I do it?

Thanks for any help.

Cathy

---

### Post by kreggz on 2010-10-26
You should be able to download debootstrap from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and then when you setup the chroot environment you can change the package sources to your local cdrom in theory.

---

### Post by wyrdrat on 2010-10-27
Thanks for getting back to me.  Won't that be the same debootstrap that I have in my own repository?  Everything I have read implies that it goes online to get some files when it is run, which I can't do.

I thought it should be able to use a local repository in theory, but being a bit thick I can't work out how to do it in practice.

Thanks for any more advice.

Cathy

---

### Post by CharlesA on 2010-10-27
I think you would need to set software sources to use the cd/dvd instead of the online repo, but I'm not 100% sure how to do that.

---

### Post by kreggz on 2010-10-27
this bug report indicates you can but there are some issues to work around [https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589](https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589)

---

### Post by wyrdrat on 2010-10-28
Thanks everyone for your help.

---

### Post by wyrdrat on 2010-10-30
I have got debootstrap to recognise my hard drive repository, but although it finds and validates the packages and resolves dependencies it then says

w:couldn't download package

Any ideas?
Thanks

---

