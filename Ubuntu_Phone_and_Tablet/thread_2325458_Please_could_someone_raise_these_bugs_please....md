---
title: "Please could someone raise these bugs please..."
date: 2016-05-22
forum: Ubuntu Phone and Tablet
---

### Post by andrew-q2 on 2016-05-22
hi, please could someone log the items below as bugs / observations for Ubuntu Touch.  I know this seems lazy but I really don't have the time for the learning curve and associated admin to get into this.  I'm sure someone who is already set up and knows the ropes can do this easily.

1. TOUCH is turning on GPS shortly after booting up.  See [http://ubuntuforums.org/showthread.php?t=2324695](http://ubuntuforums.org/showthread.php?t=2324695)
I believe it should not be turned on if you have previously turned it off in Battery properties.

2. In Security and privacy \ Location, I see various apps listed, but there is one entry with no app shown.  Surely there should not be such an entry.  What does this blank entry refer to please?  (MX4, OTA 10.1)

3. I have no Cut The Rope Free app, perhaps I uninstalled it, I don't want it. But 31Mb is still reported to this app.  Should a future OTA include a Clean-Up to get rid of stuff like this.  I also have 153Mb for Document Viewer, but only one doc at 53Kb.  And 59Mb for File manager.  Note there is 495Mb "used by apps", purple colour, so I'm assuming the previous figures are not simply the space needed for the executables.

4. Sending an email from my Microsoft outlook.com address using WiFi fails.  The progress bar hangs at 10% then eventually times out saying "Sending Failed    Connection timed out".
It works ok using mobile data or if sending from an ordinary email address.

5. I videoed some important music today but there is no sound, not only when played on the phone but also on my desktop.  Other video not from the phone is working ok.  I don't use the video often.  Ok I should have checked everything was working first, but I'm disappointed with the phone.  Have I got a setting wrong? - there's an icon quite like a hot air balloon, I've tried recording at both Yes and No but no sound either way.  This is an example of minimalist design that doesn't work - it doesn't say what this icon means, poor.

6. If you have the rear camera on the best setting (4:3) and switch to the front cam, then back to the rear, it's now on 5:3 (poorer setting).  I think it should be 4:3.

---

### Post by andrew-q2 on 2016-05-22
All the items in my previous post are for OTA 10.1.  The email one refers to Dekko 0.6.20.  I can't see what version the Camera app is, but there are no updates pending as of today.
--------------------

---

### Post by donquichot2016 on 2016-05-22
2. Did you install & uninstall any additional applications that require location permissions? It seems someone just filed a bug report for this: [1584547]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-system-settings/+bug/1584547").

4. I found this bug with the same problem, except it happens on the mobile network instead of wifi: [1547065]("https://bugs.launchpad.net/dekko/+bug/1547065") .  Was the Wifi connection strong or weak?

---

### Post by andrew-q2 on 2016-05-23
donquichot,  I have tried various apps, so this is probably the bug you kindly identified above.
Regarding (4) and Dekko, I'm pretty confident it's WiFi that's the problem in my case.  Can anyone else with an Outlook.com email address they're using on MX4 try this please?  The WiFi is at home, it's a strong signal, and there are no problems I'm aware of with the WiFi, and it gets quite a lot of use across various devices.

---

### Post by QIII on 2016-05-23
Hello!

While we are happy to help you sort out issues as we can, the Ubuntu Forums are not part of the mechanism for bug reporting.

We are users like you, not Ubuntu developers or employees of Canonical.

Launchpad is the appropriate place to raise bugs.

---

