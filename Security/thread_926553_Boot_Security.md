---
title: "Boot Security"
date: 2008-09-22
forum: Security
---

### Post by Drezard on 2008-09-22
Instead of posting one of those "I got hacked!" posts. Im wondering what are some pratical ways of protecting grub and boot security. 

The only two things I could find, was add a bios password (which you can curcumvent using default passwords) and disable cd booting. And the other thing being add a Grub password which you can supposedly boot into a live cd and read the grub password. 

So what are some boot security measures I should take?

Daniel

---

### Post by jerome1232 on 2008-09-22
Honestly there's not much you can do, here are a couple things (most of which you just mentioned)

You can put a password on bios setup, so that in order to change any bios settings a password has to be entered.

You can then configure your bios to only boot from the Hard Disk, this solves the issue of booting live cd's and doing unwanted things.

You can Password protect Grub so that no one can just boot into recovery mode and get a root shell.

Problems with this is anyone with physical access can open the box up and flash cmos, this will remove the password lock on bios so they now can get cd booting working.

Fully encrypting the disk won't stop them from seeing the grub password if they do boot into a live cd because /boot has to remain unencrypted and I'm guessing that's where the password is stored.

Buy a sturdy case and put a good lock on the opening to prevent it from being opened to stop someone from flashing cmos?

edit: You can put a password on Grub that cannot be seen, it accepts them encrypted

```

###### the entry in menu.lst for passwords
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
```

so if you put it in a form of password --md5 
you can have a password that cannot be viewed
A how to on setting grub up with the encrypted password
[http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

---

### Post by jerome1232 on 2008-09-22
Edit I went over that guide and it kinda sucks, there are better ways to edit the menu.lst, here is what the relevant sections look like for me. This password protects editing the boot line, booting into recovery mode, and booting into old kernels.

```
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password --md5 $1$fe5jh$/X7d3RoY9.lG/fzq4QIm1/
```

```
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true
```

```
## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=true
```

---

### Post by Dr Small on 2008-09-22
If there is physical access, there is no security, unless you fully encrypt your drive.

---

### Post by jerome1232 on 2008-09-22
> **Dr Small said:**
> If there is physical access, there is no security, unless you fully encrypt your drive.

agreed, and upon think that would actually prevent them from doing much by booting into recovery mode as mr. attacker must still enter the passphrase to decrypt the disk.

I Still think it's a good idea to lock grub up a bit with a password though.

---

### Post by Dr Small on 2008-09-22
> **jerome1232 said:**
> agreed, and upon think that would actually prevent them from doing much by booting into recovery mode as mr. attacker must still enter the passphrase to decrypt the disk.

I Still think it's a good idea to lock grub up a bit with a password though.
Oh sure. I can think of numerous things that would slow an attacker down such as:

Set a BIOS password
Set a GRUB password
Set the BIOS to boot from HardDrive
Remove the CDROM drive
Place a lock on the case
Encrypt the hard drive

But all can be circumvented except for the encryption. The rest just slows the attacker down, unless it is the Feds busting down your door and confiscating your case.

---

### Post by hyper_ch on 2008-09-22
who are you afraid of? physical access or remote access?

---

