---
title: "login screen resolution is wrong"
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kraziyk on 2012-03-06
Hi,

I just upgraded to Ubuntu 12.04, and the login screen resolution is all wrong. It is way to big for my screen. How do I change the resolution?

Thanks.

---

### Post by overdrank on 2012-03-06
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by kraziyk on 2012-03-08
I installed 12.04, and the screen resoluiton is to big on the Log-in screen where you choose user and enter your password. How do I change it, so that it fits my screen? I have changed my desktop resoultion but it didn't help at all.

---

### Post by cariboo on 2012-03-08
Please don't create multiple threads on the same subject, I have merged your two threads.

Could you tell us what display adapter and monitor you are using?

---

### Post by kraziyk on 2012-03-08
Its a normal VGA monitor hook up. The monitor is a emachine L22ycet

---

### Post by grahammechanical on 2012-03-08
It depends upon the video driver that is in use.

The default driver is the open source Nouveau. For that you go to system Settings Displays or just select the second option (Displays) in the Power cog menu.

See if that will let you change the resolution.

If you are using a proprietary driver activated through Additional Drivers then it should come with its own settings utility. And that may give you an option to change resolution.

Regards.

---

### Post by kraziyk on 2012-03-08
Well I updated my nvidia driver, and changed my desktop res. But the login screen remains to big.

---

### Post by No1StoppedMe on 2012-04-09
I"m also having this problem. Has anyone had any luck finding a solution? I'm using a Sharp Aquos TV 32" and it doesn't have the auto-adjust feature that the newer models have. I'm also using nVidia drivers and they automatically adjust the display config utility in the system settings. It seems as though the login screen runs off a seperate utility than the desktop does as it's not changing the login screen when I change the desktop resolution.

Any help here would be appreciated as I have run out of ideas.

---

### Post by cyberedsun on 2012-04-11
I also faced this issue after upgraded to 12.04 directly from 11.10. I think this is a temporary error and will be fixed soon.

---

### Post by cariboo on 2012-04-11
Could it be that the picture you've chosen for a background is much smaller than your screen resolution? Have you tried different backgrounds to see if it also happens?

---

### Post by Xgen on 2012-04-11
Yes, if picture size is what he is referring to, I find that if I don't resize the wallpaper to the aspect ratio of my laptop (16:9) then it will go into 'zoom' mode.

---

### Post by dcstar on 2012-04-12
> **No1StoppedMe said:**
> I"m also having this problem. Has anyone had any luck finding a solution? I'm using a Sharp Aquos TV 32" and it doesn't have the auto-adjust feature that the newer models have. I'm also using nVidia drivers and they automatically adjust the display config utility in the system settings. It seems as though the login screen runs off a seperate utility than the desktop does as it's not changing the login screen when I change the desktop resolution.

Any help here would be appreciated as I have run out of ideas.

You can add a VESA mode resolution to the Grub config file to force a particular resolution for the boot and Plymouth screens. Do a web search for the detailed instructions.

I believe the Ubuntu-tweak package may also allow you to change this setting.

I actually use BURG instead of GRUB because it is more flexible in this area.

---

