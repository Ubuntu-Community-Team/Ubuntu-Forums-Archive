---
title: "Creating a cryptocd"
date: 2010-11-16
forum: Security
---

### Post by troubleshot on 2010-11-16
I have found numerous guides:
[http://ubuntuforums.org/showthread.php?t=579173&highlight=aespipe](http://ubuntuforums.org/showthread.php?t=579173&highlight=aespipe)[http://savvyadmin.com/create-encrypted-cds-and-dvds-in-linux/](http://savvyadmin.com/create-encrypted-cds-and-dvds-in-linux/)

This one is insane but it works but it takes far too long:
[http://www.gentoo-wiki.info/HOWTO_Burn_Encrypted_Optical_Media_With_Luks#Start](http://www.gentoo-wiki.info/HOWTO_Burn_Encrypted_Optical_Media_With_Luks#Start)

Using the first guides listed I try 'sudo modprobe cryptoloop' after having installed loop-aes-utils but the module is not there. I cannot proceed until this is fixed what am I supposed to do?

I have tried using 'dd if=/dev/urandom of=cryptocd.iso bs=1M count=4400' but dd cannot get the size right, the file size is usually larger that the 4.4 gigs I have specified, can someone help me with this? I then use luksFormat, then I open it to format it but I do not know how to get it to format to a cd type of fs, do you?

---

