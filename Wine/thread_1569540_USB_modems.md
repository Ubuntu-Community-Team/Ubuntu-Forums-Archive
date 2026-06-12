---
title: "USB modems"
date: 2010-09-06
forum: Wine
---

### Post by Fableflame on 2010-09-06
So my mom has a laptop that is running Ubuntu 10.4.
She doesn't live within range of any hotspots and they don't have internet where they live, they don't even have a computer besides her laptop.
She asked me if one of those USB plugins that connects your laptop to the internet would work on Linux, because she knows that they are made for using on Windows.
My question is, can I use WINE to use one of these USB wireless modems?

---

### Post by linux18 on 2010-09-06
Usually, if the device doesn't require driver installation it will work flawlessly on linux via usb. "made for windows" is just an advertising slogan. If in doubt, google the device name + linux and see what pops up.

---

### Post by Fableflame on 2010-09-07
What if it installs a driver?
Can I use WINE to make it work?

---

### Post by xzinkx on 2010-09-07
I don't think you can use wine to run modem drivers designed for windows under linux in order to establish a successful internet connection as that would require extensive use of the windows registry which wine provides little if any support for at all. Not to mention it would also require ubuntu to be able to communicate with wine in ways that just arn't possible yet.

Your best bet would be just to simply bite the bullet and buy the usb modem, plug it into the laptop and hope that it is autodetected and autoinstalled; which it will most likely be as ubuntu has great support for a vast amount of hardware. 

Put it this way, I installed lucid lynx on my acer 5930g laptop and everything worked perfectly straight from the disc. I was browsing the internet via wifi within 2 minutes, even the one touch email access and internet access buttons that I thought had very little chance of working on an operating system they weren't designed for work perfectly as if it was still windows. The driver that needed downloading from the internet was for my nvidia gfx card and again, ubuntu automatically located the correct driver for me.

Just my 2 cents. :D

---

### Post by Hobgoblin on 2010-09-07
I have a couple of USB 3G sticks which work with Ubuntu 10.04 straight away.

One required the stick to be plugged in before booting but that's all.

If you can find the model number of the modem then either google it with "Linux" or search the forum for the model number to see if there are any users reporting problems.

---

