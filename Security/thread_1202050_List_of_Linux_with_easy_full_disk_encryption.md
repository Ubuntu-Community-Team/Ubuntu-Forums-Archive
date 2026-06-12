---
title: "List of Linux with easy full disk encryption"
date: 2009-07-01
forum: Security
---

### Post by WarholsGhost on 2009-07-01
hello all,

i think it's time we push more people into installing full disk encrypted linux with that in mind, it would be nice to have a list of easy to install FDE linux distros, so far i have the 3 'buntus

THE LIST:
Ubuntu
Kubuntu
Xubuntu
Fedora 11 [http://fedoraproject.org/get-fedora](http://fedoraproject.org/get-fedora)

---

### Post by bodhi.zazen on 2009-07-01
Fedora 11

Simply click the encryption option during installation, even easier, IMO, then Ubuntu, which involves the alternate CD.

---

### Post by u-slayer on 2009-07-01
You don't need an alternate CD. Just format your drive with cryptsetup. Then unzip the initrd image in your /boot folder, edit the script that mount's your hard drive to ask for a password. Include any neccesary binaries and rezip the cpio archive.:-P

---

### Post by WarholsGhost on 2009-07-01
do you have a together how-to with pictures on how to do that? encryption can get really confusing and i'v failed every time i'v tried it not using a reconfigured cd. I'm trying to do this for beginners so we can spread doing FDE

---

### Post by bodhi.zazen on 2009-07-01
> **u-slayer said:**
> You don't need an alternate CD. Just format your drive with cryptsetup. Then unzip the initrd image in your /boot folder, edit the script that mount's your hard drive to ask for a password. Include any neccesary binaries and rezip the cpio archive.:-P

You could do it that way, but it will not be so easy, you are missing a few steps in your "how to".

---

### Post by u-slayer on 2009-07-01
> **bodhi.zazen said:**
> You could do it that way, but it will not be so easy, you are missing a few steps in your "how to".

I actually did do it that way. Of course I had to put /boot on a usb drive, and do the whole grub-install thing, but I think my post capture the basic idea.

---

### Post by Dr Small on 2009-07-01
> **bodhi.zazen said:**
> Fedora 11

Simply click the encryption option during installation, even easier, IMO, then Ubuntu, which involves the alternate CD.
I had a brainstorm idea for this on Ubuntu awhile back. I think it got lost into oblivion...

---

### Post by michaelzap on 2009-07-01
> **WarholsGhost said:**
> i think it's time we push more people into installing full disk encrypted linux

I just stopped encrypting my entire disk now that Jaunty does easy home directory encryption. I like that better than having two passwords, and for multi-user machines this seems like a more secure method. Are you opposed to home directory encryption instead of FDE?

I know that there are swap and log file issues to be addressed, but there are ways to deal with those.

AFAIK, Debian does FDE easily also:
[http://madduck.net/docs/cryptdisk/](http://madduck.net/docs/cryptdisk/)

---

### Post by bodhi.zazen on 2009-07-01
> **u-slayer said:**
> I actually did do it that way. Of course I had to put /boot on a usb drive, and do the whole grub-install thing, but I think my post capture the basic idea.

Basic idea yes. Your how to is, however, as has been pointed out, a bit scant on details. 

Certainly not the "easy full disk encryption" the OP is seeking.

---

### Post by WarholsGhost on 2009-07-01
i like the idea of having it fully encrypted better, but this is about more than ubuntu, encryption in ubuntu is good, but i want to make sure it's easier and more available

---

### Post by bodhi.zazen on 2009-07-01
> **Dr Small said:**
> I had a brainstorm idea for this on Ubuntu awhile back. I think it got lost into oblivion...

Would be nice.

> **WarholsGhost said:**
> i like the idea of having it fully encrypted better, but this is about more than ubuntu, encryption in ubuntu is good, but i want to make sure it's easier and more available

At this time you can not encrypt /boot or the BIOS / MBR. The best you can do is to move /boot to a USB and physically remove the USB after booting (you would only need to replace and mount it when updating the kernel or grub).

---

### Post by Dave_Connor on 2009-07-02
I know full disk encryption is VERY safe and even more with keeping your key on a usb drive but the only reason for me not using key is in case of having to reinstall and recovering data off the hard drive. I already have backups but I guess it is due to my paranoia with hard disk failure.

---

