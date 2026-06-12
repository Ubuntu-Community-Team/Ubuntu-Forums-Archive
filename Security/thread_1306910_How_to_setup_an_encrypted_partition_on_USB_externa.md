---
title: "How to setup an encrypted partition on USB external HDD?"
date: 2009-10-30
forum: Security
---

### Post by olivertreend on 2009-10-30
Hi

I have been looking all over these forums and over the internet to find out how to do this. And so far, I've only found dead ends. I know this is possible to do - and I'm sure a lot of people do it - but for some reason I can't find anywhere that easily documents how to do it.

I have a 1TB external hard drive. I'd like to connect it to my Ubuntu Server box and use [BackupPC]("http://backuppc.sourceforge.net") to take backups of several desktops on the network.

I'd like this external drive to be encrypted, but still be accessed like a normal drive - I think this is possible through LVM e.g. /dev/mapper/crypt/mydrive although I'm not sure how to do it. None of the partitions or drives in the rest of the Ubuntu Server setup are encrypted - it's only this one drive.

[http://jeltsch.org/node/457]("http://jeltsch.org/node/457")
This article seemed pretty informative, but I found it rather confusing and didn't understand what exactly was going on.

How would I go around encrypting my external drive's partition?

I would be extremely grateful if someone could post instructions or a mini howto walking me through how to set this up. Or maybe you could point me in the right direction with a link to another forum post?

Cheers :D

Oliver

---

### Post by bodhi.zazen on 2009-10-30
[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

### Post by OpenSourceFuture on 2009-10-30
This could also be easily accomplished with truecrypt.

---

### Post by XCan on 2009-10-30
I vote for truecrypt as well. For me, it was the easiest to get running, and it's multiplatform (provided you use a "multiplatform" filesystem of course).

---

### Post by olivertreend on 2009-10-31
How would I go about encrypting the partition with Truecrypt?
I've used Truecrypt under Windows a fair amount, but not from the command line.

At the moment, I have Truecrypt installed on my Ubuntu Server box. I also have the 1TB volume plugged in and mounted.

Where can I go from here?

I've tried looking around for tutorials, but I'm finding it hard to get my head around. I'd really appreciate some simple and easy to follow instructions or tips.

Cheers again :D

---

### Post by bodhi.zazen on 2009-10-31
> **olivertreend said:**
> How would I go about encrypting the partition with Truecrypt?
I've used Truecrypt under Windows a fair amount, but not from the command line.

At the moment, I have Truecrypt installed on my Ubuntu Server box. I also have the 1TB volume plugged in and mounted.

Where can I go from here?

I've tried looking around for tutorials, but I'm finding it hard to get my head around. I'd really appreciate some simple and easy to follow instructions or tips.

Cheers again :D

Everything you would want to know (and more) is documented on the TrueCrypt home page:

[http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

---

### Post by XCan on 2009-10-31
> **olivertreend said:**
> How would I go about encrypting the partition with Truecrypt?
I've used Truecrypt under Windows a fair amount, but not from the command line.

At the moment, I have Truecrypt installed on my Ubuntu Server box. I also have the 1TB volume plugged in and mounted.

Where can I go from here?

I've tried looking around for tutorials, but I'm finding it hard to get my head around. I'd really appreciate some simple and easy to follow instructions or tips.

Cheers again :D

It should work more or less the same as in Windows. Sure you can run it from the command line but there is a GUI included that is more or less identical to the Windows versions'. Have you looked in your menu Applications -> Others? After I installed Truecrypt it resides there.

---

### Post by tubbygweilo on 2009-10-31
Oliver,
if using 9.10 the Trucrypt application can now be found in Application>Accessories. 
It has moved places from 9.04 to 9.10.

---

### Post by olivertreend on 2009-10-31
> **XCan said:**
> It should work more or less the same as in Windows. Sure you can run it from the command line but there is a GUI included that is more or less identical to the Windows versions'. Have you looked in your menu Applications -> Others? After I installed Truecrypt it resides there.

Wow! I didn't even realise that TrueCrypt came with a GUI on Linux! That'll come in handy next time!
This time round, I've decided to encrypt it under Windows since the encryption is cross platform.

I've found a pretty good tutorial for using TrueCrypt command line under Linux here: [http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)
It seems pretty informative and easy to follow.

---

### Post by HermanAB on 2009-11-01
Here you go:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

