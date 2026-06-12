---
title: "No default encryption on Ubuntu 20.04 Desktop?"
date: 2020-04-25
forum: Security
---

### Post by johnnyslogan on 2020-04-25
Hi,

Just installed 20.04 Desktop. Nothing seems to be encrypted per default. So no /home encryption and no fulldisk encryption. And as opposed to other Ubuntu installs, I don't recall the install wizard explicitly asking me, weather I wanted encryption on either disk or home. Am I missing something?

And I know I can probably turn it on using advanced options during install, but why not have at least home-encryption set as a visible option, and maybe as default. 

And also: 20.04 looks very cool and crisp. 

Best regards,
Jakob

---

### Post by sudodus on 2020-04-25
There are security holes in the system with 'encrypted home' and 'encrypted swap'. For that reason it is abandoned.

 'Encrypted disk' alias LVM with LUKS encryption is available via the installer (at the partitioning window). See the attached screenshot.

I think that it is moved to a sub-menu because many people have been using it without really needing it, and too many of them have had problems because data recovery is much more difficult compared to a normal installation. After all, I think the main security threat is via the internet when the computer is running, and encrypted disk does not protect against that.

---

### Post by johnnyslogan on 2020-04-25
I would say data encryption in general is important for instance when units are lost or stolen. Also in this day and age often data is stored in the cloud, so the risk of data loss, if users forget their password - again in general - is limited. But on the other hand the cookies that give access to the cloud data are stored locally. And should be encrypted. 

Anyway, thanks for the input. I will reinstall with LUKS and LVM.

---

### Post by kevdog on 2020-04-26
I haven't run through the 20.04 installation process (just upgrading from 18.04).  Does the installer not offer ability to install zfs encryption?

---

### Post by EuclideanCoffee on 2020-04-26
I've gone through the install process a few time and am running 20.04 (just now LTS). The encryption option is more difficult to customize than it has been.

Would you be interested in a preseed configuration for the zfs partition? I can hack this today and write a tutorial. I don't know where to put it though.

---

### Post by sudodus on 2020-04-26
> **EuclideanCoffee said:**
> I've gone through the install process a few time and am running 20.04 (just now LTS). The encryption option is more difficult to customize than it has been.

Would you be interested in a preseed configuration for the zfs partition? I can hack this today and write a tutorial. I don't know where to put it though.

There is a [Tutorial Forum](https://ubuntuforums.org/forumdisplay.php?f=100) :-)

---

### Post by thedarb2 on 2020-04-27
Try this, works great!  Note, this does not encrypt your swap, so that's a separate thing to look into:
[https://linsomniac.gitlab.io/post/2020-04-09-ubuntu-2004-encrypted-zfs/](https://linsomniac.gitlab.io/post/2020-04-09-ubuntu-2004-encrypted-zfs/)

---

