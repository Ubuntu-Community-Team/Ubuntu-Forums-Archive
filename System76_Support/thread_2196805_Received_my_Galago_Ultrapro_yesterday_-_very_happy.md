---
title: "Received my Galago Ultrapro yesterday - very happy"
date: 2013-12-31
forum: System76 Support
---

### Post by porcini_m.2 on 2013-12-31
Not a support thread, just a testimonial.

<tl;dr: Nice machine, tricky trackpad, interesting ubuntu re-installation & upgrade>

I got my Galago Ultrapro yesterday, and I'm very happy - it is sharp looking, and the build quality is very good. After years of choosing laptops by minimizing cost at a certain spec level & getting crappy build quality like flimsy keyboards, etc, it's nice to finally invest in a quality machine. The keyboard on the Galago is solid & the keys have a nice feel, with the right amount of resistance & a nice surface texture.

The only downside is the trackpad is a bit temperamental - there are no buttons, so the trackpad is like a floating platter that you press (similar to the macbook pro). It can be tricky to right-click, as it tends to select when you let the right-click go, so I've had to hold the right-click down & then select with my other finger. "Tap to click" comes disabled with system76's default settings, and with good reason as the surface seems not quite sensitive enough for it to work well. Te slight tilt to the platter when you left-click can cause your finger to slip slightly, which makes the mouse pointer move a bit with the click.

Since I had a Samsung EVO SSD I already bought separately, I ordered the Galago with an Intel 240GB mSATA SSD, and left the full-size drive bay empty to install the EVO myself. There's no easy-access door for the drive bay, so I had to remove the back cover which involved about 16 screws. Here's a pic:

[IMG]http://sporkforge.com/img/system76_galago_opened.jpg[/IMG]

The drive fit in nicely & was detected fine.

I planned to format the two drives with btrfs, with / mounted to the mSATA and /home mounted to the EVO, however the installation dialog that came up was limited, and only allowed setting the basics like username, password, timezone, etc, but didn't give me the disk installation part. So to get this the way I wanted, I had to do a full ubuntu re-install.

The reinstall did not do smootly, as the installer had trouble reformatting the disks for some reason - it kept saying that they couldn't be formatted, and when I tried it from the command line in the live session, it said they were "busy". Eventually, after trying it several times, the live session wouldn't start at all - it would just drop to an "(initramfs)" text prompt or something. After googling the problem, I fixed it by booting from a different liveCD, and zeroing out both disks using dd:

dd if=/dev/zero of=/dev/sda
dd if=/dev/zero of=/dev/sdb

and ctrl-C'ing after about 20 seconds after each. Afterwords the next installation attempt went fine. I then installed the system76 drivers using the PPA as instructed on their website.

So all along I wished ubuntu 14.04 LTS was already out, as I wanted to be on the LTS release & not go through future upgrades, so feeeling adventurous I went ahead & upgraded to the 14.04 development build:

sudo do-release-upgrade -d

Luckily, the upgrade went smoothly, and the system76 mods remained intact.
Everything seems fine under 14.04, with only one crash experiends when printing a test page to the printer (not a system crash, just a crash notifier for something).

So now I have a very nice machine with the latest LTS installed - smooth road ahead. :)

FYI: this machine has 16Gb RAM, which is 1000 times the amount of RAM my IBM thinkpad of 17 years ago had.

---

