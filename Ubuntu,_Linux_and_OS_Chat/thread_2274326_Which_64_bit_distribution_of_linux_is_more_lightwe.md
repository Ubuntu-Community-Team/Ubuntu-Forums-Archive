---
title: "Which 64 bit distribution of linux is more lightweight ?????"
date: 2015-04-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Grippy_Man on 2015-04-19
Hi, Could anyone tell me what is best lightweight distrubition having the 64bit color.....I wanted to use for laptop i5 which has 2GB graphics, I want both faster and 64bit colors.

---

### Post by mattharris4 on 2015-04-19
I don't know what you mean by "64 bit color" but if you mean version Lubuntu (the lightest Canonical OS, runs on about 1GB of RAM) works fine on my 64 bit laptop.  In trials using a USB stick Xubuntu (not much more RAM and processor intensive than Lubuntu, uses about 1.3GB of RAM in my tests) and Ubuntu (or Edubuntu -- you would need at least 3GB of RAM to run either one) also booted up fine.  However, assuming you have at least 4GB of RAM with that i5 processor and 2GB graphics (it is 99.9% likely you do, especially with a 2GB graphics card) the concern is are all of your parts supported in whatever distro you wish to use.  This is mainly a concern with very recently released computers and computers with Nvidia parts (the guy who originally created Linux has some harsh profanities he sends their way in lectures).  Another concern is will your UEFI allow you to install a Linux distro without reprogramming part of the UEFI (instructions are available but explaining computer programming is way beyond my knowledge).  This is a big issue with new HP computers, some Toshiba users are also starting to report issues (although my year-old Toshiba took a Lubuntu/Win dual-boot just fine, it came with Win 8.1 and a UEFI).  It would help if you would post with the manufacturer and model of computer you are dealing with here.  In general if the drivers are in the OS these specs (along with at least 4GB of RAM) will allow you to run any Canonical OS, actually the video card and i5 processor you cite are overkill but the latter will serve to future-proof the computer.

Obviously if the computer is custom built by a computer shop (or you are asking in order to tell them what you want) you should have (or should) told (tell) them of your plans to install Linux and they should have (or should) take(n) that into account in their parts selection.  If that is the case and you aren't a gamer or doing video editing for some movie producer you certainly don't need such a fancy video card either.  If you are a gamer do your research carefully if you don't also install Windows on the computer.  This is definitely second and third hand info but gamers say that many games do not come in a Linux version, some won't work with Windows emulation either using the Windows version.  Also, for future-proofing your computer I do suggest if you are having a computer built you go for 8GB of RAM, it is only $50 more or so and will save you grief in five years time.  If you can still afford an i5 processor along with that extra RAM that will go a long way toward future-proofing your computer for years to come as well.  So will installing USB 3.0 ports.

---

### Post by Bucky Ball on 2015-04-20
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Lubuntu. Xubuntu next. Why not download the ISO, burn install media, boot from it and try them both out? 

I personally go for a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") and only add what I want (xfce4 desktop environment to start with). Very fast.

---

### Post by brian62 on 2015-04-20
What are you trying to achieve? If you are thinking that you'll get better "performance" by switching to a distribution that is some how "faster", you are confused about how Linux distributions work.

---

### Post by grahammechanical on 2015-04-20
The hardware makes a lot of difference. I am sure that If I upgrade my video adapter that has 1 GB of its own memory with one that has 2 GB of memory then I must surely see an improvement. But then again maybe not. This old computer already works faster than I can think.  A newer video adapter would also have a more powerful GPU. But the OS would be the same.

All Linux distributions of a similar age will have the same Linux kernel. And it is the Linux kernel that makes a difference and not the distribution. Another factor is the Video driver.

If you are thinking of High Definition video playback, then I am reminded of some television advertisements that I have seen on the better quality of the very latest HD TV screens. But I am watching these ads on a very old CTR TV, So, it is all a bit pointless do you not think?

We also need a monitor that can deliver the viewing quality we desire.

Regards.

---

### Post by Tar_Ni on 2015-04-20
What's the amount of RAM? Just asking but with a i5 processor and a 2GB graphic card you can use vitually any Linux desktop environment in the Ubuntu family and expect *excellent *performance.. It will be fast and responsive, trust me. Apparently you have top-notch specs for running a Linux system with Unity, Gnome or KDE.

I'll have to agree with Bucky Ball, if you want a OS without bells and whistles than you could use a lightweight flavor of Ubuntu if that's what you really want.. You might want to try Lubuntu 14.04 or Xubuntu 14.04 -- both 64 bit in this case. Though bear in mind that your computer can handle way more.

---

### Post by gordintoronto on 2015-04-21
Ubuntu Mate is also a possibility. I am running it on a netbook which was the slowest computer you could buy -- six years ago.

---

### Post by monkeybrain20122 on 2015-04-21
If you have > 2G's of ram it doesn't matter light weight or not light weight assuming normal use. You need 'light weight' only because you don't want the DE to be hogging resources which could be used for other things, but if resource is abundant the amount used by the DE becomes relatively insignificant. On a laptop with, e.g 4G of ram (pretty standard these days) I can see no difference between lubuntu and Ubuntu in terms of speed.

