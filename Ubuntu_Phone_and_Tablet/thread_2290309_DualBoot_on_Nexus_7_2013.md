---
title: "DualBoot on Nexus 7 2013"
date: 2015-08-11
forum: Ubuntu Phone and Tablet
---

### Post by w2vy on 2015-08-11
I was able to get my hand on a Nexus 7 2013 and wanted to give this a try and maybe keep it available for testing.

I was following the [Wiki Steps]("https://wiki.ubuntu.com/Touch/DualBootInstallation")

I found out that SuperSU installation changed with Lollipop (5.0) so in order to get rooted I needed to stay with 4.4 KitKat
(Yes SU is operational)

That page also suggests using utopic, which is no longer on the list of the Ubuntu Dual Boot app, but it does select vivid-proposed which looks right.

I say LOOKS right because after all the install steps complete with no error and I use the app to start Ubuntu, I get the Google splash screen twice and the android is running.

It seems to me it reboots (1st Google) attempts to load, fails and then resets to reload android (2nd Google)

If I manually start the bootloader and run recovery I get the same sequence.

Is there a logfile I can inspect, assuming that the kernel started to boot?

I am going to see if I can let android update to Lollipop now that it is rooted...
No big deal, it is easy to get back to the state I am currently in :)

Tom

---

### Post by grahammechanical on 2015-08-11
That wiki page was last edited a year ago. And I also think that dual boot of Android and Ubuntu touch was a bit of a private project by Canonical engineers. I do not think that it is an up to date development. It is still classed as a tech preview.

Most Canonical development work has gone in a different direction

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/)

Regards

---

### Post by w2vy on 2015-08-11
Yes I had noticed it had not been updated in a year... I figured I would check it out anyway...

I will check out the link you provided

thanks
tom

---

### Post by w2vy on 2015-08-11
Those steps worked quite well.

Thanks
Tom

---

### Post by w2vy on 2015-08-16
I asked over on the launchpad ubuntu-phone mailing list and was pointed to the MultiROM app.

It seems to work quite well for loading many different roms as bootable via a grub like menu.

On my rooted Nexus 7 2013 the app installed from the app store with no problems.

I did find that the dev-proposed/flo version 275 (Aug 2nd) is the latest build that works.

I have posted a comment about it on the xda forum to get it fixed.

[MultiROM at xda]("http://forum.xda-developers.com/showpost.php?p=62360638&postcount=1148")

Tom

---

### Post by w2vy on 2015-08-18
And r282 works!

I am sure I had nothing to do with getting it fixed :)

---

