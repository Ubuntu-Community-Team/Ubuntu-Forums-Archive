---
title: "Do you have Kino working under Intrepid?"
date: 2008-11-16
forum: Ubuntu Studio
---

### Post by Rulls on 2008-11-16
I've had no luck with any of the instructions previously posted for enabling DV capture with Kino under Intrepid.  All instructive posts I've found appear to be relevant to earlier Ubuntu releases.  Some of what I've read indicates that the FireWire subsystem has been undergoing recent modification.  I don't know if my current problem is related to FireWire access or Kino itself.

I'm running Kino ver. 1.3.0 under a recent new installation of Intrepid on a Toshiba Satellite laptop with a built-in FireWire (4-pin) port.

Thanks in advance for feedback and assistance.

---

### Post by kellemes on 2008-11-17
You didn't give any details about your issue with Kino so I'm guessing it's about the same as the one I had, could'nt get capturing going..
It was fixed using the following instructions..[http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html]("http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html")

---

### Post by Rulls on 2008-11-17
Thanks for your reply, kellemes.  I've gotten past that problem (didn't change privileges for all users, but I associated the file with group "Video," and my user ID is a member of that group, per another help instruction).

Latest error conditions are as follows:

On the Kino Preferences (Edit/Preferences) panel, under the "IEEE 1394" tab, there is no entry shown in the "AV/C Device" pull-down box, and;

Error message at bottom of "Capture" screen: "No AV/C compliant cam connected or not switched on?"

I have verified connections and power-on status. I have previously been successful capturing DV from this cam in a different system environment (under OS not to be mentioned here!)  I am able to access other devices (a hard drive) using the same port.

---

### Post by kellemes on 2008-11-17
Hi Rulls,
  I'm afraid I only can search for possible answers instead of providing my own. This issue has been around for some time now and is associated with some reported bugs, as far as I understand a fix is in the pipeline.
Anyway, a couple of links you may have seen already..

Lot of info here, couple of methodes to try.. method 5 has been known to work ;-)
[https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=784385]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=784385")

[http://ubuntuforums.org/showthread.php?t=946708]("http://ubuntuforums.org/showthread.php?t=946708")

Hope it helps..

---

