---
title: "How to burn windows 10 iso to usb."
date: 2017-04-15
forum: Windows
---

### Post by Hewjr100 on 2017-04-15
Does anyone know how to do this.  My windows 10 installation on usb has a corrupt file message after copying files over to hdd.  I know that the flash drive has to be formatted in NTFS, but other than that I do not know how to do it in ubuntu gnome 17.04.

Henry

---

### Post by RobGoss on 2017-04-15
Hello and welcome, This might be of use for creating a bootable USB for Windows [http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html](http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html) I have never tried this method so I can't say if it's 100%

---

### Post by Hewjr100 on 2017-04-15
Checking it out now, thanks.

Henry

---

### Post by RobGoss on 2017-04-15
No problem lets us now how it works

---

### Post by yancek on 2017-04-15
I've never used the winusb software so have no idea if it works.  I have used the method explained in detail at the site below to create a windows bootable iso and boot that installer with Grub and successfully install windows.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by RobGoss on 2017-04-16
> **yancek said:**
> I've never used the winusb software so have no idea if it works.  I have used the method explained in detail at the site below to create a windows bootable iso and boot that installer with Grub and successfully install windows.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

Nice tutorial** Yancek, **when I was using Windows they never had these options thanks for sharing the link

---

### Post by yancek on 2017-04-16
Reading over the initial post by the OP, I'm not really sure what he's doing based on the statement below.

> My windows 10 installation on usb has a corrupt file message after copying files over to hdd. 

The title referes to putting a windows 10 installer on a usb which is not the same as having an install of windows on a usb.  The latter can't be done with the windows installer as it is designed to detect and attempted installation to a usb drive and will result in the following message:

> windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports

I'm not sure what is being referred to by the statement:  "My windows 10 installation on usb has a corrupt file message after copying files over to hdd"  as copying anything FROM the usb to the hard drive would not have any effect on the usb?

---

### Post by Hewjr100 on 2017-04-16
Ok sorry for the delay.  I tried winusb from the terminal all went well, however the same thing happened after files were copied to hdd from usb the installation failed with the same corrupt file error.  Today I will try a different iso and flash drive.

Henry

---

### Post by Hewjr100 on 2017-04-16
Alright, it's a no go on winusb, third iso and third usb same failure when booting from usb and attempting to install windows 10.  It is windows 10 version 1703  This is the most recent iso with the creators update included.  anyway I am happy with linux, did not use windows anyway.  The only reason I install it is because it was free.

Henry

---

### Post by wildmanne39 on 2017-04-16
Have you used this page to get and install windows?
[https://windows10.help/blogs/entry/24-windows-10-creators-update-version-1703-iso-files-now-available-for-download/](https://windows10.help/blogs/entry/24-windows-10-creators-update-version-1703-iso-files-now-available-for-download/)

---

### Post by wildmanne39 on 2017-04-16
*Thread moved to **Windows**.*

Thread re-opened!

---

### Post by QIII on 2017-04-16
Hello!

Before anyone gives any further advice, the OP needs to describe to is what is meant by "free".

Please hold all further comment until then.

---

### Post by Hewjr100 on 2017-04-17
Hey everyone I sort of figured it out.  The problem was not with winusb or my laptop or me.  The issue is with windows 10 version 1703 iso.  Just for the heck of it I downloaded windows 10 1607 ios from ms.  This iso successfully installed windows 10 without incident.

Henry

---

### Post by Hewjr100 on 2017-04-17
Found a solution.  Instead of downloading windows 10 version 1703 I downloaded version 1607 instead.  This iso  was bruned on usb with winusb, and was able run and complete installation of windows 10.  Have no idea why version 1703 did not work.

Henry

---

### Post by Hewjr100 on 2017-04-17
QIII What I mean by free as in I did not have to purchase a license for windows 10, it was a free upgrade from windows 8.1 in my case.

---

### Post by QIII on 2017-04-17
OK.  However, the free grace period for upgrading has long since passed, so you will likely have to buy a key to activate Win10.

---

### Post by Hewjr100 on 2017-04-17
Sorry, I forgot to mention I have been a insider since day one, plus I had windows 8.1 so basically I had it since it came out (windows 10).  From the first time you log in with ms account you get a digital entitlement license.  as you probably know this means I can fresh install windows 10 as much as I like, so long as it is on the same pc/laptop and using the same ms account log in.

Henry

---

### Post by eankerasg on 2017-12-27
> **RabGoes said:**
> Hello and welcome, This might be of use for creating a bootable USB for Windows, I have never tried this method so I can't say if it's 100%
Un huh  , Sites like this I can find a lot on Google , but that's actually not very useful, you can burn Windows iso to usb , but if flash drives are not formatted in NTFS , everything is invalid, isn't it ?
I got some tutorial about it on Google , not all the advides are good for us . 
[https://www.iseepassword.com/how-to-burn-iso-to-usb-drive.html](https://www.iseepassword.com/how-to-burn-iso-to-usb-drive.html)
[https://forums.macrumors.com/threads/burning-a-windows-8-iso-to-a-usb-flash-drive.1423037/](https://forums.macrumors.com/threads/burning-a-windows-8-iso-to-a-usb-flash-drive.1423037/)

---

