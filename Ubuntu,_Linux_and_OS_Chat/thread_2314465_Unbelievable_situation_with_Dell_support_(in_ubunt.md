---
title: "Unbelievable situation with Dell support (in ubuntu-preinstalled) laptops"
date: 2016-02-21
forum: Ubuntu, Linux and OS Chat
---

### Post by chefarov2 on 2016-02-21
First of all I don't know if this is the right section for this post. I searched through the forum categories but I didn't find something looking more appropriate.

I recently bought a brand new Dell Latitude e5550 with Ubuntu 14.04 preinstalled. I am using linux for the past 10 years and I never had such a pain to get a system working. The specs included Intel Core i5-5200U and Intel Graphics HD 5500 and because Ubuntu was also preinstalled I thought nothing could go wrong, but I was mistaken. Thus I would like to share my experience in order to help other people that are interested buying a linux compatible laptop to avoid making the same mistake. 

First of all out of the box:
1) Wlan (intel wireless 7265) was constantly disconnecting from every wireless network I tried.
2) After hibernate, the laptop wouldn't recover. Hard reset the only option.
3) After some days USB was not detected either!

Thus I decided to install ubuntu 15.10. Then I came up with the following situation:
The laptop booted in dell recovery (which by the way wouldn't work even with the recovery iso in USB!). I fixed this using boot-repair tool through live-USB
Then when I finally booted I couldn't reboot again because of [#1488719 bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1488719")
thus I was forced to downgrade to 3.13.0-36 generic. The problem is that Wireless 7265 won't work with older than 3.18-rc1 kernel as mentioned [here]("http://ubuntuforums.org/showthread.php?t=2242147&page=2")

That's the short story how I ended up without working PC. The thing that made me write this post is that by calling Dell support, the tech guy told me that 
"We don't know a lot of things about Linux. We support it at a very basic level" !!!! And he suggested I recover to factory state (which is impossible as I explained above).

Thus I would like to warn anyone thinking that buying a Dell laptop with preinstalled ubuntu is a good idea... to reconsider!

---

### Post by oldfred on 2016-02-21
My Dell SFF just worked, but it did not have the Intel wi-fi. And my system was Haswell and I installed 15.10, and now also dual boot with 16.04. So distribution was a couple of version after release of hardware.

But generally with Linux you need to use the newer, not an older kernel or support software.
And with a New Intel chip, you need the newest version of Ubuntu and may need to update from that to newer kernel & drivers.

Intel is pretty good about supporting Linux, but it writes updates, they have to get included in the Kernel and then included in a distribution. Or with new hardware, full support may be a version of two away because of timing.

And Dell typically was better about its own updates. With 12.04 it released Sputnik with extra drivers to make system work. And by 14.04 all those updates were included in the standard distribution.

I might suggest creating another 25GB / (root) partition, just as a test and install 16.04.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1451246](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1451246)

---

