---
title: "LUKS - Change Authentication mechanism"
date: 2009-12-19
forum: Security
---

### Post by michael_schmid on 2009-12-19
Hello forums!

Initial situation:


[LIST]
[*]Karmic Koala (x64) installed from alternate CD
[*]Root, swap and /home are LUKS-encrpyted, using AES and passphrase authentication mode. The passphrase is the same for all 3 partitions. When my system is starting up I have to enter said password 3 times.
[/LIST]

Now to my questions:


[LIST=1]
[*]Is it possible to change the authentication mode from passphrase to "external " key file (from an USB stick) in a running system? If yes, how can I achieve this?
[*]Can I use the passphrase authentication as a fallback mode in case the USB stick gets stolen?
[/LIST]
Thanking you in anticipation,
Michael

---

### Post by rookcifer on 2009-12-19
Is your problem that you don't want to enter the password 3 times?  If so, you don't have to -  you can enter it once to unlock all partitions if you have setup LVM.  Since you obviously didn't do this when you encrypted your disk, you will need to go back and reinstall unfortunately.  

If you choose to do this, you can use [this guide]("http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/") to get it set-up properly.

---

### Post by michael_schmid on 2009-12-19
Thanks for your answer and the link rookcifer, I know about the LVM option and it will be my plan B if there exists no other solution. I'd still like to know if it's possible to switch from passphrase to key (file)-based authentication without reinstalling the whole system. Does anyone know if that is possible at all?

---

