---
title: "[SOLVED] Machine &amp;amp;amp;amp; Distro?"
date: 2008-08-27
forum: The Cafe
---

### Post by Yezinki on 2008-08-27
Hi there,

After having a a 10 day feel of Linux/Unix distros......I have a plan & would appreciate your suggestions.

1. My plan is to only install Vista on my note book dell xps 1710.

2. Linux distro on Sony Vaio VGC-LS1.


a. Sony vaio's specs are 250 GB HD, 2 GB RAM, Infrared KB & mouse, integrated Z-star Micro Corp web cam, XBrite 1600X 1200 resolution....no video card......Intel grahic accelerator......Intel 945 GM Chipset, Fuijitsi TV tuner board.

b. 250 GB is enough space for 1 distro....how would you partition it...meaning number & their sizes?

c. Which distro would you install...Ubuntu, Kbuntu, Klikit-Linux?

d. Dell with Vista I shall use primarily for video conferncing & messengers & Sony for professional work.

How do you smart people see it,

Hoping to hear all kinds of suggestions,

Regards!

---

### Post by pelle.k on 2008-08-27
First of all, do it the other way around. Dell notebooks are known for their linux compability while sonys are not. You're *going* to hit more problems with the vaio i'm afraid.
20 gigs is more than enough for a full install of ubuntu. In fact, you could probably do it in 5-10 gigs. You may however make an extra partition for "files".

make a swap at least as large as you amount of ram (for hibernating...)
a root (/) of 10 gigs
a home (/home) of say 5-10 gigs
(and optionally another partition with a mount point of your choice (i.e /media/files)

If you want to try something else than ubuntu, the i suggest kubuntu (not the remix), pardus 2008.1, mandriva 2008.1 (kde or gnome, both are on the free DVD)

That's it! Have fun.

---

### Post by Yezinki on 2008-08-27
Thanks.........whats this command for?

---

### Post by wersdaluv on 2008-08-27
> **Yezinki said:**
> Thanks.........whats this command for?
The command is his signature

---

### Post by Lord Xeb on 2008-08-27
```
nathan@nathan-laptop:~$ cat negativity > /dev/null
cat: negativity: No such file or directory
nathan@nathan-laptop:~$ pmount /dev/disk/by-label/intentions
Error: device /dev/disk/by-label/intentions does not exist
nathan@nathan-laptop:~$ sudo apt-get install good-life
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package good-life
nathan@nathan-laptop:~$ 

```

LOL

---

