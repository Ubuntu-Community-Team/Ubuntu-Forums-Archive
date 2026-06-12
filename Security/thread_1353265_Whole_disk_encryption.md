---
title: "Whole disk encryption"
date: 2009-12-12
forum: Security
---

### Post by LinuxFanBoi on 2009-12-12
Anyone know of any solid apps that will allow a user to encrypt their entire hard disk in Linux?  Specifically employing, encrypt/decrypt on the fly, Doesn't require a clean install,  pre-boot authentication.

I know Truecrypt can do this with windows, and I've used it before and it's solid, but it would be nice to know if there is a Linux counterpart.

---

### Post by pwnst*r on 2009-12-12
> **LinuxFanBoi said:**
> Anyone know of any solid apps that will allow a user to encrypt their entire hard disk in Linux?  Specifically employing, encrypt/decrypt on the fly, Doesn't require a clean install,  pre-boot authentication.

I know Truecrypt can do this with windows, and I've used it before and it's solid, but it would be nice to know if there is a Linux counterpart.

it can also do it with Linux, iirc.

---

### Post by Keyper7 on 2009-12-12
Never used it myself, but I heard the Linux version of Truecrypt does its job quite well.

---

### Post by FuturePilot on 2009-12-12
> **pwnst*r said:**
> it can also do it with Linux, iirc.

AFAIK it can't. Check out the Ubuntu alternate installer. It gives you can option to setup full disk encryption.

---

### Post by LinuxFanBoi on 2009-12-12
> **FuturePilot said:**
> AFAIK it can't. Check out the Ubuntu alternate installer. It gives you can option to setup full disk encryption.

Just what I thought,  It doesn't yet have full disk encryption but does encrypted containers quite well.

Wouldn't the alternate installer require a full re-installation?

---

### Post by pwnst*r on 2009-12-12
i think you're right.  although i can't find where it says specifically that it cannot encrypt a linux system, linux and mac osx are missing from that specific list.

[http://www.truecrypt.org/docs/?s=system-encryption](http://www.truecrypt.org/docs/?s=system-encryption)

---

### Post by WorldTripping on 2009-12-12
Truecrypt cannot encrypt an entire HDD that has an OS to be run from it.

You would not be able to access the encrypted boot partition, without decrypting said partition using Truecrypt, and to use Truecrypt the machine would have to have been booted.

It does do a good job of creating 'containers' in which you can have additional nested or hidden containers. Depending on which password you enter, the appropriate container opens.

AFAIK the only way at the moment to have an encrypted HDD is to use the alternate install. You even get the opportunity to have an encrypted /home/username directory.

[caveat]
I think that I am right but I could be wrong - it has been known.
[/caveat]

For the super-secure, have an encrypted HDD, encrypt your /home dir and fill it with a Truecrypt volume.

WorldTripping

---

### Post by BkkBonanza on 2009-12-12
This is a little confusing for people. You can have encrypted volumes, just not one that you will boot into on Linux. You would need a boot partition and then mount the encrypted partition after.

---

### Post by 37fleetwood on 2009-12-15
I'm facing this right now, Truecrypt in Windows lets you encrypt the drive with the operating system while running Windows. you don't even have to let it finish encrypting, it will continue from where it left off the last time. all this while you use the computer. why can't they do this in Linux? should be simple enough, a bootloader like the Windows one that decrypts the drive and allows boot as normal. put the root partition and the swap in an extended drive partition which would be decrypted by the Truecrypt bootloader. really this is basically what the Ubuntu alternate cd does with the exception of being able to do it while the OS is running.

the best system in Windows is Drivecrypt which lets you encrypt the entire drive and for the truly paranoid, you can make a hidden clone of your Windows install in the free space of the regular encrypted install. this gives plausible deniability. if forced just give the first pass which opens the first encrypted os, and the other os is not discernible.

---

### Post by abhiroopb on 2010-01-12
So, is there a solution (with or without truecrypt?) I simply want to encrypt my HD so that if my laptop is stolen I won't have to worry.

---

### Post by BkkBonanza on 2010-01-12
Your simplest solution is using an encrypted home. Ubuntu has this as an install option and it's almost entirely transparent. If you need to add it after then you can use this tutorial,

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

While it looks complicated, it's fairly easy to follow and does work.

Encrypted home won't encrypt the whole drive but: 1. It's pretty much transparent to use regarding passwords/keys and such, so no added hassles. 2. Pretty much everything you store is in your home directory anyway and this covers all the important keys/settings etc. Anyone stealing your notebook will require your user password to see anything in your home.

You can use LUKS whole drive encryption and there is tutorials around here on that, but I believe it requires extra boot passwords etc.

---

### Post by abhiroopb on 2010-01-12
Thanks for that...it says that I should backup my home directory. I have a backup of it already (which is current to within 3 hours). Do I still need to back up my home directory?

---

### Post by BkkBonanza on 2010-01-12
Up to you. It's only in case you mess it up and need to recover it. If nothing changed since 3 hours I don't see why you need to do it again. Maybe rsync it and only changes will be copied.

---

### Post by abhiroopb on 2010-01-12
Ok thanks! Makes it feel safer!

---

