---
title: "My Desktop went ubuntu"
date: 2020-06-09
forum: Ubuntu, Linux and OS Chat
---

### Post by aughey on 2020-06-09
I decided to add Ubuntu 20.04 to my trusty old Philips desktop. It was one that Microsoft kindly upgraded to windows 10 when the upgrades were still for free even though I never asked them to as I was happy with windows 7 at the time. Thing was it was running as a 32 bit windows 10 system. So I wasn't sure if it could share a drive with Ubuntu 20.04 as I understand that is a 64 bit OS. So I was in CEX one day and they had a 1.0 terrabyte 3.5" HD at the right price so I bought it. My plan at that stage was to take a chance and reinstall Windows 10 x 64bit on one half of the drive and Ubuntu 20.04 on the other half.  Meanwhile my desktop started flashing me messages about a CMOS fault but it did still boot up by pressing F1 OK. So I googled it and all it was the little battery which keeps the time and date etc needed renewed. So I bought a pack of CMOS batteries and took the sides off the desktop to replace it. As I was doing so I noticed there were in fact four SATA connectors on the motherboard. It suddenly struck me that I didn't need to replace the current HDD at all. So I bought a molex to SATA power splitter and a SATA lead. I installed the 1.0 terrabyte hard drive. I fired up my DVD with 20.04 ISO but it was insisting on installing the 20.04 onto my original windows 10 hard drive. I did find the other drive but I didn't understand how to continue so I completely stopped the install at that point. I then reopened the desktop and I unplugged the power and data cables to the windows hard drive and restarted the install. Now the 20.04 install went smoothly onto the larger drive. So I closed down the desktop and reconnected the windows 10 hard drive. I now can swap easily between the two drives by changing the boot order in the bios. :p:p

---

### Post by crip720 on 2020-06-09
Think doing a simple [code] sudo update-grub [code]  will place windows in grub and give you easier choice.  Need both drives connected.

---

### Post by kurt18947 on 2020-06-10
> **crip720 said:**
> Think doing a simple [code] sudo update-grub [code]  will place windows in grub and give you easier choice.  Need both drives connected.

I was using grub to dual boot happily then one day a Windows 10 update overwrote grub. Gee, thanks Microsoft.  I was able to restore using boot-repair but Windows was not getting another chance. It now resides on a separate hard drive and I plug it in if necessary after unplugging the Ubuntu drive. The Windows drive has not been started in months. I guess it'll be the mother of all updates if/when it's plugged in again:lolflag:

---

### Post by CelticWarrior on 2020-06-10
> **kurt18947 said:**
> I was using grub to dual boot happily then one day a Windows 10 update overwrote grub. Gee, thanks Microsoft.  I was able to restore using boot-repair but Windows was not getting another chance. It now resides on a separate hard drive and I plug it in if necessary after unplugging the Ubuntu drive. The Windows 

A proper UEFI mode dual-boot has no such problems. Windows feature updates may change the UEFI boot priority to itself for your convenience (those updates require several reboots) but you can always change it back to "Ubuntu" (Grub) in UEFI settings, that's all.

---

### Post by aughey on 2020-06-10
Just when you mention Windows updates I recently booted my laptop into Windows and as usual it decided to update. After an interminable wait it presented me with its new version of the windows browser. There was no X to stop it taking me to whatever site it was insisting I should visit. I needed to look up a phone number of a local pharmacy so I had to hit Control Alt Delete then closed it down using task manager that way I then unpinned it from the taskbar.

---

### Post by CelticWarrior on 2020-06-10
> **aughey said:**
> Just when you mention Windows updates I recently booted my laptop into Windows and as usual it decided to update. After an interminable wait it presented me with its new version of the windows browser. There was no X to stop it taking me to whatever site it was insisting I should visit. I needed to look up a phone number of a local pharmacy so I had to hit Control Alt Delete then closed it down using task manager that way I then unpinned it from the taskbar.

Pressing F11 to get out of the full screen mode is faster and safer :lolflag:

---

