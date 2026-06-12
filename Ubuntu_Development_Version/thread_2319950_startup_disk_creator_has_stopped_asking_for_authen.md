---
title: "startup disk creator has stopped asking for authentication"
date: 2016-04-08
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-04-08
This is a serious security bug.

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1568149](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1568149)

---

### Post by sudodus on 2016-04-08
I think it is by intention, so that people without superuser privileges can create USB boot drives.

But I agree with you, that people without superuser privileges might not understand what they can destroy, not only by creating USB boot drives, but also by using them.

*Edit:* And people with superuser privileges might need the warning (by typing the password).

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> I think it is by intention, so that people without superuser privileges can create USB boot drives.

But I agree with you, that people without superuser privileges might not understand what they can destroy, not only by creating USB boot drives, but also by using them.

*Edit:* And people with superuser privileges might need the warning (by typing the password).


 Whether intentional or not , I see it as a security risk. It is also a GUI fry-point in that  the end_user space is affected - that being that there is no last-chance stop point and so hdds can be easily wiped without the users knowledge. 

 Not trying to be overly emphatic here .. but sdc and it's components are in serious degredation - but - perhaps it needs to be done to find what is causing these dilemas with standard formatting  of USBs, or, at least the entry points where code can be patched in.

btw .. if it was you who added meetoo to my bug .. thanks . I thought it was only me.:)

---

### Post by mc4man on 2016-04-08
I believe previously Sdc only needed auth to install the bootloader. Now it doesn't do that so no auth is required. 
As far as the other polkit actions (mount & image) those are overriden from admin_auth_keep  to yes in com.ubuntu.desktop.pkla
(- location is - /var/lib/polkit-1/localauthority/10-vendor.d
> [usb-creator]
Identity=unix-group:admin;unix-group:sudo
Action=com.ubuntu.usbcreator.mount;com.ubuntu.usbcreator.image
ResultActive=yes

---

### Post by $yl9pAR%t on 2016-04-08
The same on Ubuntu GNOME 16.04 (I guess on other flavores, too), but I don't consider it as a bug.

---

### Post by ventrical on 2016-04-08
Here is from marc D.

> 

[SIZE=2]The policykit-desktop-privileges package was changed in 2011 to allow
 writing images without a password:
 
 policykit-desktop-privileges (0.7) oneiric; urgency=low
 
   * Allow local admins to do the less harmful usb-creator actions (mounting
     and writing image) without a password.
  -- Martin Pitt <martin.pitt@ubuntu.com>   Wed, 06 Jul 2011 10:12:36 +0200
 
 The user still needs to be in the admin group.
 
 Is this no longer sufficient?



  This is totally mind boggling. SDC has always asked me for password until I upgraded udisks2. I wonder what planet I am on :)
 [/SIZE]

---

### Post by ventrical on 2016-04-08
> **mc4man said:**
> I believe previously Sdc only needed auth to install the bootloader. Now it doesn't do that so no auth is required. 
As far as the other polkit actions (mount & image) those are overriden from admin_auth_keep  to yes in com.ubuntu.desktop.pkla
(- location is - /var/lib/polkit-1/localauthority/10-vendor.d

I would swear on a stack of bibles that it prompted me for a password when I used it today after upgrading the udisks2 package. Then , on re-boot it stopped asking me.

---

### Post by sudodus on 2016-04-08
I think mc4man is right - the SDC wanted a password only for writing the bootloader, and now the bootloader is written as part of the cloning, which is allowed, but as Marc D. wrote, 'The user still needs to be in the admin group.' I did not realize this. It keeps the least responsible people away from using it, so maybe this is enough :-)

---

### Post by mc4man on 2016-04-08
I think it's fine as is (sudo group). The way it was before was a bit weird, asking for a password at the very end.
That was likely from a slight unwillingness to do away with the password prompt for sudo user altogether. If I remember right at some point users had to enter password at least twice during process which made no sense. The fix to that was to add the pkla override & just leave the one password prompt at bootloader install.

Myself used to override that thru a user pkla created in /var/lib/polkit-1/localauthority/50-local.d/  as some times SDC used to hang or fail at that prompt..

---

### Post by ventrical on 2016-04-08
My bad here.  I have been using gnome disks and mkusb to make bootable ISOs for quite some time so .. I made a mis-step in my assumption.  I e-mailed marc and made note of this erroneous assumption on my part. Thanks for your help.
Will mark the thread as solved.

---

