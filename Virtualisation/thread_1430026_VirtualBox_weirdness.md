---
title: "VirtualBox weirdness"
date: 2010-03-14
forum: Virtualisation
---

### Post by MisterEwok on 2010-03-14
So, I've been using VirtualBox 3.0.8 that came from the Ubuntu (9.10) software manager. Today for the first time I needed to use a USB drive, so I read up a little and upgraded to version 3.1.4, the latest from the VirtualBox website. It installed well, and I made the changes for USB recommended at help.ubuntu.com/community/VirtualBox/USB. It ran my Windows XP VM that I had previously created and been using well and the USB drive worked. But, when I shut it down, it actually tried to restart, rather than shutting off. It got to the xp "welcome" screen and then flashed a split-second blue screen and then restarted again. This repeated several times, and I think it would have gone on infinitely had I not manually shut off the machine from the host window control. I was able to "pause" the screen once during the super-quick blue screen:

[IMG]http://photos-e.ak.fbcdn.net/hphotos-ak-ash1/hs471.ash1/25841_109317049084529_100000187042186_248860_3736786_n.jpg[/IMG]

I know that this doesn't have to do with the USB drive, because I restored my virtual hard drive from a backup and ran it again without using the USB drive, and it still did the same thing.

Someone please help. It's so sad that I still have to deal with windows issues.

---

### Post by mkvnmtr on 2010-03-14
When you upgraded did you remove the old OSE packages? Youn can find what is installed in synaptic with a search for virtual box. As I recall I uninstalled virtual box and the guest additions and maybe another package that was OSE virtual box related and had no trouble with the change. I did not remove any library packages just ones that said OSE Virtual Box. I did not even have to import my machines, they just were there.

---

### Post by MisterEwok on 2010-03-15
Yes, I removed two items in synaptic, because the deb for the new version told me it conflicted with the already installed one. I removed two virtualbox ose items there and then it installed and operated fine. And just like you say, my machine was just there. And it ran fine, until I shut it down.

---

### Post by MisterEwok on 2010-03-17
So, I have discovered that it does not do this weirdness when I uncheck the box "Enable IO APIC" under the system settings for my XP machine. From the note shown upon rolling over this option, it appears that this should have been enabled before I installed Windows XP on the machine. I don't know much about virtualization, so tell if I'm wrong about that. And if I'm right, tell me if there is some kind of workaround, because I was instructed at help.ubuntu.com/community/VirtualBox/USB to enable this option.

---

### Post by Ozymandias_117 on 2010-03-19
You would be correct. Enabling or disabling that on an already installed windows VM will break it. I am unaware of any workarounds.

---

### Post by bpalone on 2010-03-19
> **MisterEwok said:**
> So, I have discovered that it does not do this weirdness when I uncheck the box "Enable IO APIC" under the system settings for my XP machine. From the note shown upon rolling over this option, it appears that this should have been enabled before I installed Windows XP on the machine. I don't know much about virtualization, so tell if I'm wrong about that. And if I'm right, tell me if there is some kind of workaround, because I was instructed at help.ubuntu.com/community/VirtualBox/USB to enable this option.

Have you tried the USB with that turned off?  If it works without it, then I wouldn't worry about it.  That is, until something didn't work right later.  I don't have it activated on either 2K or XP and usb works ok.  I use a bit older version of VirtualBox, but I doubt they changed that.

---

### Post by MisterEwok on 2010-03-22
Cool. I tried it, and the usb seems to work fine without it. So, I guess it's no problem. Thanks.

---

