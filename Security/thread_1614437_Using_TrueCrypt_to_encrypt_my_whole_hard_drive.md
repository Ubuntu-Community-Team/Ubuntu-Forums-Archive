---
title: "Using TrueCrypt to encrypt my whole hard drive"
date: 2010-11-05
forum: Security
---

### Post by okayneil on 2010-11-05
So what I want to do is encrypt my entire hard drive, but heres the thing. 

I dual boot Ubuntu and windows 7, but I am afraid that if I use truecrypt to do the encrypting that it will wipe GRUB and not allow me to boot into any OS, is that a possibility and is there a way around it?

Cheers.

---

### Post by HermanAB on 2010-11-06
Howdy,

First of all, you can never encrypt the whole hard disk.  Some piece must be plain text (MBR and /boot) to allow the machine to boot up.

You correctly figured out that the MBR, Windows and Linux partitions would need to be handled separately.  You can make an encrypted Ubuntu system by using the Alternate CD.

---

### Post by okayneil on 2010-11-06
So if I wanted to encrypt my entire drive (without the MBR//boot) basically I would only need to have one OS otherwise things are going to get complicated?

Can I encrypt my ubuntu partition without having to do a new install and wiping my MBR?

---

### Post by olepi on 2010-11-06
I think what Herman was saying is that the /boot partition of the hard drive cannot be encrypted. If it is, the computer will not see anything on the hard disk during boot up and ask you where your operation system is.

Using Truecrypt to encrypt a windows installation, alongside a ubuntu installation encrypted with dmcrypt (truecrypt will only fully encrypt windows), would be somewhat complicated.  So much so that I never tried it.  

It is possible to have the uncrypted /boot partition on a usb key. You could install the usb key at boot-up, then the computer would know how to decrypt the /root /swap and /home partitions on your hard drive.  In this situation, everything on the hard disk would be encrypted.

Hope that makes a little sense.

---

### Post by HermanAB on 2010-11-07
Howdy,

On a home system, it should be sufficient to encrypt /home and leave the rest of the system in plain text.  You can do that with some juggling.  

You first need to backup your data, then boot into single user mode, unmount /home, encrypt it and then reboot, log in and copy your data back to the encrypted /home.

---

### Post by newboyo on 2010-11-08
> **HermanAB said:**
> Howdy,

On a home system, it should be sufficient to encrypt /home and leave the rest of the system in plain text.  You can do that with some juggling.  

You first need to backup your data, then boot into single user mode, unmount /home, encrypt it and then reboot, log in and copy your data back to the encrypted /home.

To do this, I plan to -
1. backup my data to an external HDD
2. load gparted and format existing /home.

What should I do next? Suggestions/instructions would be most appreciated.


thanks

---

### Post by HermanAB on 2010-11-09
You don't need to format /home.  It will be overwritten anyway.

This may help:
[http://www.aeronetworks.ca/howtos/luks-usb-howto.html](http://www.aeronetworks.ca/howtos/luks-usb-howto.html)

---

### Post by alphaamanitin on 2010-11-09
Using TC you can set up a hidden OS, and encrypt the entire hard drive.  Truecrypt installs its own MBR from what I read.  However, this feature of making a whole disk encryption and hidden OS in TrueCrypt does not support linux distros.  You should read bodhi.zazens blog about setting up encrypted drives and home partitions.  I know some of these are cross platform and will work with your windows boot as well.

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

AlphaA

---

