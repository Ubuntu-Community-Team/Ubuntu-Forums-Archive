---
title: "Dual boot Ubuntu and XP or run XP virtually in Ubuntu?"
date: 2009-11-21
forum: The Cafe
---

### Post by Happycamper374 on 2009-11-21
Hi all,

I'm currently dual booting 9.04 and XP on my college desktop that's six years old. I've had the same XP installation since I got the computer and I'd like to reinstall XP to speed things up as well as get rid of 6 years worth of random crap that I've accumulated. I'm trying to decide between continuing to dual boot or just running XP in Ubuntu with one of the virtualization programs. 

My girlfriend, the other main user of this computer, feels much more at home in XP and uses it for netflix, etc. Also, there are a few programs that I need windows for.

I've never set up a virtual machine before but am confident that I can do it. 

What do you all think? Dual boot or virtual machine in Ubuntu? Thoughts, pros and cons, anything?

---

### Post by myusername on 2009-11-21
> **Happycamper374 said:**
> Hi all,

I'm currently dual booting 9.04 and XP on my college desktop that's six years old. I've had the same XP installation since I got the computer and I'd like to reinstall XP to speed things up as well as get rid of 6 years worth of random crap that I've accumulated. I'm trying to decide between continuing to dual boot or just running XP in Ubuntu with one of the virtualization programs. 

My girlfriend, the other main user of this computer, feels much more at home in XP and uses it for netflix, etc. Also, there are a few programs that I need windows for.

I've never set up a virtual machine before but am confident that I can do it. 

What do you all think? Dual boot or virtual machine in Ubuntu? Thoughts, pros and cons, anything?


just dual boot. xp will be noticeably slower in a virtual machine

---

### Post by SunnyRabbiera on 2009-11-21
Dual boot is a good option, especially for beginners.

---

### Post by Happycamper374 on 2009-11-21
Ok, thanks.

---

### Post by Nerd King on 2009-11-21
Just one note of caution. When you reinstall windows it'll screw up grub. That means you'll not be able to see the boot up screen where you choose windows or linux. You'll need to reinstall grub therefore after installing windows, otherwise you'll have no way into your linux installation. Btw if you're just using windows for non-gaming things, you may find a virtualbox more straightforward, as you can just keep a clean image and whenever it gets messy you just revert to the clean one.

---

### Post by Nerd King on 2009-11-21
Regarding netflix.. what's the specific issue preventing linux use?

---

### Post by MasterNetra on 2009-11-22
How much ram and video memory does the computer have?

---

### Post by Warpnow on 2009-11-22
Win4Lin looks neat. Virtualizes in a window for each app so you can't tell its virtualizing. Might replace the need for full blown windows.

---

### Post by Nerd King on 2009-11-22
Interesting. You know Wine does a pretty decent job of running Windows apps right?

Edit: Win4Lin. Mostly doable with Virtualbox.

1. Go to virtualbox.org and get the .deb to install or add their repository and update, install virtualbox-3.0.
2. Create new virtual PC in virtualbox and install winXP/win7 on it (easy-peasy, follow the prompts)
3. Tools -> Install Guest Addons
4. Now you can do cool stuff. Seamless will put a windows taskbar and start menu at the bottom, put your apps in their own windows and allow you to create a shared folder for windows and linux to use together.

Security: I consider having a single shared folder to be safer than letting windows have any direct access to the linux filesystem, let's face it, windows aint the most secure OS out there. Hope that helps.

---

### Post by phrostbyte on 2009-11-22
If you have over 2 GB RAM and a recent processor (perf one with hardware virt support) I seriously recommend virtualizating it. Actually Windows XP runs excellent in Virtualbox ([[apt link]]("apt:virtualbox-ose")). Be sure to install Guest Additions after you install XP.

---

### Post by Nerd King on 2009-11-22
> **phrostbyte said:**
> If you have over 2 GB RAM and a recent processor (perf one with hardware virt support) I seriously recommend virtualizating it. Actually Windows XP runs excellent in Virtualbox ([[apt link]]("apt:virtualbox-ose")). Be sure to install Guest Additions after you install XP.
Yep, xp works just fine in vbox on my craptop (laptop that's crap = craptop).

---

### Post by Happycamper374 on 2009-11-22
Thanks for all the comments.

Yup, I'm aware that Windows will screw up GRUB. I encountered that when I installed Windows 7 RC on my laptop. 

My computer is a Pentium 4 2.8 GHz with 2 Gb ram and a 32 Mb NVidia graphics card. I dropped a pretty penny on it back in 2002 when I thought student loans were just free money. I've bumped up the ram to 2 Gb but not upgraded anything else.

Yup, I've tried wine with mixed results. I've installed Pokerstars and DVD Shrink with wine. They run, but I can't read any of the text. It looks like it gets all jumbled and has horizontal lines through it. I did some digging and I'm pretty sure it has something to do with my LCD monitor and the settings on Ubuntu. But it was taking quite a bit of time to figure out so I just decided to run those programs in windows. I love to tweak and mess with my computer just as much as the next guy, but it just wasn't a high priority.

As for netflix, it's the watch now feature that we like. We have no problems doing anything else on the site. I looked into a workaround for that a while ago and, at the time, there wasn't one. Maybe there is now?

I'll look into Win4Lin. 

Thanks again, you folks rock.

---

### Post by Warpnow on 2009-11-22
> **Nerd King said:**
> Interesting. You know Wine does a pretty decent job of running Windows apps right?

Edit: Win4Lin. Mostly doable with Virtualbox.

1. Go to virtualbox.org and get the .deb to install or add their repository and update, install virtualbox-3.0.
2. Create new virtual PC in virtualbox and install winXP/win7 on it (easy-peasy, follow the prompts)
3. Tools -> Install Guest Addons
4. Now you can do cool stuff. Seamless will put a windows taskbar and start menu at the bottom, put your apps in their own windows and allow you to create a shared folder for windows and linux to use together.

Security: I consider having a single shared folder to be safer than letting windows have any direct access to the linux filesystem, let's face it, windows aint the most secure OS out there. Hope that helps.

Virtualbox Seamless and Win4Lin aren't the same. Win4Lin lets you launch windows applications from the ubuntu menu. I think this is far superior to having 2 bars. Plus, VB seamless doesn't work well with compiz.

---

