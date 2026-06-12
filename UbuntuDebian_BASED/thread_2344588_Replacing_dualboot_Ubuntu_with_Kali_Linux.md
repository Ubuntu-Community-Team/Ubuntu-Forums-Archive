---
title: "Replacing dualboot Ubuntu with Kali Linux"
date: 2016-11-26
forum: Ubuntu/Debian BASED
---

### Post by fftorettol on 2016-11-26
Last year, I installed Lunux Ubuntu on my PC as dual boot (GRUB). First option is Windows 10, second one is Linux Ubuntu... What I want now, is to replace Ubuntu with Kali Linux.. Can you guys help me through this process?

Linux Ubuntu is installed on its own partition, and Windows 10 on its own.. Do I need to remove Linux partition now and then add it again, or I can just overwrite it somehow with Kali? I was also informed that after deleting Linux partition will cause that the GRUB boot loader won't boot my computer properly. What should I do now? Thanks in advance!

---

### Post by howefield on 2016-11-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by yancek on 2016-11-26
Are you planning to use Kali in your job as a computer forensics expert or are you trying to learn computer forensics?  If you are trying to learn computer forensics, I would suggest you use the instructions at the Kali site to create a bootable/persistent install of Kali on a flash drive.  Kali is a terrible choice to use as a standard Desktop system and that is explained on their site.

---

### Post by fftorettol on 2016-11-27
> **yancek said:**
> Are you planning to use Kali in your job as a computer forensics expert or are you trying to learn computer forensics?  If you are trying to learn computer forensics, I would suggest you use the instructions at the Kali site to create a bootable/persistent install of Kali on a flash drive.  Kali is a terrible choice to use as a standard Desktop system and that is explained on their site.

I'm actually trying to learn computer forensics. I found a link on their website with informations you provided: [LINK]("http://docs.kali.org/downloading/kali-linux-live-usb-install").

So if I uderstand this right, I just create a bootable USB with Kali Linux image on it, and plug it in when booting up a PC(I know how to install Windows through bootable USB, But I'm worried that Kali Linux will overwrite my Windows partition. Will I be able to choose on what partition do I want to Install it?

Thank you!

---

### Post by yancek on 2016-11-27
The link you posted above is for creating a Live Kali system on a usb.  The link below is for creating a "persistent" Live Kali system which means you can make/save changes on it.  No, you don't need to install it anywhere you would just plug it in when you want to use it and boot it from any computer capable of being booted from a usb.  There is no need to install it on your computer hard drive.

> But I'm worried that Kali Linux will overwrite my Windows partition.  Will I be able to choose on what partition do I want to Install it?

The Kali Linux site has documentation and instructions on that at their site  below.  You would just select the partition(s) on which you installed Ubuntu to install Kali.  You would also need to be aware of whether you are using UEFI currently with windows/Ubuntu.  If your windows is UEFI/GPT, you need to install any other system UEFI or you will have problems booting.  Since your intention is to learn computer forensics and your knowledge of installing is limited, it would seem to me it would be a lot simpler and less problematic to use a Live persistent USB for Kali.

[http://docs.kali.org/installation/dual-boot-kali-with-windows](http://docs.kali.org/installation/dual-boot-kali-with-windows)

---

