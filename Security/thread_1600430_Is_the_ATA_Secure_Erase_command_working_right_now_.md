---
title: "Is the ATA Secure Erase command working right now? I first tried to use UBCD HDDEras"
date: 2010-10-18
forum: Security
---

### Post by dialxdrop on 2010-10-18
I first tried to use UBCD HDDErase although it won't detect my seagate  1000 GB Sata HD (This worked for my other computer/HD). So I loaded up a  OpenSUSE live cd rescue terminal to enter the command (of course after  setting a password and making sure HD is not frozen): (My Ubuntu livecd didn't work on this motherboard so i used Suse)

time hdparm --user-master u --security-erase uber /dev/sda

**The following line appears:**
"Issuing SECURITY_ERASE Command, password="uber", user=user
[B]
That's all it says and there is no % completed or anything. [/B](as it  appears on the wiki)
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

Also I can still type but theres no command or console or anything it  just is blank if I hit enter.


Is my HD being wiped right now? or is it not working?

---

### Post by HermanAB on 2010-10-19
Use Data Definition - or better yet, a big hammer.

$ sudo dd if=/dev/urandom of=/dev/sdaX
Long wait...

The hammer method is however much more satisfying...

---

### Post by dialxdrop on 2010-10-19
> **HermanAB said:**
> Use Data Definition - or better yet, a big hammer.

$ sudo dd if=/dev/urandom of=/dev/sdaX
Long wait...

The hammer method is however much more satisfying...

HermanAB, well I am sure that this hammer method will also be satisfying, however hdparm should do the trick for me...

but is my hdparm command working correctly? Its not displaying anything... How do I know if its working or not? 

(BTW I am trying it on Ubuntu live cd now and same thing happened although Ubuntu is working normal in the background)

---

### Post by dialxdrop on 2010-10-19
[B]Updates:
[/B]3 hours passed and then it appears to have worked? 

**Here is the final display message:**
 Issuing SECURITY_ERASE command, password="uber", user=user
0.00user 0.00system 2:00:24elapsed 0%CPU (0avgtext+0avgdata 1984maxresident)k
0inputs+0outputs (0major+167minor)pagefaults 0swaps

**My master password is still enabled after the wipe? It shouldn't be**:
After a successful wipe operation, the drive security should automatically be set to disabled although my security still displays "Master password.... **enabled**" vs ***not***** enabled**.

Does anyone know if this operation worked? And if so, how do I change the password back to null?

---

### Post by cariboo on 2010-10-19
In a lot of cases some operation doesn't take place until a reboot. have you rebooted and checked your security password?

---