---

### Post by monkeybrain20122 on 2015-04-21
> **gordintoronto said:**
> Ubuntu Mate is also a possibility. I am running it on a netbook which was the slowest computer you could buy -- six years ago.

Well I cannot see how Mate would qualify as 'light weight' if your netbook is as weak as you said. Mate = gnome2 and it wasn't that light on weak or old hardware. Before gnome 2 was killed people who needed a light DE for the kind of netbook you described would go for xfce, lxde or even openbox.  :) But if your netbook has > 1G of ram it is probably not as bad as you made it out to be. :)

---

### Post by gordintoronto on 2015-04-22
After booting, with a weather applet running, Conky reports that 196 MB of memory (out of 1 GB) are being used by Mate. That's less than Xubuntu on the same system.

If I play a video in VLC which must be scaled to display on the small screen, CPU usage goes to 100% and frames are dropped. On the plus side, I have never seen the CPU temperature go as high as 50 C. It's a really "cool" little computer. [smile]

---

### Post by lisati on 2015-04-22
> **grahammechanical said:**
> 
If you are thinking of High Definition video playback, then I am reminded of some television advertisements that I have seen on the better quality of the very latest HD TV screens. But I am watching these ads on a very old CTR TV, So, it is all a bit pointless do you not think?


I am reminded of the early days of colour TV with many people watching advertisements for colour TVs on older B&W sets! :D

---

### Post by enricobe on 2015-04-23
I have the same PC (i5, 2gb video, 4gb ram) and i'm happy with Xubuntu. 
Ubuntu works fine too, but I wanted a "light" distro which is really complete. Lubuntu is lighter, but still lacks of some functions that Xubuntu and Ubuntu have (e.g. quick search from "Start"). I think that Xubuntu is the best balanced distro for my needs, but Unity is a great DE too.

---

### Post by kurt18947 on 2015-04-23
> **gordintoronto said:**
> Ubuntu Mate is also a possibility. I am running it on a netbook which was the slowest computer you could buy -- six years ago.

Ubuntu Mate is interesting. I installed Mate 64 bit 15.04 beta on a Core2Duo machine with 3 GB RAM. It was using 300 MB. with Firefox open 1 tab. I tried to install it on a netbook that is currently running Xubuntu to compare them. The netbook would not boot either USB or DVD. I didn't spend time troubleshooting it. I suspect a video issue because of where it failed in the boot process but I'm not sure.

---

### Post by mattharris4 on 2015-04-27
> **brian62 said:**
> What are you trying to achieve? If you are thinking that you'll get better "performance" by switching to a distribution that is some how "faster", you are confused about how Linux distributions work.

In the OP's case there would probably not be much performance difference between Lubuntu and Ubuntu.  However, with a power saver processor such as the AMD E1-2100 1.0GHz processor which is slower and less capable I found Lubuntu was faster and worked more smoothly than the heavier distributions even though the computer has 4GB of RAM.

Also, some may prefer the look and feel of one of the lighter OSes to Ubuntu's Unity, finding them easier to use.  I find Unity to be harder to use as the icons do not have the name of the program under them, the other Canonical OSes do once you create the icon.  Yes, you do need to create the icon in Lubuntu and Xubuntu from the list menu but I find that easy to do.  Edubuntu also has two Gnome options that are easier to use than Unity if someone does not like the latter and still want some feature of Ubuntu as Edubuntu is essentially Ubuntu with other programs and options.

---

### Post by vtpoet2 on 2015-04-27
I'm also not sure of what you mean by "64bit color". My first response would be to say that color depth has nothing whatsoever to do with 32 vs 64 bit OS's -- but then I'm always getting my comeuppance with some little geeky nicety that I know nothing about.

Beyond that, if your system only has 2 Gigs of RAM (you didn't say), then using a 64 bit OS is 'just about' pointless. Use a 32-bit option. It will use less CPU and memory -- making it lighter weight and more responsive. Physical Address Extension will get you up to 3 Gigs (I think).

I personally have a 64bit desktop that I rescued, but with only has 2 Gigs of RAM. I run 32-bit [Voyager]("http://voyager.legtux.org/") on it. Relatively lightweight, a distro based on Xubuntu and with lovely customizations.

---

### Post by DanielWEWO on 2015-04-27
The answer to OP's question would be Lubuntu 64-bit. As has already been stated, but I do believe he is slightly confused as to what he is asking. Virtually any graphics card you could find these days would handle full color, though I'm not sure what he means by "64-bit" color. The version 64-bit vs 32-bit is not directly related to the color palette, but to the size of instructions and memory that the CPU can handle. If you have an i5, you have a 64-bit computer. What you really need to know is how much "System Memory" you have, not how much "Graphical Memory" you have. If you have 2GB of graphical memory, you are going to be able to run your games at a higher resolution/quality. Other than that, anything with 128MB of memory should be sufficient for most if not all daily tasks. If you have a 2GB graphics card, I wouldn't be surprised if you have 8GB of memory. I'm sure you have at least 4. You would be fine running almost any flavor of Ubuntu or GNU/Linux.

---

