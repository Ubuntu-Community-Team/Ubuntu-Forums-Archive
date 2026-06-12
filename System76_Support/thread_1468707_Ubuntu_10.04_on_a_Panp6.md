---
title: "Ubuntu 10.04 on a Panp6"
date: 2010-05-01
forum: System76 Support
---

### Post by |Porsche on 2010-05-01
Hello everyone,
I didn't see a post on Panp6 running Ubuntu 10.04. Here is what I am experiencing after UPGRADING from 9.10.

WiFi - No Issues.
HDMI Video - No Issues.
HDMI Audio - It works after you unmute the source via alsamixer. This behavior persists from 9.10. No issues.
_Bluetooth - Dead in the water. Nothing. Nada. It doesnt event show up on a lspci or lsusb._

I dont really use any power management functions so I dont know if they are working properly.

Share your experiences with the panp6 and Ubuntu 10.04. We should come up with a checklist so we can report on other features that we take for granted.

---

### Post by Scotty Bones on 2010-05-01
Enable the proposed repo and run an update. That fixed all the issues with the function buttons on my panp5. I can now toggle BT, wifi, camera and touch-pad. I have not tested HDMI yet. Give it try and see if it helps.

---

### Post by |Porsche on 2010-05-02
I am not sure what repo you are talking about. I have enabled the System76 repository, backports and proposed. Did an update. Downloaded the latest System76 Driver. Ran it. No luck. Bluetooth does not show up on a lspci or lsub. I forget what type of interface it has so I run both commands. Some Fn key combinations work others do not.

---

### Post by Noah0504 on 2010-05-03
> **|Porsche said:**
> I am not sure what repo you are talking about. I have enabled the System76 repository, backports and proposed. Did an update. Downloaded the latest System76 Driver. Ran it. No luck. Bluetooth does not show up on a lspci or lsub. I forget what type of interface it has so I run both commands. Some Fn key combinations work others do not.
Not sure why it's not working.  The kernel update in the proposed repo worked like a champ for me.  The only problem I have with HDMI video is having to change the resolution back and forth every time.  Not a huge problem, but it does suck.  My screen on the laptop is 1600x900... I have to change it for my 720p TV.

---

### Post by thomasaaron on 2010-05-03
Porsche, did you try pressing Fn-F12 to turn the bluetooth on after running the updates and rebooting?

---

### Post by |Porsche on 2010-05-03
Oddly enough, I didnt have a new kernel waiting for me once I enabled the repositories. I did try Fn-F12 with no success. I just did an apt-get update/upgrade and I am seeing a  new kernel. I hope this is the one.
BTW before the update my uname -a = Linux hostname 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux.

After upgrade uname -r = 2.6.32-22-generic.

This fixes all issues I had. Fn keys now work as expected. Bluetooth is back!!

**_[COLOR="Black"]Fix Action: Enable the backports and proposed repositories. apt-get update, apt-get upgrade -- ensure that there is a new kernel update on the update.[/COLOR]_**

---

