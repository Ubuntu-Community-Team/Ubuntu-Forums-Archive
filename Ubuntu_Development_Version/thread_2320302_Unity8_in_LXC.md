---
title: "Unity8 in LXC"
date: 2016-04-12
forum: Ubuntu Development Version
---

### Post by tajreed on 2016-04-12
What is the status in 16.04? I can't seem to get beyond the log-in screen. I know we are a long way from a final version but I'de sure like to see what it looks like at the moment.
I'm using a Lenovo laptop with the I5 processor and 4g of ram. Intel on-board video.

Thanks

---

### Post by grahammechanical on 2016-04-12
The same thing is happening to me. The Linux container is failing to load. I have also tried unity8-desktop-session-mir and that also does not go beyond the login screen. And before anyone asks, this is using the open source video driver - Nouveau. 

Both of these packages worked about 12 - 18 months ago but there was no development of Unity 8. Apps would not install because they were written for ARM CPUs & not x86. Unity8 on x86 became just a curiosity. And I gave up on it. And now when I try it is broken.

During the 15.10 development cycle I experimented with Ubuntu Personal (personal_x86.img). That installed & worked and it called itself "Snappy Ubuntu Desktop Next." It was built on Wily code and received transactional updates that rolled back if the update to the OS failed. New images were built daily. It was an interesting experiment but that was all it was. I say experiment because once 15.10 was released no further images were built. Development did not move on the Xenial code.

I am kind of hoping that building Ubuntu Personal images will be restarted once 16.04 is released. It makes sense to develop this concept on stable LTS code rather than the changing development code. I have hopes for the next development cycle. But no hope for Unity8 in LXC or Unity8-desktop-session-mir. Nor, do I count on one day running snap apps on Unity 7. That also has been spoken of. That is just not possible at the moment on 16.04. May be in one year's time.

Regards.

---

### Post by tajreed on 2016-04-12
Thanks for the reply. I had hopes as the container seems to get updates almost every day. I thought that Unity8 was supposed to be an option under Ubuntu 16.10. Perhaps we'll see some action after the 16.1 dev cycle begins.

---

### Post by ventrical on 2016-04-12
You can look at this thread here :



[http://ubuntuforums.org/showthread.php?t=2312045&highlight=snappy+personal](http://ubuntuforums.org/showthread.php?t=2312045&highlight=snappy+personal)

and here:

[http://ubuntuforums.org/showthread.php?t=2286066&highlight=snappy+personal](http://ubuntuforums.org/showthread.php?t=2286066&highlight=snappy+personal)

regards..

---

### Post by ventrical on 2016-04-12
snappy_personal is suppossed to start up in May.

> 
[SIZE=2]On 01/02/16 11:40, Will Cooke wrote:
 > Hi Dale,
 >
 > Thanks for your emails.
 >
 > So we stopped the Snappy builds of the U8/Mir desktop around October last
 > year when it became clear that having the two options was confusing people,
 > also there was a pretty big bug which would result in your boot partition
 > being over-written if you tried to install the Snappy version alongside the
 > classic .deb based version.
 >
 > The decision was made to stop building the Snappy version while the bugs
 > were being ironed out.
 >
 > Right now we're all focusing on getting the LTS out in the best possible
 > shape we can, and so we will be rebooting the Snappy images work from the
 > beginning of the 16.10 cycle.  All the machinery is still in place to build
 > those images, so it won't be long before we see them being generated again.
 >
 > I'll let you know as soon as we flip the switch back on again.
 >
 > Cheers, Will
 >
 >

[/SIZE]

---

### Post by entw on 2016-04-30
I wanna try Unity8 on real hw, especially how it works with a touchscreen.

---

