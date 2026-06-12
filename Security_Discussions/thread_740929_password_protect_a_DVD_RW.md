---
title: "password protect a DVD RW"
date: 2008-03-31
forum: Security Discussions
---

### Post by sergiom99 on 2008-03-31
Hey there, I want to passwrod-protect a DVD+RW with some of my files.
So that only my user can open it, and maybe it wont play anywhere else without the password. Is there a way to do it in linux?

BTW: What's the best way to mount a DVD ISO file in Kubuntu? I installed Gmount ISO but it always get an error when loading the file.

Thanks for your help.

---

### Post by FluffyElmo on 2008-03-31
I think your best bet would be to use Truecrypt to encrypt the data. You can then include the Truecrypt executables outside the encrypted partition and decrypt anywhere.

Never seen it used on DVD specifically but many people use it on their USB thumb drives which is a similar application. I'd probably encrypt the data on your hard drive and then burn the encypted file to the disk to save wear and tear on the DVD-RW.

Here are instructions for Windows, doing it on Ubuntu would probably be similar, check the Truecrypt site for some of the options.
[http://glosoli.blogspot.com/2005/09/encrypted-thumb-drive-and-autoplay.html]("http://glosoli.blogspot.com/2005/09/encrypted-thumb-drive-and-autoplay.html")


I usually just mount isos from the command line, the following will mount  image.iso at /media/cdrom but you can change it to any directory you want.
```
sudo mount -o loop image.iso /media/cdrom
```

---

### Post by sergiom99 on 2008-03-31
> **FluffyElmo said:**
> I think your best bet would be to use Truecrypt to encrypt the data. You can then include the Truecrypt executables outside the encrypted partition and decrypt anywhere.

Thanks! I'll take a look at it.

> 
I usually just mount isos from the command line, the following will mount  image.iso at /media/cdrom but you can change it to any directory you want.
```
sudo mount -o loop image.iso /media/cdrom
```
Thanks again.
I thought some special command was required to mount an ISO. what's -o?

Regards-

---

### Post by cdenley on 2008-03-31
> I thought some special command was required to mount an ISO. what's -o?
The "-o" is used to set the mount options. The "loop" option means you are mounting the filesystem from a file, not a device.
```

man mount

```

---

