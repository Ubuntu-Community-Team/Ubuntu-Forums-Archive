---
title: "i need help! When I login it's only a wallpaper I get!"
date: 2013-07-02
forum: Ubuntu Development Version
---

### Post by computawhizze39 on 2013-07-02
[ATTACH=CONFIG]244324[/ATTACH]
This is all i get when I login! is there a chance this is fixable or do i need to do a complete re-install

---

### Post by dino99 on 2013-07-02
that screenshot is showing a graphic driver installation issue; how have you installed ubuntu ? which card/chipset is it ?

---

### Post by zika on 2013-07-02
> **computawhizze39 said:**
> [ATTACH=CONFIG]244324[/ATTACH]
This is all i get when I login! is there a chance this is fixable or do i need to do a complete re-installIs this 13.10 or...?

---

### Post by jerrylamos on 2013-07-02
I was fooling around with fglrx (if I've spelled that right) I think it's an ati Radeon driver from synaptic on saucy 13.04 i386 last night and wound up with just my own wallpaper.  I could do a Ctrl-Alt-t and get a terminal session and run command line, but no panels or launchers.  Well, I'm pretty used to doing installs since I'm usually on unstable U+1 so it's time to clean things up with a fresh install.  I've already got a 13.10.0-1 i386 running in another partition, I was just experimenting with 13.04.  There's also a 12.04.2 and a 10.10 on the pc on some partition or drive or another.

I've got my customization in an exec.  I do a zsync to get the latest .iso, boot it directly from the hard drive, turn off the blasted screen lock, copy in my home files including firefox bookmarks, set wallpaper, and run an exec.  Sets up samba for home network, updates, gparted, the whole nine yards. Reboot and I'm off and running.  Oh, yes, google chrome beta.  I run both browsers depending on what I'm doing.

---

### Post by grahammechanical on 2013-07-02
That is not one of the default Ubuntu Saucy Wallpapers. You have just proved that Saucy is not yet ready for that wallpaper. I see nothing wrong with installing the development version and testing to see if we can set it up the way we like it. I do that all the time. But we need a way out when things break badly. You have two options as I see it:

1) Remove that wallpaper. For that you need to get to the System Settings. Try right clicking the desktop and selecting Change Desktop Background. Or you could learn more through practical experience about fixing things through Recovery Mode>Root.

2) Re-install. It is simple and easy.

If you are not ready to learn more about fixing things in Ubuntu, then re-install. There is no shame in that. I have done it many times.

Regards.

---

### Post by jerrylamos on 2013-07-03
On 13.04 I just tried fglrx graphics driver for radeon from synaptic. Messy however I did or didn't do it.  Removed it, then just got wallpaper.  Ctrl-Alt-t got a terminal session so I could do most anything, firefox, videos, etc. but no way to get the panels back for useful things like settings.

Stopped fiddling around and re-installed.  Working just the way 13.04 is supposed to.

---

