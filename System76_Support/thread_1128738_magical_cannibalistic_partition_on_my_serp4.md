---
title: "magical cannibalistic partition on my serp4"
date: 2009-04-17
forum: System76 Support
---

### Post by eyecreate on 2009-04-17
I've been trying to install Kubuntu 9.04 RC onto my computer, but I don't seem to be getting anywhere fast. I am able to go through the install process fine(and I noticed the time zone bug they fixed from the beta) but as soon as I try to set things up, it starts eating itself. I don't know what triggers it for sure, but I first notice it when kpackagekit starts acting up. It may not happen the first reboot or even a few more reboots, but as soon as I'm trying to install things at some point, kpackagekit will "freeze" in the middle of doing what it was supposed to. I hit the cancel button on it and try again. It only continues to say "waiting for another process" no matter how many times you try after that. Even logging off won't change it. After you restart, though, you can never boot up again as it stops with busybox and says in recovery mode that the ext3 partition is corrupt and cannot mount. I have tried to install kubuntu many times now and have gotten frustrated. I like most of the software and set up I can do with KDE 4, but it seems there is still buggy things, most liely kpackagekit. Is this a problem of mine or a bug and how can I make it become  a herbivore?
p.s. On my serp4 I used to have ubuntu 8.10 on it and my synaptics pad scroll on the side worked. It does not in kubuntu 9.04 RC(haven't tried ubuntu 9.04 rc yet). Is thing in the system76 driver or is something else broke there too?

---

### Post by eyecreate on 2009-04-18
Hm...so far it seems that if I had updates the packages first through apt-get instead of kpackagekit, then the updates seem to be okay. Will let know if it stops being okay,

---

### Post by eyecreate on 2009-04-18
hm..i'm now getting an error i've seen before. it seems my harddrive just "disappeared". No application can see the entire drive(root and all). I'm not sure what's gona happen once I close this firefox window, so I'm posting this here. I might be back into the problem I had before, but one thing I think it seems is that I don't think it's related to kpackagekit anymore. I'm gona restart now...I hope it's just I'm paranoid it's back again and not there is a serious bug in the file management area, and I'm not even using the new ext4 system.

---

### Post by eyecreate on 2009-04-18
yep, it did it again. Here are some errors I thought were useful:

```
kinit:no resume image, doming normal boot
mount: mounting /dev/disk...on /root failed:invalid argument
mount: monting /dev on /root/dev failed: no such file or dir
target filesystem does not have /sbin/init
ext3-fs:group descriptors corrupted
no init found try passing init=bootarg
ext3_check_descriptors block bit map for group <number here> not in group <number here>
```

---

### Post by eyecreate on 2009-04-18
Seems I got a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691)
Hope it's fixed soon.

---

