---
title: "What can I use to encrypt all data on my USB flash drive"
date: 2010-04-18
forum: Security
---

### Post by e24ohm on 2010-04-18
Folks:
What can I use to encrypt all data on my USB flash drive? 

If possible, could I use something that has a public Key, so I do not have to type in a password to access the information when I plug the drive into my machie, but will not open or display contant if the drive is plugged into anyone else's machine, unless they have the public key?

---

### Post by HermanAB on 2010-04-18
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

### Post by FuturePilot on 2010-04-18
+1 for LUKS. It's also really easy to set up in Ubuntu 9.10. You can do it from System > Administration > Disk Utility.

---

### Post by node8472 on 2010-04-18
truecypt can do it and much more

---

### Post by e24ohm on 2010-04-19
> **node8472 said:**
> truecypt can do it and much moreIs truecrypt for Linux? I thought that was only for Windows.

In addtion, is there a way I can do this with pgp and make my keys?

---

### Post by jerome1232 on 2010-04-19
I really liked truecrypt, but luks can do the job as well.


Nice thing about truecrypt is it works with multiple OS's, as far as I know Luks is Linux only.

---

### Post by FuturePilot on 2010-04-20
> **jerome1232 said:**
> I really liked truecrypt, but luks can do the job as well.


Nice thing about truecrypt is it works with multiple OS's, as far as I know Luks is Linux only.

You can use LUKS on Windows too. [http://www.freeotfe.org/]("http://www.freeotfe.org/") (As long as the underlying file system can be read in Windows. i.e. FAT32)

---

### Post by DodgeV83 on 2010-04-20
> **HermanAB said:**
> [http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

These instructions should be updated, as it is now much easier to create the encrypted partition, at least with 10.04.

Simply right click on the drive from Places -> Computer and click Format -> "Encrypted, compatible with Linux (FAT)".

FreeOTFE can open this partition without any problem.

I'd like to have one small partition in the clear, with a portable version of FreeOTFE, along with an encrypted partition which can be opened either natively in Linux or with the portable FreeOTFE in the first partition in Windows.  Unfortunately, Windows only allows you to have one partition on USB drives, haven't yet found a way to use the portable FreeOTFE (on the usb stick) with an encrypted partition.  

Click here for more info on that:

[http://www.freeotfe.org/docs/Main/FAQ.htm#ed](http://www.freeotfe.org/docs/Main/FAQ.htm#ed)

Edit:  Oh yea, the FreeOTFE Explorer works in Wine (though I have had some crashes).  You can use that with .vol files on the USB Stick.  This will keep the main partition on your drive in the clear so you can quickly use it for non-sensitive data, but also give you the option to encrypt.  It's not as clean as mounting a partition, but it works.

Unlike Truecrypt or the normal FreeOTFE, the FreeOTFE Explorer does not require Administrator access to the machine.

---

