---
title: "I need to reinstall?"
date: 2009-01-30
forum: The Cafe
---

### Post by uberdonkey5 on 2009-01-30
When 9.04 (Jaunty) comes out, there is NO WAY I am gonna miss using the ext4 file system. However I presume that if I use ext4 I have to reinstall?

Problem is, I am really not sure what to do. I currently have dual boot vista/hardy. I am currently upgrading to intrepid. Thing is, I'm gonna install xp instead of vista. I was going to do it through virutalbox, but had problems getting the screen full size, so I now have fears that pinnacle video editing (only software I use in windows) won't work properly or I'll have other probs in virtual box.

Basically I LOVE my current ubuntu set up (its pretty customised), but want ext4 and to get rid of vista. My mind is a tangled mess of what to do. I mean, can I make a custom live disk and reinstall my preferences from that if I have to reinstall everything...?

Damn! You lot must have had the same problems with distro hopping etc, any advice, and any of you had similar distro confusion???

---

### Post by quinnten83 on 2009-01-30
I have to install 8.10 over my current 8.04. I want to triple boot between Xp, ubuntu en opensuse. I don't have a live cd for Opensuse and i don't quite trust the installation when trying for a triple boot. XP needs to remain untouched. And you thought you had problems :(

---

### Post by uberdonkey5 on 2009-01-30
he he, I wouldn't know where to start! One thing though, intrepid seems to have a create USB startup disk function (using CD or disk image). Seems pretty groovey. Somewhere in ubuntu forums are instructions for creating your own customised live disk based on the the configuration of your computer. So potentially you could update to intrepid, then copy this image to usb. Upgrade I just did to intrepid allowed me to keep my customised files (e.g. I speeded up the boot up by removing splash screen etc, and use different printer drivers). Only problem is, it wiped off Skype!

---

### Post by billgoldberg on 2009-01-30
> **uberdonkey5 said:**
> When 9.04 (Jaunty) comes out, there is NO WAY I am gonna miss using the ext4 file system. However I presume that if I use ext4 I have to reinstall?

Problem is, I am really not sure what to do. I currently have dual boot vista/hardy. I am currently upgrading to intrepid. Thing is, I'm gonna install xp instead of vista. I was going to do it through virutalbox, but had problems getting the screen full size, so I now have fears that pinnacle video editing (only software I use in windows) won't work properly or I'll have other probs in virtual box.

Basically I LOVE my current ubuntu set up (its pretty customised), but want ext4 and to get rid of vista. My mind is a tangled mess of what to do. I mean, can I make a custom live disk and reinstall my preferences from that if I have to reinstall everything...?

Damn! You lot must have had the same problems with distro hopping etc, any advice, and any of you had similar distro confusion???

Using a video editor in a VM isn't really useful. Things will be sloooowwww.

Yes a reinstall will be neccesary.

---

### Post by FuturePilot on 2009-01-30
No you can convert existing Ext3 partitions to Ext4. There is no need for a reinstall.
See here [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4")

---

### Post by binbash on 2009-01-30
> **FuturePilot said:**
> No you can convert existing Ext3 partitions to Ext4. There is no need for a reinstall.
See here [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4")

NOTE: by doing so, new files will be created in extents format, but this will not convert existing files. However, they can be transparently read by Ext4.

---

### Post by FuturePilot on 2009-01-30
> **binbash said:**
> NOTE: by doing so, new files will be created in extents format, but this will not convert existing files. However, they can be transparently read by Ext4.

That is true, but from what I hear, when the defragmenting tool gets added to Ext4 it will allow you to convert existing files to extents.

---

