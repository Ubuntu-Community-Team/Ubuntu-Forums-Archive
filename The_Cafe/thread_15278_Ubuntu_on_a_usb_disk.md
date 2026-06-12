---
title: "Ubuntu on a usb disk"
date: 2005-02-13
forum: The Cafe
---

### Post by rosslaird on 2005-02-13
You may have seen the recent article in Linux mag about this. It's becoming more popular to put a distro on a usb flash drive. But I have tried both FlashLinux and Debian without success. On my 512M quite a bit of Ubuntu would fit.
Such an option would add even more to the appeal of Ubuntu.

Ross

---

### Post by BWF89 on 2005-02-13
That would be cool. Especially since I have a 1GB flash drive.

---

### Post by darkoptix on 2005-02-14
When I was installing ubuntu with my usb key plugged in it asked if i would like to install on it. I would try but its only 256 megs. I think you would need a bios thats boots from usb, or a bootdisk of some sort.

---

### Post by maddox on 2005-03-28
you could try SLAX instead, its supposed to fit in 256 megs 
check this article  [http://arstechnica.com/columns/linux/linux-20041109.ars](http://arstechnica.com/columns/linux/linux-20041109.ars)

---

### Post by somuchfortheafter on 2005-03-28
well i suggest removing gnome in favor of a smaller window manager, lets face it gnome eats ram and is a big big file. so use fluxbox, you could probably use midnight commander for most file browsing needs and fire fox. that should decrease it enough to fit on a flash drive... but then you have to figure out a way to make it install only those apps which would mean remastering the installer disk.

---

### Post by jdong on 2005-03-28
You do realize that a flash drive only withstands a couple of thousand of read/write's, and that's easily reached within one 24-hour Linux session, especially with /var/* , correct?

Get a LiveCD that fits on USB, like Puppy, which correctly expand the variable components into RAM. Otherwise, you're gonna destroy that USB stick within a few days of use!!

---

### Post by garyng on 2005-03-28
[QUOTE=jdong]You do realize that a flash drive only withstands a couple of thousand of read/write's, and that's easily reached within one 24-hour Linux session, especially with /var/* , correct?

Get a LiveCD that fits on USB, like Puppy, which correctly expand the variable components into RAM. Otherwise, you're gonna destroy that USB stick within a few days of use!![/QUOTE]

I don't see why not if the USB flash is used as a RO media as if it is just a CD/DVD(loop mount on squashfs for example). Ubuntu does have live CD(and rumoured to be with unionfs as well in hoary). Just union mount /var, /etc, /tmp and /home to tmpfs and it is done. This unionfs thing is very promising in that one doesn't need to have specially constructed root fs(as in KNOPPIX and many other live CD distro), just mount it at an early init script. I did this briefly using translucency fs and can put a standard debian woody setup(no change to the file system layout) on RO media(well USB flash formatted as FAT with one large file used as loopback fs). Can even ap-get install if I use another loopback file instead of tmpfs(which lose the setup on each boot).

Even without unionfs, the selective /var/log etc. can be tarballed and expanded to tmpfs on each boot to achieve the same effect.

BTW, kdebase provides a minimal environment(comparing with GNOME) which includes konqueror that meets the basic GUI needs(file/web browser). I was able to sequence that within a 256M flash disk(using cloop back then).

---

### Post by jdong on 2005-03-28
Yeah, I was hinting at a unionfs/tmpfs setup with the highly-volatile areas (/tmp, /var). Not saying it's not possible -- in fact, it's very possible to get such a setup. Just wanted to warn you guys before accidentally ruining the considerably-priced media in question!

---

### Post by jerome bettis on 2005-03-28
does anybody know why i can't boot from my usb hard drive?  it is supported in bios (the usb is first priority too), i've tried installing a few different distros and windoze, and both lilo and grub.  but for some reason it just refuses to boot from the usb drive.  any ideas what i'm missing or doing wrong?

---

### Post by garyng on 2005-03-28
too vague, at least tell us what error you see.

---

### Post by jerome bettis on 2005-03-28
no errors, it just loads the grub i have on the local hard drive and misses the usb disk completely.  but it shouldn't .....

---

### Post by garyng on 2005-03-28
chances are only one of your USB port is bootable and you may have used the wrong one. Other than that, it is hardware specific.

---

