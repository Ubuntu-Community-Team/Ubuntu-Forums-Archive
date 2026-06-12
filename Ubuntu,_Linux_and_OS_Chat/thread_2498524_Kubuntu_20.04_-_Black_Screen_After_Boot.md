---
title: "Kubuntu 20.04 - Black Screen After Boot"
date: 2024-06-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2024-06-17
Just loaded up Kubuntu 24.04, and got a black-screen after boot.

I was able to work-around this problem by removing "quiet splash" from the GRUB script.
I had to go to the boards to figure this out... took me a couple of hours.  Eventually I found something that helped.

Then, after I was able to boot, I had to remove it from the /etc/default/grub file and remove "quiet splash" from there as well.
Dirty fix.

However... I really am at a loss here... this is a major problem.  This isn't just a bug that causes an app or something to not work, it's the entirety of the OS.
Booting up to a black screen and not being able to use your OS at all is a MAJOR issue.

I guess I don't understand the bug-fixing and/or reporting.

Can someone explain why this hasn't been dealt with?  This is an LTS release... I mean, what gives?

---

### Post by Xian on 2024-06-17
There is an open bug report for this issue. 
You may want to subscribe for updates. 

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/2063983](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/2063983)

---

### Post by him610 on 2024-06-18
@Shibblet
> Can someone explain why this hasn't been dealt with? This is an LTS release... I mean, what gives?
The folks at Canonical and these Ubuntu Forum have been saying ever since 24.04 was released back in April it was not a finished product. They have also advised to wait until the first point release in August if you do not want to experience software bugs and glitches.

No software is perfect. The software development cycle is basically a series of product improvement efforts.

---

### Post by Shibblet on 2024-06-18
> **him610 said:**
> @Shibblet

The folks at Canonical and these Ubuntu Forum have been saying ever since 24.04 was released back in April it was not a finished product. They have also advised to wait until the first point release in August if you do not want to experience software bugs and glitches.

No software is perfect. The software development cycle is basically a series of product improvement efforts.

I'd rather it not be released if it's not finished.  Put a statement out saying that it's not ready for an LTS, and skip it...

---

