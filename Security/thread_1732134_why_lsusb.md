---
title: "why lsusb?"
date: 2011-04-17
forum: Security
---

### Post by Docaltmed on 2011-04-17
Got hacked today. Yeah, my own fault, VNC was on. Anyway, once in, the chump fired up the terminal. Once he got the command line, the first thing that he did was run lsusb. Then I pulled the plug.

I'm curious. Why, if someone was hacking my system, would lsusb be the first thing that they do, rather than some sort of chroot or something?

---

### Post by dfreer on 2011-04-17
Hmmmm... maybe to see if a USB keyboard/mouse was detected, and the next step would be to disable them? Agreed, not really useful considering you could just pull the plug on him and fix things at your leisure.

Not sure why you think they would try to use a chroot, those are normally used to keep people out (although not what they were originally designed for). I suppose a hacker wanting to keep hidden might set up a chroot enviroment to hide all of his files from your view, but I don't know.

---

### Post by Docaltmed on 2011-04-24
I figured it out, why the hacker went immediately to lsusb.

I was sorting out my backups, and found that my backup disk was too full to hold another full backup. Which is odd, because I use an automatic purging scheme to prevent such things.

I took a look, and the files on the disk did not add up to the amount of space that was being used.

Using the disk utility, I looked at the disk, it was still a single partition. Fsck was happy, found no errors. Nonetheless, some 250 GB had gone missing.

My backup disk is connected via USB. Does it make sense that the hacker had been storing data/programs there, and had hidden it from me (is that something that chroot can do?).

Which certainly makes sense, in that the time that I caught him, the first thing he did was try to find out if and where that disk was connected.

None of this really occurred to me until after I had reformatted the disk, of course. I just thought it was another one of those generalized screwups that happen in life, fixed it and moved on. Then I put 2 and 2 together.

If my brain had been in gear, I would have tried to figure out what had been stashed there before erasing it. Oh, well.

---

### Post by The Cog on 2011-04-24
That makes a lot of sense, although of course you will never be sure. It would be interesting to know what was hidden there.

---

### Post by Dry Lips on 2011-04-24
Were you running VNC unsecured, without SSH, keys, etc?

---

### Post by josephmills on 2011-04-24
```
lsusb 
``` tells you what is in your usb ports or not in your usb ports as **ls** stands for list and **usb** stands for well usb so **ls--><--usb = list usb **

---

### Post by Docaltmed on 2011-04-24
> **Dry Lips said:**
> Were you running VNC unsecured, without SSH, keys, etc?

Yup. No-one's fault but my own. I turned it on for experimentation, then forgot to turn it off.

---

### Post by rookcifer on 2011-04-24
I really wish the Ubuntu team would just do away with VNC and not include it in the default install.

---

### Post by Rubi1200 on 2011-04-25
> **rookcifer said:**
> I really wish the Ubuntu team would just do away with VNC and not include it in the default install.
a huge +1 to that!

---

