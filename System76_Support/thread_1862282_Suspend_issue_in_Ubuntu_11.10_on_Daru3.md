---
title: "Suspend issue in Ubuntu 11.10 on Daru3"
date: 2011-10-16
forum: System76 Support
---

### Post by Temposs on 2011-10-16
I have successfully installed Ubuntu 11.10 on my Darter Ultra(daru3), used the system76 driver to restore the machine to factory settings, and everything is looking good except that suspend is almost entirely non-functional.

The only case in which suspend will work is if I choose "Suspend" from the system menu. However, I cannot resume the system by pressing the power button as is expected. I have to manually power down at that point by holding the power button for 5 seconds. 

Also, the usual action of closing the laptop lid does not initiate suspend at all. My "Power" settings are set to suspend on closing the laptop lid.

Suspend worked perfectly in Ubuntu 11.04.

I will be available to provide any further information to resolve this issue. Thanks so much :-)

---

### Post by ranjan_mg on 2011-10-16
I have the exact same issue on System 76 pangolin 6 laptop. Closing the lid just turns the screen blank. Does not suspend at all with the options correctly set. I can suspend from the system menu and wake up from the function keys but not the power button. Anyone seen this issue able to resolve it ? I have a feeling it is is not gnome/kde issue as I have the same problem on kubuntu 11.10 and ubuntu 11.10. Works perfectly on 11.04.

---

### Post by dfarrell07 on 2011-10-17
I have a similar issue. On a Lenovo W520, I can suspend fine (via laptop lid or GUI), but I cannot wake up from suspend. I get a black (but powered-on) screen, and sometimes I can see and even move my mouse around. I did not have this issue in 11.04, only after upgrade to 11.10. So far, I haven't found any solution, or found a bug report about the issue. Still searching..

---

### Post by aaronr4 on 2011-10-17
I had the same problem with my Pangolin 6 (Panp6).  Found that to resume I had to use Fn+F4 (my little moon key).  That wakes the laptop up.  It used to wake by opening the lid.

---

### Post by Nortrom on 2011-10-18
I also have the same problem on my Acer Aspire.

---

### Post by birdsarah on 2011-10-18
Hi,

I have a Gazello Pro (GAZP6).

Suspend seems to work fine - I close the lid and it suspends. 

However, waking up is a problem. I open the lid, it takes maybe 20-30 seconds to get the password prompt, where it used to take 2-5.

Cheers,

Bird

---

### Post by ranjan_mg on 2011-10-19
Probably bug 

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834)

---

### Post by birdsarah on 2011-10-19
It's now up to 1.5-2 minutes to resume from sleep. Thanks for bug link ranjan_mg however that is not what is going on with my system. I can suspend and resume, but something has happened to make it take forever to resume.

---

### Post by isantop on 2011-10-20
I think the rest of the people in this thread are affected by that bug. 

@birdsarah: Can you try running through the System76 Driver again? That could be causing your issues.

---

### Post by birdsarah on 2011-10-21
Hi,

I have latest version of system76 driver - 2.7.0 installed. I have done "Install Drivers" and "Restore System" and rebooted.

My problem remains - I am waiting a long-time for resume from suspend.

Any other useful information I can provide?

Cheers,

Bird

---

### Post by birdsarah on 2011-10-23
Hi,

By using Fn+F4 as per here [http://ubuntuforums.org/showthread.php?t=1863555](http://ubuntuforums.org/showthread.php?t=1863555) it works again.

Thanks!

---

### Post by Arioch on 2011-10-26
+1 here.

Suspend issue confirmed in Gazelle after successful upgrade.
Reinstalled Sys76 drivers and nothing changes. When I close laptop lid the system suspends, when i open again it stays black, sometimes mouse pointer shows up.

I have to suspend again with Fn + F4 and weak up with same key combo to make it work...not very elegant and annoying.

Any solution?

Thank you

---

