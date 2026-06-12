---
title: "Panp8: Review and Questions"
date: 2011-09-27
forum: System76 Support
---

### Post by 3Miro on 2011-09-27
Hi Everyone,

yesterday I got my panp8, with i7 CPU, 8GB of RAM, 500GB HDD and Intel Centrino Advanced WiFi (the rest is standard). I decided to share my experience so far and I would also like to ask some questions.

The most important question: **Why does the synaptic touch-pad doesn't have scroll area on the side, is it something that I need to enable or is it just not an available feature?** I thought all touch-pads come with the side scroll enabled and I am quite used to it, I would surely miss this feature and I would have liked to know about this in advanced.

The design is very slick, those machines really look cool. I am not a fan of the striped texture, but the overall look is really nice. The machine was also packaged very well.

My first shock came when I opened the screen and saw the Nvidia Optimus sticker. I ordered a laptop with Intel video and it came with Intel video; neither in the BIOS nor anywhere else did I see mention of Nvidia. However, the sticker is there. So my question is: **Do I have an Nvidia chip inside that has been disabled or has the Nvidia chip been removed and the sticker left-over?**

Other than that, the Intel HD works great. No problems with Unity or special effects, everything works very smoothly.

Everything form audio, video and wifi worked right out of the box, and it is worth noting that you can get the same performance out of a liveCD. You can run the Ubuntu 11.04 live CD and get Unity + Desktop Effects + Wifi without any extra drivers. This is a huge thing for me or anyone interested in running other distros. I also tested the system with Gentoo LiveDVD and KDE, again everything worked right away even the kwin 3D cube.

It is worth noting that Xubuntu liveCD 10.10 did not boot. I guess the older Linux versions wouldn't like the Sandy Bridge graphics, so you should be looking at 11.04 or some other distro with newer kernel and Xorg.

Overall I am very happy. I have not tested the CPU for speed and I only did a very preliminary for the battery life. Approximately 2:00 of battery life isn't much, but I was anticipating this due to the extra RAM, CPU and HDD (I actually got an extra battery). With the default i5 and 2 - 4GB of RAM, the battery life should be higher.

I just want to note couple of extra things:
1. The HDD layout was a bit strange. I only had / and swap partitions. I thought the standard was to also have an extra /home, which makes reinstalls and upgrades that much easier. Not a problem for me since I would repartition everything anyway, but still.

2. The swap size was 7.4GB which is less than the 8GB of RAM, however, hibernation still worked so I guess this is not really an issue.

---

### Post by vanhenryjr on 2011-09-27
Sounds great. I have a gazelle ordered with very similar specs to yours. If it comes out as good as yours sounds i will be thrilled.

---

### Post by isantop on 2011-09-28
> **3Miro said:**
> The most important question: **Why does the synaptic touch-pad doesn't have scroll area on the side, is it something that I need to enable or is it just not an available feature?** I thought all touch-pads come with the side scroll enabled and I am quite used to it, I would surely miss this feature and I would have liked to know about this in advanced.

All of our touchpads use two-finger scrolling by default. To scroll, place two fingers anywhere on the touchpad, and move them both in unison in the direction you want to scroll. If you prefer, you can switch to the standard edge scrolling by opening the mouse configuration dialog, clicking on Touchpad, then changing the scrolling method from two finger to edge.

> **3Miro said:**
> My first shock came when I opened the screen and saw the Nvidia Optimus sticker. I ordered a laptop with Intel video and it came with Intel video; neither in the BIOS nor anywhere else did I see mention of Nvidia. However, the sticker is there. So my question is: **Do I have an Nvidia chip inside that has been disabled or has the Nvidia chip been removed and the sticker left-over?**

You definitely don't have an Nvidia chip in your system, and you never did. I'm not sure how your's came to have the sticker on it, but we'll make sure that sort of thing doesn't happen again.

> **3Miro said:**
> It is worth noting that Xubuntu liveCD 10.10 did not boot. I guess the older Linux versions wouldn't like the Sandy Bridge graphics, so you should be looking at 11.04 or some other distro with newer kernel and Xorg.

> **3Miro said:**
> 1. The HDD layout was a bit strange. I only had / and swap partitions. I thought the standard was to also have an extra /home, which makes reinstalls and upgrades that much easier. Not a problem for me since I would repartition everything anyway, but still.

Actually, the Ubuntu installer is smart enough not to overwrite your /home directory anyway, and having the home partiton separate from the root partition leads to issues with filling up one or the other and not being able to use your hard drive completely.

I'm glad you like your system! Let me know if there's anything else you'd like to ask.

---

### Post by 3Miro on 2011-09-28
Hi isantop,

thanks for the reply and shading light on my post.

1. Good to know that I would be able to get the mouse scroll working. Currently I cannot get the two fingers mouse scroll working (it is either disabled or I am too clumsy). I would like to get the old edge style anyway, however, I looked at the mouse settings and there was nothing about a touchpad. This is reinstalled Ubuntu 11.04, not the one from you guys (I repartitioned the HDD to dual-boot with Gentoo). So do I have to install anything extra?

2. Good to know about the Nvidia sticker. I posted a screenshot of the sticker and the Mouse options menu. My phone doesn't have much of a camera, however, I hope you can see the System76 driver, the Mouse options and the Nvidia Sticker.

For anyone who cares, all the hardware works well with Gentoo. Only the wireless required extra firmware (available in the repository) and it is inbuild in the kernel so you don't have to reinstall it on kernel update (like one would with the Nvidia driver).

---

### Post by 3Miro on 2011-09-28
Thanks for the heads up on the touchpad. I actually did the unthinkable and tried to read the manual.:shock:

The problem with the touchpad was that I had booted the machine with an external mouse plugged in. I rebooted without the mouse and the touchpad tab appeared in all the preferences. Now I have to find out how to reset the settings without rebooting, but this is a small problem.

Two finger scrolling works now, however, I cannot get the side scroll to work. I will read some more, but I guess I will have to get used to the two finger scrolling for now (it isn't bad at all actually).

EDIT: edge scroll actually works ... kind of. It is very unreliable, it have to scroll on an area not immediately to the edge, but a bit inside. Then the scroll works for a some distance and then it turns into regular mouse move. I will see if I can adjust the scroll settings, but I am getting used to the two-fingers and I guess this issue is resolved now.

---

