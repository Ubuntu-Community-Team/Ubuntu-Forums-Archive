---
title: "Recovering data from crashed server"
date: 2009-12-09
forum: Server Platforms
---

### Post by Vegan on 2009-12-09
My server died in a litany of errors.

I installed Ubuntu on another disk in the junk box. The file server disk was intact so I was able to share the disk again, and move the files away.

The problem is the boot disk is still messy.

Can I recover my /var /home and /usr directories easily or is everything toast?

---

### Post by munky99999 on 2009-12-09
Depends what happened. Can you mount the drive? What are the errors? Was the drive smoking or redhot? Did you spill coffee on it? Did zeus mess up your day and toss a lightning bolt into the drive?

If you can mount the drive. Even read-only. You should be able to simply copy the files you wish to salvage over. Though just copying over apps might be a bad idea due to potential for corruption or what have you.

---

### Post by Vegan on 2009-12-09
I am able to boot the disk, but the /usr is not present and causes the OS to fail and starts a recovery shell.

The disk seems to be fine, surface testing with WD's tools showed no errors.

---

### Post by holastickboy on 2009-12-09
what about placing it in a caddy, and plugging it in via usb?

---

### Post by Vegan on 2009-12-09
I am installing Linux on a new disk, that is larger than the crashed one. I am updating it and plan to slave the disk when the updates are finished.

I was wondering, can still use telnet with the desktop installed?

---

### Post by whoop on 2009-12-09
> **Vegan said:**
> I am installing Linux on a new disk, that is larger than the crashed one. I am updating it and plan to slave the disk when the updates are finished.

I was wondering, can still use telnet with the desktop installed?

Well, if the server just crashed, it just crashed :D but if it was hard-disk failure I would suggest to do as little as possible. Everything you do has the potential to make it worse.

I would only touch the drive when actually trying to recover data from it, if it is broken that is...

---

### Post by Vegan on 2009-12-09
The disk seems OK when I ran a SMART diagnostic. I am replacing the disk but I wanted to recover files if possible.

---

### Post by whoop on 2009-12-09
> **Vegan said:**
> The disk seems OK when I ran a SMART diagnostic. I am replacing the disk but I wanted to recover files if possible.

You can try recovering data with a livecd, storing the data somewhere temporarily, then you don't even have to replace the drive.

---

### Post by Vegan on 2009-12-09
The old disk is now /dev/sdb but it appears that initrd.img is damaged. Guess that means everything is history? :(

---

### Post by whoop on 2009-12-09
> **Vegan said:**
> The old disk is now /dev/sdb but it appears that initrd.img is damaged. Guess that means everything is history? :(

hhmm, there should be some way to recreate that, never done that before.
Maybe if you chroot and reinstall your last working kernel. I think upgrading a kernel builds an initrd.img. So maybe reinstalling the kernel will also do that?

---

### Post by Vegan on 2009-12-09
I tried that, no luck. I am now abandoning the hope of recovery. I am now compelled to find new solutions as the existing ones are inadequate. Ubuntu has failed me twice this year. Not what I want to see.

Now to get apache2 back up, so much for the next week or 3.

---

