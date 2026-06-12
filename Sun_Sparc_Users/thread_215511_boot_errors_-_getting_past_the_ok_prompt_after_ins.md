---
title: "boot errors - getting past the ok prompt after install"
date: 2006-07-14
forum: Sun Sparc Users
---

### Post by wdbreen on 2006-07-14
Gday Guys,
I have just done an intsall of ubuntu-server on a sun netra 1125.  The install went well until it rebooted for the first time.  It tried to boot and gave the error:
"The file just loaded does not appear to be executable"

Then just an ok prompt.

My OBP version is 3.29

I need some help on getting past this point.

Cheers

---

### Post by netztier on 2006-07-14
> **wdbreen said:**
> Gday Guys,
"The file just loaded does not appear to be executable"

Then just an ok prompt.

Can you boot into rescue mode from CD and then chroot (the menu proposes to do so) into your already-installed linux root partition?

Sounds like either SILO's installation went wrong or the symlinks in / or /boot for the initrd-kernel are somehow 
broken. I don't have a Sun box running permanently at home to copy& paste from. On my PC this looks somehow like this:

```
[FONT="Courier New"][SIZE="1"]marc@blaze:/$ ls -al
[...]
lrwxrwxrwx  1 root root     32 2006-06-28 18:56 initrd.img -> boot/initrd.img-2.6.15-25-server
lrwxrwxrwx  1 root root     32 2006-06-22 20:26 initrd.img.old -> boot/initrd.img-2.6.15-23-server
[...]
lrwxrwxrwx  1 root root     29 2006-06-28 18:56 vmlinuz -> boot/vmlinuz-2.6.15-25-server
lrwxrwxrwx  1 root root     29 2006-06-22 20:26 vmlinuz.old -> boot/vmlinuz-2.6.15-23-server
[...][/SIZE][/FONT]
```

Your kernel and initrd.img file names will probably be different.
In general, silo.conf refers to the symlink of **initrd.img** and will look for **vmlinuz** in the "root =" partition given in silo.conf.

Check that thes files or their symlinks exist in the places SILO will be looking for them.


kind regards

Marc

---

### Post by hw-tph on 2006-07-16
[quote="wdbreen"]"The file just loaded does not appear to be executable"[/quote]

Sounds to me as if you are using a CD image intended for another platform (like i386 or amd64). Use the [SPARC image](http://releases.ubuntu.com/6.06/ubuntu-6.06-server-sparc.iso).


Håkan

---

### Post by netztier on 2006-07-17
> **hw-tph said:**
> Sounds to me as if you are using a CD image intended for another platform (like i386 or amd64).

I had thought of that one, too. But how would he have been able to do an installation in the first place? He (or she?) claims the installation was successful...

I don't think that a CD-based installation would allow for messing the process up so badly that a kernel for a different architecture was installed. On the other hand.. no one ever knows...

To the OP:
Can you tell us what CD image you used?


regards

Marc

---

### Post by wdbreen on 2006-07-17
Thanks for your replies guys!
Not long after i attempted a *boot scsi0:0* (where the image is stored!) and it worked.  Just need to look at some of the /boot files netztier referred to or the environment variables for booting.

Yes, it was a SPARC image i used.  It was succesful, just not all the way.  Having fun learning though.

Any idea when Ubuntu may release a desktop-sparc iso so that users can grab a gnome or kde gui??

Breeny

---

### Post by netztier on 2006-07-17
> **wdbreen said:**
> Just need to look at some of the /boot files netztier referred to or the environment variables for booting.

That's another idea to check for - what file does OBP try to load when you have it **boot disk** at the **ok >** prompt

> **wdbreen said:**
>  Any idea when Ubuntu may release a desktop-sparc iso so that users can grab a gnome or kde gui?? 

Hm. I see - I'll just have to do a proper installation fromn scratch with ubuntu-sparc server. My active  setups are still based on the Dapper 6.06beta CDs. Aren't the **ubuntu-desktop**, **kubuntu-desktop** or **xubuntu-desktop** packages available for Sparc? 

I even see kernel releases for my beta-based installations - so instead of installing a server-oriented kernel, a desktop-oriented kernel might also boost things a bit (I think it's the "preemptive" flag that does the trick - back in my gentoo days that thing really helped). 

kind regards

Marc

---

