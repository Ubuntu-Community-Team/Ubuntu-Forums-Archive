---
title: "Server install problems"
date: 2010-04-15
forum: Server Platforms
---

### Post by domgad on 2010-04-15
Hiya folks, I tried searching for this problem to find a solution and didn't get good result so i'm asking here. I created a bootable Usb Key with UnetBoot with the server ISO. It installs all fine on the computer. 

But my problem is that when I reboot it doesn't boot from the HDDs. I get the blinking cursor. If I put the Usb Key back in now Grub loads and boots fine and I can see the system. Is there a way to fix so it boots grub from the HDD and not needing the Usb Key ?

Thanks in advance,
Dom

---

### Post by ICEB3AR on 2010-04-15
Not to be rude, but why have you created a bootable USBKey if you don't want to boot from USB ? 

I DOn't know UnetBoot, but it sounds as if you need a normal install-image (and not UnetBoot), because you don't want to use the feature: booting from USB. Or am I wrong?

For the normal install CD (maybe for Unetboot)
Sure is there a solution. Install Grub on the HDD and everything should be fine. 
You could either use the install cd and then (don't know how to get in this menu without this somewhat silly way, but) when you go to back in the installationroutine there should open a list with the installationsteps. there you could choose Install Grub - Or install it manually.

---

### Post by dudumomo on 2010-04-15
You can install Ubuntu Desktop or Server or any other version by creating a LiveUSB with Unetbootin as you did I guess.

when you have your pen drive ready, just boot on the liveUSB and install Ubuntu on your hard drive. (Usually sda or hda or IDE)

---

