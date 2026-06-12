---
title: "Lucid Server x86 Installation disk"
date: 2010-04-30
forum: Server Platforms
---

### Post by jgarner on 2010-04-30
I downloaded the x86 server version for Lucid twice today.  Both times before burn the md5 match those published on the Ubuntu site.

I am attempting to install the system on a Dell poweredge 2500.  2x 1.4 gb P4 procs, 1 gb ram, 750 GB HDD (raid)

Boot to installer.  it goes through the standard language checks, keyboard, checks for cdrom, then attempts to start copying files.

It gets to 17% copy on fs-core-modules-2.6.32.21-generic-di  and hangs there for 5 minutes or so.  Then comes back with the error that it could not get the file and asks if I want to retry.  all retries lead back to this error.

As I said, MD5 is exact, burner does not complain of a bad burn, and disk is closed at the end of the burn.  so, has anyone else been able to install Lucid server x86?

burned four disks today, one pair on two different burners.  All fail at 17% retrieving that file.

---

### Post by jgarner on 2010-04-30
I grabbed the 9.10 version,  it also does not grab the modules, although this time it is the nic modules.  maybe it is a Kernel thing with Ubuntu.  Either way, Ubuntu doesn't like older, stable server hardware it seems.  RH/Centos5, opensuse 11.x both install without any issues(suse 11.1 is what I am trying to install over).  Guess its time to give one of them a chance again..  

just did a manual network hardware attempt, it doesn't find the card! it's a 3com 3c905 onboard NIC..  so my point is made it seems, no support for older hardware..  sigh

epic.. FAIL!

---

### Post by iamgeniusrnti on 2010-05-23
You know what--I'll join you in the pitty party buddy.  

I just spent the entire morning googling and reburning the Ubuntu Server disc and the MD5 is perfect.  But my Dell 2450 simply gets stuck at 17% just like you said and then complains of an error.

I am sure there is a key combo I'm supposed to press, a dance I'm supposed to accomplish,  perhaps an earthquake that is supposed to occur during the install but this Ubuntu simply won't install... I wonder if I try to install an older version........

---

### Post by ingeva on 2010-05-24
> **iamgeniusrnti said:**
> You know what--I'll join you in the pitty party buddy.
Sorry, I can't join here, but I'll just tell you: My Lucid installed fine, but I couldn't use it with my regular keyboard because it was dead.
The computer is a Dell Vostro 400, and the keyboard is a Dell keyboard with wireless (Bluetooth).
Another keyboard worked fine, but as long as I can't use the wireless I'm better off with 9.10. I have some problems with that also, but that's another story. :)

---

### Post by iamgeniusrnti on 2010-05-25
Just to close the loop on this thread, I got it working by running the 6.06 Dapper Drake Server and then upgrading to 8.04 and then again straight to 10.04.  Virtually flawless.

---

### Post by tgalati4 on 2010-05-25
Well, resourcefulness is a trait of those who use Linux.  I'm runny hardy server on my older poweredge 1750.  It installed fine.  I was going to wait a while before upgrading to Lucid.

Why did you need to load Dapper, why not start with Hardy?

Also, isn't there a "Check CD" option on server installer?  That reads through all of the compressed binaries and compares the checksums for each one.  It's slow, but it will verify if your CDROM is working OK.

---

### Post by iamgeniusrnti on 2010-05-25
> **tgalati4 said:**
> Well, resourcefulness is a trait of those who use Linux.  I'm runny hardy server on my older poweredge 1750.  It installed fine.  I was going to wait a while before upgrading to Lucid.

Why did you need to load Dapper, why not start with Hardy?

Also, isn't there a "Check CD" option on server installer?  That reads through all of the compressed binaries and compares the checksums for each one.  It's slow, but it will verify if your CDROM is working OK.

Yes, there is a CD check and both Fedora and Ubuntu failed but the image checksum was spot on.  AND when I compared the disc to the ISO, windows said they were perfect.  Ergo, something with the CD rom drive or the controller could not tolerate the archives on the cdr.

I chose 6.06 primarily because Google told me to LOL!  Well after trying to install Fedora (amahi) and getting disc read errors and then got disc errors from 9.04, I had burned 12 of the 15 cdr and I really needed  I a sure fire method.

---

### Post by Z-95 on 2010-05-27
Its a known issue:
[https://bugs.launchpad.net/dru/+bug/148466](https://bugs.launchpad.net/dru/+bug/148466)
[http://ubuntuforums.org/showthread.php?t=858377](http://ubuntuforums.org/showthread.php?t=858377)

The workaround in bug comment 65 worked and let me install 9.10 and 10.04 on my PowerEdge 2450--you just need a 1GB USB stick.

---

### Post by iamgeniusrnti on 2010-05-27
> **Z-95 said:**
> Its a known issue:
[https://bugs.launchpad.net/dru/+bug/148466](https://bugs.launchpad.net/dru/+bug/148466)
[http://ubuntuforums.org/showthread.php?t=858377](http://ubuntuforums.org/showthread.php?t=858377)

The workaround in bug comment 65 worked and let me install 9.10 and 10.04 on my PowerEdge 2450--you just need a 1GB USB stick.

How did you find this?

---

### Post by iamgeniusrnti on 2010-05-27
> **iamgeniusrnti said:**
> How did you find this?

BTW, this is friggen brilliant, I wish you could have posted sooner!

---

### Post by trundlenut on 2010-05-28
I had problems installing 8.04 server on a poweredge 2800 and had the problems with copying the files.  It turned out that lens in the CD drive was dirty, when I checked the CD drive was full of dust, a quick clean and all was well.

---

