---
title: "how to secure grub 2.0 ?"
date: 2010-03-11
forum: Security
---

### Post by S.Mohamed on 2010-03-11
please, how can i secure grub 2.0 ????
with grub 1 just do : grub-md5-crypt
then we write password --md5 <crypted_password> in /boot/grub/menu.lst

thinks for your help !

---

### Post by gnupipe on 2010-03-11
Grub2 supports only plaintext passwords. :)

---

### Post by S.Mohamed on 2010-03-12
thanks for the information, i didn't know it, but even with plaitext passwords, how to secure it?

---

### Post by bodhi.zazen on 2010-03-12
> **S.Mohamed said:**
> thanks for the information, i didn't know it, but even with plaitext passwords, how to secure it?

IMO things such as a BIOS password and grub password add very little to security. If somebody has physical access they are easily defeated.

They can slow someone down a bit, but, IMO, at the end of the day you need to restrict physical access.

---

### Post by BigSteve_G on 2010-03-23
Well I'm surprised! - got my Linux Mint 8 (based on Ubuntu 9.10) system all up & running locked down user folders / files stuff like that & read all over the Internet about how Linux in general is so secure - imagine my surprise when I find out that with just a tiny a bit of info gathered on-line I was able to hack my system giving me access to EVERY single file & folder without being asked for a single password! - and with the aid of a grub2 feature at that.

So what I now need is a way to stop users from bringing up the grub menu then being able to use [e] to edit the boot line things.

---

### Post by Arand on 2010-03-23
I'll just blatantly quote myself here:

> **Arand said:**
> If you have the "boot a liveCD/USB/PXEboot" issue out of the way, and you don't want to have a BIOS password on each boot (one solution), then the next step would be to password-protect grub, in grub-legacy this is fairly simple: 
[http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

In grub2 it is trickier (but doable of course):
[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

This will limit certain entries in the menu to only be bootable if a password are provided, which I'm guessing is kind of what you are looking for.

Also disabling manual editing of grub entries will be required for lockdown.

Of course, anyone with access to the sudo password will be able to circumvent easily.

If they don't have the sudo or grub passwords, then the lock in should be acceptable.

- Arand

It's the old issue of physical access:
GNU/Linux is secure from Eve The Hacker, but not from Bob The Kid Brother

- Arand

---

### Post by BigSteve_G on 2010-03-23
Beats me how in the world of Linux security features (like legacy grub's password protect feature) get dropped like this & newer versions of something dont seem as good as older ones

---

### Post by mathgeek2000 on 2010-03-24
> **BigSteve_G said:**
> Beats me how in the world of Linux security features (like legacy grub's password protect feature) get dropped like this & newer versions of something don't seem as good as older ones

After upgrading to Ubuntu 9.10, from 8.04? Grub 1.x was replaced by Grub 2. I found since I'm only running Ubuntu on this Laptop, Grub 1 is sufficient, and superior over lilo.
Fortunately, I found a guide to remove Grub2, and install Grub1.
 
Security Features to consider are:
  - BIOS startup password, & different BIOS setup password.
  - MD5 encrypted Grub password for editing grub menu entries.
  - use lock or specific pwd for some entries in grub, like 'single' for root access.

Personally, I also encrypt my home folder, as well.
I'm toying with using an encrypted LVM, but it makes backups harder.

---

### Post by BigSteve_G on 2010-03-25
If it helps I've found a way to secure things by stopping anyone even accessing the grub menu (only catch is (apart from NO-ONE can access the menu) its no good on a dual/multi boot setup)
 
[http://forums.linuxmint.com/viewtopic.php?f=46&t=44706](http://forums.linuxmint.com/viewtopic.php?f=46&t=44706)

"I tried a more simpler method of setting all the background, text & highlight colors to black & that half worked but the background meant the text could still (arkwardly) be seen, then I noticed towards the bottom of the grub.cfg file a conditinal statement (IF) which seem to basicaly be saying if the SHIFT key is pressed set the timeout to -1 (show the menu) or if not (ELSE) set it to 0 (just boot) so I change the SHIFT to g expecting to have to use the 'g' key to get the menu but instead it just stops anyone bringing up the menu regardless of what key is press."
 
I'm using a XP machine at work at the moment so cant post the exact text but if anyone needs things explaining a bit better I'd be happy to post instructions here.

---

### Post by augustsalbert on 2010-03-25
You must secure your password for that when you purchase a router or modem, the first thing you should do is run the install wizard (most do) and change the default login/passwords. Otherwise, you're likely to get into a situation where some piece of malware can either change your routing from either internal or external.

---

