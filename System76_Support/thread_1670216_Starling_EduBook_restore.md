---
title: "Starling EduBook restore"
date: 2011-01-18
forum: System76 Support
---

### Post by alienprdkt on 2011-01-18
I have just got this and used it for about an hour, upon first reboot It wont boot. I am stuck at the initramfs shell. And some error about not finding an ini file.

Is this an easy fix or shall I restore?

Install Ubuntu from the installer disk then install the systems76 driver, is the driver for the Starling EduBook specific or is it the same as any other systems76  driver, that I get from there site?

Thanks in advance on helping me out with my 2hr. old Starling EduBook.

---

### Post by isantop on 2011-01-18
Hi.

I think a restore is in order. Do you remember if anything unusual happened when you rebooted?

The driver automatically detects what system you're running on, and applies any patches/drivers for your system. So it's that same package as for other systems.

---

### Post by alienprdkt on 2011-01-18
> **isantop said:**
> Hi.

I think a restore is in order. Do you remember if anything unusual happened when you rebooted?

The driver automatically detects what system you're running on, and applies any patches/drivers for your system. So it's that same package as for other systems.


I created a new user and user group and rebooted but never booted up. thats all 

Thanks for the driver info.

---

### Post by isantop on 2011-01-21
Okay, I think a restore is the easiest thing to do right now. 

If you ran updates, it's possible that Grub got messed up. When you restore, if you're asked to configure "grub" or "grub-pc", then select *only* "/dev/sda", and not "/dev/sda1" as this will cause it to fail.

---

