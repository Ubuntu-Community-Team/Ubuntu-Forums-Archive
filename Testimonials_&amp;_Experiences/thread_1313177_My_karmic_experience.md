---
title: "My karmic experience"
date: 2009-11-03
forum: Testimonials &amp; Experiences
---

### Post by Viva on 2009-11-03
When interprid came out, I did not upgrade or install it because Hardy was so damn good. This time though, curiosity got the better out of me, even though Jaunty was the best OS I've used. So, I wiped out my current installation completely and installed Karmic. This is the first time I've used a live cd to install an OS, I've always preferred the alternate install because it is faster.

My install experience:
I booted to the live cd and my first impressions were good. It told me that one of my hard drives is corrupt. I decided to proceed to the install anyway, because I won't be installing on that particular drive. I have to say, the install was much much slower compared to the alternate CD. In the middle of the install process, the desktop dropped into screensaver mode. It really freaked me out because I thought something went wrong when I saw the black screen. I think the live cd should not drop into the screensaver mode or turn off the monitor automatically.

Karmic experience:
I loaded karmic after the installation and the first impressions were again good. The like the look of the new grub and the boot screen. The screen was flickering a lot, but I thought it was the power supply. The desktop theme is much improved too. Then started my problems. I could not connect to the internet. I tried everything I could, I checked the logs, asked for help on these forums and on IRC. I found out that it is a bug with the network manager that hasn't been fixed since before the release. I used pppoeconf to connect to my DSL, added the network manager daily repos and updated the network manager. I still could not connect, it gave me an insufficient privileges error whenever I tried to edit my dsl connection. I removed the connection and readded it, only with the "available to all users" box unchecked this time. No more network manager problems since then. 

The screen is still flickering and with some research, it can be fixed too. I remember when I installed Jaunty, a few people on this board had problems with it, but for me, it was near-perfect and I rarely experienced any problems. I guess it is my turn now. No OS is perfect, and somebody will have problems after every release.

I have a few suggestions
1. No automatic screensaver in the live CD
2. The bugs with the network manager should be high priority during the testing process because you need to connect to the internet to download bug fixes
3. The human theme has improved a lot, but the controls are still too large for my liking. I'm glad they included more themes and backgrounds in karmic though

---

### Post by Viva on 2009-11-05
Update: The flickering problem is caused by my power supply, not ubuntu#-o

---

### Post by stinger30au on 2009-11-05
> **Viva said:**
> Update: The flickering problem is caused by my power supply, not ubuntu#-o


thanks for reporting that back

im sure theres many issues that have been reported that people have claimed to be ubuntu fault and it isnt, its the hardware

---

