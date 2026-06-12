---
title: "Boot logging won't enable with Fiesty"
date: 2007-06-19
forum: Sun Sparc Users
---

### Post by sandpiper on 2007-06-19
Hi I am running an Ultra 2 workstation with Fiesty. Successlly installed with gdm running ok except for the classic "failed to initialise HAL" message.

 I am trying to narrow down the reason for this  by attempting to diagnose the error messages that I see during the boot process  between when dmesg,kernel logging ends and runlevel 2 services are all invoked including gdm.  I have commented out in silo.conf the "no splash" line to enable the display of the messages.
 
I have searched the forums, installed BUM, changed bootlogd priority spent many hours  but still boot log is not changed. Can someone take me through the basic steps to enable boot logging please. Alernatively is there another way to capture these boot messages so that I can review later.. appreciate any help  Chris

---

### Post by sandpiper on 2007-06-20
> **sandpiper said:**
>  
I have searched the forums, installed BUM, changed bootlogd priority spent many hours  but still boot log is not changed. Can someone take me through the basic steps to enable boot logging please. Alernatively is there another way to capture these boot messages so that I can review later.. appreciate any help  Chris

Well I have since learnt from further reading of the forums that bootlogd has been superceded by logd  but there remains a bug in logd See: [https://bugs.launchpad.net/upstart/+bug/98955](https://bugs.launchpad.net/upstart/+bug/98955)
So in the meantime until the experts have the time to fix the bug is there any alternative technique that I can use to save the console boot messages? These messages are post dmesg and kernel messages and refer to the services that are run at boot time.  Very keen to receive advice on this if someone can spare the time to educate a newbie. Thanks Chris

---

### Post by BioTeX on 2007-08-01
You can have a look at the last few boot messages by pressing CTRL-ALT-F8 from the desktop.

---

### Post by database_dan on 2007-09-16
I had that error message as well once...and was able to fix by turning on the DBUS service...
[http://ubuntuforums.org/showthread.php?t=476281](http://ubuntuforums.org/showthread.php?t=476281)

---

