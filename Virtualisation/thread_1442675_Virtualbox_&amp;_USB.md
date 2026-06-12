---
title: "Virtualbox &amp; USB"
date: 2010-03-30
forum: Virtualisation
---

### Post by asharpham on 2010-03-30
I've read quite a bit in this forum about getting the virtualbox guest os (in my case Windows XP) to recognise USB drives. There was some discussion about OSE not supporting USB but I have no idea which version I have. I got mine from the Sun site and it's v. 3.1.6 r59338. No idea if it's OSE or not.

When I click on Devices on the VB window and move the mouse down to USB devices, I get 4 items listed but greyed out. Two of the items I recognise as my USB devices.

Is there a way to "ungrey" these devices or do I have the wrong version of Virtualbox?

Alan.

---

### Post by the yawner on 2010-03-30
The OSE version is the one you get from the official repo. But as you've mentioned you installed your from the Sun's site, then USB should work just fine. If it's currently plugged in then make sure that it is *safely removed*/unmounted on your host machine.

---

### Post by mkvnmtr on 2010-03-30
You will need to install guest additions. On a xp guest once it is installed you should be offered the option to runit. Then I believe you will be able to enabel the usb support. You might need to shut down and do it under storage and then boot up.

---

### Post by arashiko28 on 2010-03-30
> **mkvnmtr said:**
> You will need to install guest additions. On a xp guest once it is installed you should be offered the option to runit. Then I believe you will be able to enabel the usb support. You might need to shut down and do it under storage and then boot up.

I have the same problem, I already installed the guest additions and added it with the virtual machine off, added my flash drive and nothing yet. Also can't get my pocket pc to be recognized by the virtual machine, which was hoping on it I installed it on the first place, I'm running W7 ultimate.

---

### Post by asharpham on 2010-03-31
Yes, I've already installed guest additions and rebooted but the USB drives are still greyed out. I'll try unmounting the USB drives before opening the virtual machine.

---

### Post by asharpham on 2010-03-31
Hey fantastic. You guys rock! Unmounting from Ubuntu was the answer. I guess remounting after finishing with windows is another matter.... unless removing and reinserting is the only way to do it. Hopefully this answers  [arashiko28]("http://ubuntuforums.org/member.php?u=324859")'s question too[URL="http://ubuntuforums.org/member.php?u=324859"].
[/URL]

---

