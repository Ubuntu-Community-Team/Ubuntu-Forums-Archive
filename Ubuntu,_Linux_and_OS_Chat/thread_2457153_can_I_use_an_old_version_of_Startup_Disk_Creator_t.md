---
title: "can I use an old version of Startup Disk Creator to create liveUSB of new Ubuntu?"
date: 2021-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2021-01-26
I have this old laptop, a Dell Inspiron E1505, 64-bit, 1GB RAM, and due to the limitations on the hardware, it will probably remain on Lubuntu 18.04 indefinitely. 

I'd like to use this laptop, as an emergency laptop in case something happens to my main laptop, to create liveUSBs of newer Ubuntu versions, such as Xubuntu 22.04 LTS for instance.

Would this be possible?

---

### Post by Bashing-om on 2021-01-26
ardouronerous; Hello -

> 
remain on Lubuntu 18.04 indefinitely.


Not at all recommended - consider that when 18.04 goes End_Of_Life there will no longer  be security updates provided. The machine will be internet facing in order to download, say for instance, new .ISOs.

Maybe; consider a minimal install of 20.04 ?

[INDENT]we do have options
[/INDENT]

---

### Post by ardouronerous on 2021-01-26
> **Bashing-om said:**
> ardouronerous; Hello -



Not at all recommended - consider that when 18.04 goes End_Of_Life there will no longer  be security updates provided. The machine will be internet facing in order to download, say for instance, new .ISOs.

Maybe; consider a minimal install of 20.04 ?
[INDENT]we do have options
[/INDENT]


I'll probably just go to an Internet cafe to download the new ISO and use my old laptop to create a liveUSB. Would this be at all possible?

---

### Post by Bashing-om on 2021-01-26
ardouronerous; Uh Huh

> 
I'll probably just go to an Internet cafe to download the new ISO and use my old laptop to create a liveUSB. Would this be at all possible?


That workie great. There is nothing preventing booting and using 18.04 - so long as security is not an issue.

- nostalgia is ubuntu 6.06 :) -

---

### Post by mastablasta on 2021-01-27
i suspect it is a 32 bit machine. i am sure there will be other OS still supporting 32 bit, though they might not be as familiar to you as lubuntu. they are aimed specifically at very old PC. and even if they are kind of niche, they will offer some support for USB creation or some browser for quick web search.

normally you can but sometimes you can't. i know that for example unetbootin and linuxliveUSB needed updates. Yumi needed update as well to create the bootable USB of new OS versions. if they distribute updated versions as portable binaries then it is no issue and you can use 18.04. but if updates need updated libraries then it can become an issue.
 

also even if you keep the OS connected to internet and only use it to access ubuntu repository and maybe some help pages / official documentation then you should be fine. because if they hacked that, then we have a much bigger problem than just your laptop.

i still have WinXP on the other side of the disk, that i last used sometime in 2019. i had a few attempts and one breach, while OS was still supported. nothing serious and i cleaned it up.

---

### Post by grahammechanical on 2021-01-27
I do not see why an old version of Startup Disk Creator should stumble burning a version of the Ubuntu ISO image newer than itself. It is just computer program readable data. After saying that, I recently failed to get Startup Disk Creator to burn some Debian ISO images. It just would not recognise the Debian ISO images as an ISO image.

I used mkusb-tool and that successfully burnt the ISO images to USB. mkusb is a comprehensive tool and us such it can seem compiicated. But it definitely works and works well. I suggest that you download the latest version. Test it with the latest Long Term Support ISO image. Then you know you have an ISO image that mkusb works with and is supported for another 4 years. Keep testing with each LTS version that is released.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Regards

---

