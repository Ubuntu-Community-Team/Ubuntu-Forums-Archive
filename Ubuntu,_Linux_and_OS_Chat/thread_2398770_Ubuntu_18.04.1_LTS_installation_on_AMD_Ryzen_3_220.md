---
title: "Ubuntu 18.04.1 LTS installation on AMD Ryzen 3 2200G and MSI A320M Pro VD/S"
date: 2018-08-17
forum: Ubuntu, Linux and OS Chat
---

### Post by skgs2 on 2018-08-17
Guys,

I completed a budget build of AMD Ryzen 3 2200G with Ubuntu 18.04.1 LTS.

My build
AMD Ryzen 3 2200G
MSI A320M Pro VD/S 
Kingston Value RAM DDR4 2400 MHz
1TB Seagate Barracuda 7200rpm
Old Samsung S19A100N 18.5inch monitor with 1366X 768 resolution.
Generic Cabinet
Corsair VS450 bronze 80+ power supply.
no extra graphics card.

I did face a lot of initial anxiety, but finally my build is up and running, although there are still some stuff i need to check.

I tried installing ubuntu18.04.1 LTS from a 4G kingston USB 2.0 drive connected to a USB3.0 port. But initially it failed to do 'Try Ubuntu' . I then tried Install ubuntu option without simultaneous internet connection. but installation freezed.
Then I connected it to internet and started fresh install and found there were remnants of my earlier installation. I opted for erase and install. It gave me two file errors of library not found(In spite of initially checking installation disk for errors), which I retried and resulted in same error, so I skipped it during install. I finished the install and rebooted. 
It froze after the install, had to press reset to boot in successfully. The first thing i did was to download [https://www2.ati.com/drivers/linux/ubuntu/amdgpu-pro-18.20-579836.tar.xz](https://www2.ati.com/drivers/linux/ubuntu/amdgpu-pro-18.20-579836.tar.xz) and follow the instructions on [https://support.amd.com/en-us/kb-articles/Pages/Installation-Instructions-for-amdgpu-Graphics-Stacks.aspx](https://support.amd.com/en-us/kb-articles/Pages/Installation-Instructions-for-amdgpu-Graphics-Stacks.aspx).

I installed  All-open Graphics stack, OpenCL and Vulkan. My installation went smoothly and it rebooted perfectly.

On next boot, I went to bios and set graphics memory to 2G and also set the time to my local time. Now my booting took a long time again and looked like it froze. I did a soft reset and could boot into ubuntu, but now the time in ubuntu was different. I changed it to my current local time and again rebooted. When I checked again the bios time it was changed again. I did some search on ubuntu forums and realized that ubuntu calculates local time from the  UTC which is set in the bios. Everytime I used to change the bios time, I my system used to take long to boot in to ubuntu and it used to freeze and I needed to reset the machine to boot normally.

Finally I stopped changing the bios time and let it to be at UTC and system started booting seamlessly into ubuntu without any problems. I checked my other ubuntu16.04LTS PC and realized that, even in that machine the bios time and OS time is different and it works perfectly.


I guess with Ubuntu 18.04.1LTS and AMD gpu drivers from their website, this type of build should work perfectly. My system is now 3 days old and I have had no problems although I am yet to test some games and image processing software. I will keep posting my experiences.

---

### Post by QIII on 2018-08-17
Not a support request.

Moved to Ubuntu, Linux and OS Chat

---

### Post by RichardLinx on 2018-08-17
Nice budget build. AMD Ryzen 3 2200G is a nice piece of hardware considering its price. How much RAM did you put in that thing? And what kernel version?

---

