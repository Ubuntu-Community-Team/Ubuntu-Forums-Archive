---
title: "Microsoft: &quot;Install Damn Small Linux to your flash drive&quot;"
date: 2010-05-18
forum: The Cafe
---

### Post by 3rdalbum on 2010-05-18
I was looking online to see if you could install Vista onto a flash drive, and I came across this question on Microsoft Technet. The Microsoft guy doesn't really answer the question, but he does link the asker to an article about installing DSL to a flash drive.

[http://social.technet.microsoft.com/Forums/en/itprovistadeployment/thread/dc2a666f-04ca-4a3a-b995-f709f16341f1](http://social.technet.microsoft.com/Forums/en/itprovistadeployment/thread/dc2a666f-04ca-4a3a-b995-f709f16341f1)

Can anyone actually tell me if Vista can be installed to a flash drive?

---

### Post by murderslastcrow on 2010-05-18
I believe it's too resource intensive to do so. Even with Windows XP, the best you can do is create a BartPE or other PE environment and burn it to a CD or build it with isolinux on a USB, and even then it runs quite slowly. And again, that's XP.

So, short answer? No. Long answer? Definitely not. The closest you could get is running a LiveUSB of a distro with Wine with Windows Vista compatibility mode enabled by default.

Of course, if you mean running the installation disc from USB, that's a different story.

---

### Post by ronnielsen1 on 2010-05-18
> Even with Windows XP, the best you can do is create a BartPE or other PE  environment and burn it to a CD or build it with isolinux on a USB, and  even then it runs quite slowly. 

While I agree with that (I have a xp media live cd that runs as fast as kde with 64M Ram) I believe that flash is quicker. I have not tried either one of these methods below

> I just did this method on one of my friends machine and installed the  new Windows 7 BETA. The main advantage is that by using USB drive you  will be able to install Windows 7/Vista in just 15 minutes. You can also  use this bootable USB drive on friend’s computer who doesn’t have a DVD  optical drive.

[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

> **Requirements to install [Windows 7]("http://www.intowindows.com/download-windows-7-rc-available-now/") on USB:**
 # An USB flash drive with a minimum of 6 GB disk  space to install Windows 7 or Vista. You can use a 4 GB drive to install  XP.
 # Bootable [Windows]("http://www.intowindows.com/windows-7-rtm/")  7 USB or DVD.
 # Free time


[http://www.intowindows.com/install-windows-7-on-usb/](http://www.intowindows.com/install-windows-7-on-usb/)

---

### Post by CharlesA on 2010-05-18
If you are thinking of installing the entire OS onto a thumb drive, good luck.

The second link that ronnielsen1 posted would be the best bet. That way you would't have to deal with a gigantic USB thumb drive (needing space for the boot partition and the normal file system).

Only downside is that you need a machine capable of running virtualbox.

---

### Post by pwnst*r on 2010-05-18
You're thread title should have been:

"Some guy that mods an MS forum..."

---

