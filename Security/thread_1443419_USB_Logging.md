---
title: "USB Logging??"
date: 2010-03-31
forum: Security
---

### Post by Fu22y_Lojik on 2010-03-31
Gents,

I help maintain a community Ubuntu computer overseas for the military. This computer is what we call UNCLASS in that it is for personal use only, and not work related. When a member connects a USB drive to the device and doesn't unmount the drive it often leaves the desktop path to it. In this way you can sometimes see the type of drive that was used on it last. Of concern is the presence of one such link to a drive that should not be used on UNLCASS systems. The name of the drive indicates it is a work (higher security closed network only) USB device. Which brings me to my question, is there any identifying information (ie. Some sort of ID) that is logged by Ubuntu that would identify the exact USB device that was used on the Ubuntu computer? 

Regards,

Shawn

---

### Post by iponeverything on 2010-03-31
> **Fu22y_Lojik said:**
> Gents,

I help maintain a community Ubuntu computer overseas for the military. This computer is what we call UNCLASS in that it is for personal use only, and not work related. When a member connects a USB drive to the device and doesn't unmount the drive it often leaves the desktop path to it. In this way you can sometimes see the type of drive that was used on it last. Of concern is the presence of one such link to a drive that should not be used on UNLCASS systems. The name of the drive indicates it is a work (higher security closed network only) USB device. Which brings me to my question, is there any identifying information (ie. Some sort of ID) that is logged by Ubuntu that would identify the exact USB device that was used on the Ubuntu computer? 

Regards,

Shawn

For this particular incident, I think that you are out of luck. For future cases though it would be fairly trivial to add some type of wrapper that would log information that would assist in the identification of the particular device. If it's fairly easy to identify devices that are intended for high-side use only, you also could easyly set up something that would automatically send an email notification of the policy violation, so that appropriate action could taken. It would also help you if the high-side had some type of mechanism in place to insure that USB devices were registered before the high-side systems would accept them. This same registration id could be used to associate devices used with users if they pop up at a local bazaar or show up in your logs.

---

### Post by Fu22y_Lojik on 2010-03-31
Thanks so mcuh anyways.

Regards,

Shawn

---

### Post by Rubicon_82 on 2010-03-31
By examining '/var/log/syslog', you may be able to get some information about the USB device.  The log information for the kernel autodetect sequence will usually show the device manufacturer and model, but not serial number.  Although this probably won't be enough to identify the device in question, you should be able to cross reference the timestamps to '/var/log/user.log' (or auth.log).  This will hopefully provide the username for the person who was ignoring your computer usage policy.

To enable logging of USB device serial numbers, you can create udev scripts.  These would normally live in '/etc/udev/rules.d/'.  Refer to /etc/udev/rules.d/README and the udev(7) man page for information.  You can also look at the pre-existing scripts in /lib/udev/rules.d/ for examples.

---

### Post by Dayofswords on 2010-03-31
in the future, why not have the user not allowed to use USB, i'm not sure what military people would use on a computer for personal use involving a usb device

---

### Post by iponeverything on 2010-03-31
> **Dayofswords said:**
> in the future, why not have the user not allowed to use USB, i'm not sure what military people would use on a computer for personal use involving a usb device

To send pictures to family and to keep the pictures that they send you and loads of other things. In places like Iraq and Afghanistan morale is very important.

---

