---
title: "Why comes Ubuntu with a recovery mode?"
date: 2012-08-01
forum: Security
---

### Post by Poeha on 2012-08-01
Is it possible to remove the recovery mode?

---

### Post by tubbygweilo on 2012-08-01
What reason do you have for removing recover mode?

Removing recovery mode may well be an action you can not recover from.

A few lines about the uses of recover mode via [Ubuntu wiki]("https://wiki.ubuntu.com/RecoveryMode")

---

### Post by na5h on 2012-08-01
Perhaps the OP is worried about the fact that recovery mode allows for any user to log in and access the file system as root...this can be avoided by setting a root password, though...

---

### Post by Grenage on 2012-08-01
And completely overridden with a boot disc/drive.

---

### Post by na5h on 2012-08-01
> **Grenage said:**
> And completely overridden with a boot disc/drive.

That's what the BIOS password is for...

---

### Post by tubbygweilo on 2012-08-01
Poeha, a couple of threads concerning root access passwords and recovery mode that have been asked in the last few weeks. 

[aks root password at failsafe boot]("http://ubuntuforums.org/showthread.php?t=2026412")

[Recovery root command-line doesn't require password?]("http://ubuntuforums.org/showthread.php?t=1933746")

The may answer some of your worries but if not then ask more questons.

Physical access trumps all other permissions.

---

### Post by dodo3773 on 2012-08-02
This?:
```

/boot/grub/grub.cfg

```

Learning how to use chroot before making these changes would probably be a good idea.

---

### Post by Poeha on 2012-08-02
> **tubbygweilo said:**
> Poeha, a couple of threads concerning root access passwords and recovery mode that have been asked in the last few weeks. 

[aks root password at failsafe boot]("http://ubuntuforums.org/showthread.php?t=2026412")

[Recovery root command-line doesn't require password?]("http://ubuntuforums.org/showthread.php?t=1933746")

The may answer some of your worries but if not then ask more questons.

Physical access trumps all other permissions.

 But what is logic behind the recovery/failsafe mode? Why is this choice/feature "defended" by refering to "Physical access is root access" arguments. I want a Linux system with restricted policies. I assume an alternate install, with a complete encrypted os is the way to go?

---

### Post by cariboo on 2012-08-02
> **Poeha said:**
> But what is logic behind the recovery/failsafe mode? Why is this choice/feature "defended" by refering to "Physical access is root access" arguments. I want a Linux system with restricted policies. I assume an alternate install, with a complete encrypted os is the way to go?

An encrypted home, is the only way to protect your personal data. If someone has physical access to your computer, they can access unencrypted data, no matter what restrictions and policies you put in place.

I've serviced and repaired computer systems for years, a password or restrictive policies has never stopped me from doing what needs to be.

---

### Post by trundlenut on 2012-08-05
> **na5h said:**
> That's what the BIOS password is for...

For at least two minutes, unless it's a laptop, in which case it would be more like 5 minutes (a few screws will need to be removed).

As mentioned encrypting your data is probably the best approach.

---

### Post by na5h on 2012-08-06
> **Poeha said:**
> But what is logic behind the recovery/failsafe mode? Why is this choice/feature "defended" by refering to "Physical access is root access" arguments. I want a Linux system with restricted policies. I assume an alternate install, with a complete encrypted os is the way to go?

You can choose to encrypt your Home folder when you install Ubuntu...it can also be done afterwards:
[http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/](http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/)

---

### Post by black veils on 2012-08-06
i was aware of the lacking privacy also. i set a bios password, and made the first bootable device the harddrive. i set the password to be asked before everything. and tested to find what key initiates my alternative boot device, for if i want to boot into something else, i can without going into the bios and changing boot order, my key is F12 but yours could be Del or F11 etc


so the only way someone could physically get in is to reset the battery inside the laptop.

---

### Post by cariboo on 2012-08-07
> **black veils said:**
> i was aware of the lacking privacy also. i set a bios password, and made the first bootable device the harddrive. i set the password to be asked before everything. and tested to find what key initiates my alternative boot device, for if i want to boot into something else, i can without going into the bios and changing boot order, my key is F12 but yours could be Del or F11 etc


so the only way someone could physically get in is to reset the battery inside the laptop.

Which as was stated earlier in the thread, is fairly easy to do, as the information is freely available to any one with an internet connection.

---

