---
title: "UNR on Toshiba NB200 takes extremely long time to boot"
date: 2010-07-08
forum: Ubuntu Moblin Remix
---

### Post by dsingh83 on 2010-07-08
I recently purchased a Toshiba NB200 Netbook with winXP pre-installed. I wanted to dual boot linux so I installed Ubuntu Netbook Remix on a different partition on the same drive. The installation went smoothly, however the problem I am having is that when I boot into Linux, there is almost a 5 minute delay before the login prompt appears. This is not just some of the time, this is all the time. Windows boots up fine without problems. This problem only exists when I try to boot into Linux (version 10.4) I have installed all upgrade packages and have been looking for a reason/solution but have not found anyone else with this issue yet. Sometimes it doesn't boot up at all no matter how long I wait. During the wait there is a black screen with a single blinking cursor in the top left corner. Once loaded, everything works properly and smoothly (except I only get sound with headphones, not through the speakers - have not looked for a solution to this yet but if someone has a link that would save me time :).

I have tried deleting the partition and reinstalling UNR from scratch, however that does not seem to solve the problem. It's getting frustrating having to wait 5-10 minutes just to boot into my OS. Any suggestions?

---

### Post by cariboo on 2010-07-10
Could you install bootchart, it is in the repositories, and add it to your next post. the png is located in /var/log/bootchart. Please use one of the image sharing services like  [http://imgur.com/](http://imgur.com/), as the forum reduces the size of the to the point where it is unreadable.

---

### Post by dsingh83 on 2010-07-11
> **cariboo907 said:**
> Could you install bootchart, it is in the repositories, and add it to your next post. the png is located in /var/log/bootchart. Please use one of the image sharing services like [http://imgur.com/](http://imgur.com/), as the forum reduces the size of the to the point where it is unreadable.
 
 
Ok I installed bootchart and rebooted my netbook. At first it failed to restart, but when I did a hard reset, the boot time is suddenly a lot shorter now that bootchart is running. There's still a delay but now it's more like 1-2 minutes instead of 5-10. Nevertheless, I booted the netbook twice and here are the resulting png's from both boots
 
First boot:
[http://imgur.com/0dMtm.png](http://imgur.com/0dMtm.png)
 
Second boot:
[http://imgur.com/YAzdv.png](http://imgur.com/YAzdv.png)

---

