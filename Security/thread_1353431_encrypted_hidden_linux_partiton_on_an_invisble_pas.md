---
title: "encrypted hidden linux partiton on an invisble passworded boot loader"
date: 2009-12-12
forum: Security
---

### Post by fireandspike on 2009-12-12
HI ,  
 

 I'm just about to install ubuntu after using it from a usb stick for a few days. I'll be using it to work with some sensitive IP information and I need to use some secure encryption and an obscure linux system incase my laptop falls into the wrong hands.
 

 What I need is this,
 

 boot into an invisible boot loader that does not appear on screen just boots straight into a windows partition on disk A. However if the right key combinations are held down (known only to me) after the BIOS has loaded the system does not boot to windows it asks for a password which if entered correctly boots to a full encrypted hidden Linux partition on drive B. I also need the Linux swap encrypted too. The encrypted partition should encrypt and decrypt files on the fly as they are written and read.
 

 Now heres the hard obscure part,  
 

 If it boots to windows as mentioned, then drive B to windows looks like an unformatted blank disk so somebody sniffing around to try and find the encrypted data cannot see it because windows says there is nothing there. Also when programs that detect and modify partitions such a G parted, partition magic etc. are run on the drive they also see it as an unformatted disk with no partition. In other words there is no way to tell that there is a hidden encrypted Linux partition on it.  
 

 Is there anyway to do this with ubuntu? 
 

 Thankyou for your time

---

### Post by bodhi.zazen on 2009-12-12
I do not believe there is any way to do this with any OS. If someone has physical access encryption will protect your data ...

[indent]... to a point[/indent]

[img]http://imgs.xkcd.com/comics/security.png[/img]

But seriously, anyone with physical access can easily either defeat your desired security measures or the technology does not exist (you really can not hide an encrypted partition for example).

---

### Post by tubbygweilo on 2009-12-13
Standard answer number 538. Always good in these situations.

---

