---
title: "Encrypted file server setup questions"
date: 2008-11-29
forum: Security
---

### Post by monsterthrash on 2008-11-29
Looking to build myself an Ubuntu Server-based file server but I have a question regarding encryption.

It's going to be headless, with administration through SSH and webmin.  I want to set up an encrypted RAID array but I don't want to have to type out a password every time I need to restart the machine to mount the RAID volume or when a machine on my network wants to access it.  What I would *like* to do is have a keyfile on a USB flash drive (or SD card if I get a card reader): If the keyfile is present, the RAID volume is decrypted and mounted, if not, Ubuntu boots like normal but the RAID volume remains encrypted and inaccessible.

Is this possible?  How would I set this up?

---

### Post by bodhi.zazen on 2008-11-29
I believe both LUKS and Truecrypt will do this.

LUKS :

[http://luks.endorphin.org/dm-crypt](http://luks.endorphin.org/dm-crypt)

[https://bugs.launchpad.net/gnome-mount/+bug/133520](https://bugs.launchpad.net/gnome-mount/+bug/133520)

[http://ubuntuforums.org/showthread.php?t=555513](http://ubuntuforums.org/showthread.php?t=555513)

Truecrypt :

[http://www.truecrypt.org/docs/?s=keyfiles](http://www.truecrypt.org/docs/?s=keyfiles)

[http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

---

### Post by monsterthrash on 2008-11-30
Thanks for the suggestions, I had completely forgotten about Truecrypt.  I'm testing this out on a virtual machine right now but the Truecrypt .deb has some dependencies i'm not liking (X11 and GTK).  I want to run this on a headless server and I don't need any GUI at all.  If there a way to install a command line only version?

---

### Post by hyper_ch on 2008-11-30
monster: if you want to setup an encrypted raid lvm I'd currently suggest to use Debian Lenny - if you want to use full disk encryption provided by luks/dm-crypt - as the initramfs isn't setup correctly yet in 8.04, 8.10 and debian etch.

---

### Post by monsterthrash on 2008-11-30
> **hyper_ch said:**
> monster: if you want to setup an encrypted raid lvm I'd currently suggest to use Debian Lenny - if you want to use full disk encryption provided by luks/dm-crypt - as the initramfs isn't setup correctly yet in 8.04, 8.10 and debian etch.

What do you mean?

---

### Post by hyper_ch on 2008-11-30
I think I misunderstood you :)

but why do you want to mount the encrypted drives only when the usb pendrive is in there?

---

### Post by monsterthrash on 2008-11-30
> **hyper_ch said:**
> I think I misunderstood you :)

but why do you want to mount the encrypted drives only when the usb pendrive is in there?

So I don't have to enter a password every time I reboot the server to mount the encrypted device, and so I can just take the USB/SD key with me (keeping the data encrypted) if i'm out of town for a while.  Yes, I can get paranoid sometimes.

---

### Post by hyper_ch on 2008-12-01
you can also remotely unlock/reboot the server if it's fully encrypted...

---

