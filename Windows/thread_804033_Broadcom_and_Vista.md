---
title: "Broadcom and Vista"
date: 2008-05-22
forum: Windows
---

### Post by Aeph on 2008-05-22
Got Vista for DX10. Installed it and began to configure my drivers. After I installed my wireless card Vista decided that it didn't want to boot anymore. If I remember correctly, my card is a Broadcom b43 (though I erased my Linux install to put Vista on, though I plan to put Linux back on my larger hard drive once it arrives). Does anyone know how to fix this?

---

### Post by MaxIBoy on 2008-05-22
Besides getting Linux again? The only thing is to boot off a Linux CD, recover whatever files you need to onto another hard drive, and install Vista all over again. If the wireless card drivers continue to mess it up, consider it a message from above that your computer and Vista just weren't meant to be together.

---

### Post by smoker on 2008-05-23
see if you can boot into safe mode. if so uninstall the wireless drivers. if the machine boots ok after that, then you definately know it is a driver issue. go to the broadcom support website (obviously on another pc), and check if they do have vista drivers for your card, and download the latest. it is possible they don't, vista hardware support is not all it could be.

best of luck

---

### Post by Aeph on 2008-05-26
Got the wireless card working. Unfortunately, it disconnects from the internet after about 20 seconds. Then I can reboot and get another 20 seconds.

Not very useful.

---

### Post by marsmissionaries on 2008-05-27
Wow even windows can't handle the broadcom chipsets :)

---

### Post by rickyjones on 2008-05-27
> **Aeph said:**
> Got the wireless card working. Unfortunately, it disconnects from the internet after about 20 seconds. Then I can reboot and get another 20 seconds.

Not very useful.

Sounds like Broadcom can't create viable Windows drivers. Complain to that company about them. 

-Richard

---

### Post by sabamanga on 2008-05-27
I installed Vista a few days ago on a partition on my MacBook, the broadcom drivers came with my Mac install disk, and they worked on Vista...
Ha.. If only they would work on Ubuntu.. I can't even connect to the internet via ethernet :(

---

### Post by r76 on 2008-05-27
> **marsmissionaries said:**
> Wow even windows can't handle the broadcom chipsets :)

Haha, that's exactly what I thought!  I replaced a mini-PCI broadcom wifi card in my Dell laptop for an Intel 2200bg card, so I could run linux without the pain of workarounds, and I noticed that when I now boot the same laptop into xp, wireless connects quicker and never drops.  For new PC purchases at work now I always specify Intel rather than broadcom.

To the OP, have you tried [booting with the Vista disk]("http://windowshelp.microsoft.com/Windows/en-US/help/24cccadc-1c47-4e04-a1e5-c7236c943fd11033.mspx") in to repair?

---

### Post by Aeph on 2008-05-29
> **r76 said:**
> To the OP, have you tried [booting with the Vista disk]("http://windowshelp.microsoft.com/Windows/en-US/help/24cccadc-1c47-4e04-a1e5-c7236c943fd11033.mspx") in to repair?

Actually, the first thing I tried was to reinstall Windows, but that didnt help. It still won't work.

---

### Post by MONODA on 2008-05-29
You should be able to boot into safemode and rollback the driver with device manager or something. If not, try system restore with your recovery cd, you did make one right?

---

### Post by rickyjones on 2008-05-29
> **Aeph said:**
> Actually, the first thing I tried was to reinstall Windows, but that didnt help. It still won't work.

You reinstalled Vista and then what happened? Reading this it sounds like: "Windows Vista would no longer boot after installing drivers. I reinstalled Vista. It still does not boot." Or did you mean that after reinstalling Vista, and then installing the same drivers, it then refused to boot?

I still think that you have a botched driver. I recommend contacting the OEM and getting an up-to-date driver.

-Richard

---

### Post by Aeph on 2008-05-29
Okay, heres what happened:

I got Vista from Newegg and installed it onto my hard drive. I began to install drivers onto it, and once I had installed the wireless driver from the CD, the OS refused to boot. So I reinstalled since I hadn't really done anything yet anyway and tried installing the drivers again. This time, I found that the wireless card works natively in Vista, and in fact does not like the install CD. The internet kept dropping out, so I tried to reinstall yet again. Same problem. I know the wireless router and card are working because they work perfectly in my Ubuntu partition and worked in XP. But it doesn't want to work in Vista.

This really bothers me because one of the reasons for purchasing Vista was to play Shadowrun with my friends online. Of course, this can't really be done if I am constantly disconnected every minute or so.

---

### Post by dca on 2008-05-30
Don't quote me but I don't believe Broadcom drivers are even necessary on Vista.  If you bought the PC from BestBuy, it's on there and if you do a clean install of Vista, it's on there.  If the vers that comes w/ Vista OEM DVD is outdated surprisingly enough Vista updates them as a part of your natural progression of ridiculous Microsoft updates.

---

### Post by Aeph on 2008-06-03
Would it be best to just go out and buy a new wireless card?

---

