---
title: "Adding encryption to laptop"
date: 2009-07-13
forum: Security
---

### Post by cmnorton on 2009-07-13
Already passed, new tough data security laws are about to be enacted in Massachusetts. I need to add encryption to my LTS Kubuntu 8.04 system. 

What is the best way to do that? 

Kubuntu is installed on a Thinkpad T61p.

---

### Post by tubbygweilo on 2009-07-13
cmn, 
would it be possible to post a link to the new laws as encryption may not be the only thing you have to consider?

---

### Post by cmnorton on 2009-07-13
[http://www.cmr17.com/](http://www.cmr17.com/)

---

### Post by HermanAB on 2009-07-14
You should use LUKS of course.  It is actually quite simple to use LUKS to encrypt a drive.  Just read these man pages:
man cryptsetup
man luks-tools
man crypttab
man fstab

You could also look at my recent wizards - read the Perl code to see some tricks:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

### Post by shaggy999 on 2009-07-16
To be honest, the best way to setup encryption is to start from scratch and install your OS using the alternate CD.

---

### Post by bodhi.zazen on 2009-07-16
> **HermanAB said:**
> You should use LUKS of course.  It is actually quite simple to use LUKS to encrypt a drive.  Just read these man pages:
man cryptsetup
man luks-tools
man crypttab
man fstab

You could also look at my recent wizards - read the Perl code to see some tricks:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

+1

> **shaggy999 said:**
> To be honest, the best way to setup encryption is to start from scratch and install your OS using the alternate CD.

That is a broad statement and there are several options for encryption post install including Truecrypt, LUKS, ecryptsfs, etc, etc. You can encrypt swap post install if you wish.

I also agree that a fresh install has advantages as well.

---

