---
title: "Meizu Pro 5 Ubuntu Phone Problem"
date: 2016-05-21
forum: Ubuntu Phone and Tablet
---

### Post by Arakhkia on 2016-05-21
Hello,

I have a problem with my Ubuntu phone Meizu pro 5, when I'm turning it on, the
screen "Meizu powered by Ubuntu" is appearing but nothing is happening after.
How can I reinstall my Ubuntu phone ?

Thanks in advance to everyone for help.

---

### Post by howefield on 2016-05-21
Have you tried doing a hard reset by pressing and holding the power button and then the volume up & down simultaneously ?

---

### Post by Arakhkia on 2016-05-21
First, thank you so much for your reply !

Yes I tried, but nothing has changed.

---

### Post by termajik on 2016-05-23
Hi

I have a meizu Pro 5 so. Received 2 days ago.
I tried to install some packages and my phone didn't reboot.
After screen "Meizu powered by Ubuntu" I had a black screen.
Hard reset didn't work for me.
For repear my phone I did (In console via ssh, but should be possible with adb shell)
apt-get update
apt-get dist-upgrade.
After reboot IHM come back.

---

### Post by howefield on 2016-05-23
> **Arakhkia said:**
> First, thank you so much for your reply !

Yes I tried, but nothing has changed.

Well, given the model it has to be a very new phone, have you taken it up wioth Meizu support ?

---

### Post by Arakhkia on 2016-05-23
> **termajik said:**
> Hi

I have a meizu Pro 5 so. Received 2 days ago.
I tried to install some packages and my phone didn't reboot.
After screen "Meizu powered by Ubuntu" I had a black screen.
Hard reset didn't work for me.
For repear my phone I did (In console via ssh, but should be possible with adb shell)
apt-get update
apt-get dist-upgrade.
After reboot IHM come back.

Thank you for your answer ! When I'm trying to do "sudo adb shell" I've got : "error: device not found"

> **howefield said:**
> Well, given the model it has to be a very new  phone, have you taken it up wioth Meizu support ?

Yes, I'm waiting for their answer ! :)

Here's a video of what's happening : [https://yadi.sk/i/pN4ClCfDrwBPC](https://yadi.sk/i/pN4ClCfDrwBPC)

---

