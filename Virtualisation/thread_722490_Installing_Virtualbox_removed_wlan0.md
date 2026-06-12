---
title: "Installing Virtualbox removed wlan0"
date: 2008-03-12
forum: Virtualisation
---

### Post by gronbaek on 2008-03-12
Hi everybody.

I installed VirtualBox-OSE today, and the gave me a couple of problems. I normally use the generic kernel, but apparently VirtualBox required the 386 kernel. I didn't notice that, so I just went on with the installation.
After installation and reboot, my wireless interface wlan0 disappeared, and I couldn't get it back. Using lshw -C network showed the card, an Intel PRO/Wireless 4965, but there was no way to bring it up.

The solution was to use the generic kernel again. But I only figured that it was a kernel problem, when powertop suddenly reported that CONFIG_NO_HZ was disabled, and I spent a good deal of time searching these forums before that.

I haven't figured out what I need to do, to get the card working with the 386 kernel yet, but I'm guessing it's not so hard.
My biggest problem was more along the lines that it was kind of annoying that it just stopped working, and I had no idea why. So hopefully other people searching the Net will find this post, and figure it out faster than me... :)

---

