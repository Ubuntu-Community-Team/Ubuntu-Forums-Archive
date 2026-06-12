---
title: "Galago Ultra Pro screen issues"
date: 2016-10-14
forum: System76 Support
---

### Post by riseringseeker on 2016-10-14
My Galago Ultra Pro purchased 4/2015 (Order #44045) started having video issues this morning.  It will work fine for a period of time, then begin to flicker, just enough to be noticeable, irritating and troubing, then it will have vertical colored lines, blanking the screen.  Closing the lid and putting it to sleep seems to fix this temporarily, but it keeps coming back.

I am still running Ubuntu 14.04.5 LTS, with a Cinnamon DE.  (I usually wait a month or two before upgrading from one LTS to the next, and schedule etc has not let me have time to do it yet, was planning on making the upgrade this week)  Switching to another desktop environment does not change this behavior.

Best uneducated guess is it may be the video card, but please tell me what I should look for, and/or if indeed a video card is replaceable in this laptop.

---

### Post by a-emma on 2016-10-17
Hello!
I created a support case for you to address the display issue. The video card can't be replaced without replacing the motherboard since the CPU is soldered to the board and the video is embedded on the CPU. We can provide options for repair through support before the end of the day. We'll get it resolved as quickly as possible!

Cheers,
Emma Marshall
Consumer Account Manager
[email]Emma@System76.com[/email]

---

### Post by fallenshadow on 2016-11-11
Strange. I also have a Galago Ultra Pro (order #41234) and have only recently been experiencing flickering display issues.  I'm just running Ubuntu 16.04 and have been for a long time without issues. I opened a support case already - 19608. Sounds like maybe a recent Ubuntu update is causing this?

---

### Post by g33zr on 2016-11-11
I had the same problem with my new System76 Sable PC, Ubuntu 16.04 LTS pre-installed.

There are a couple of fixes:

1.) open terminal
gksudo gedit /etc/default/grub
edit line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash&#8221; 
add i915.enable_psr=0 in the quotes e,g.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_psr=0&#8221;
save
sudo update-grub
reboot

2.) $ cd /tmp
$ wget [https://01.org/sites/default/files/downloads/intelr-graphics-linux/sklgucver43.tar.bz2]("https://01.org/sites/default/files/downloads/intelr-graphics-linux/sklgucver43.tar.bz2%3Cbr%3E--2016-10-28")

3.) Upgrade to Ubuntu 16.10 :D

---

### Post by fallenshadow on 2016-11-15
I've since upgraded to 16.10 since Ubuntu 16.04 has annoying bugs that have since been resolved. All my troubles went away once I upgraded to 16.10 but its a shame because I always do try to stick to LTS but always I'm forced to upgrade to solve issues.

---

