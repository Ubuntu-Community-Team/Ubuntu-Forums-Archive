---
title: "Ubuntu Studio 12.04 install problem"
date: 2012-06-07
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2012-06-07
Ok, so I do recall posting a thread of the same issue a couple of days ago, but I couldn't seem to find it, so here it is again. 

I am having a huge problem installing Ubuntu Studio 12.04 on my PC. It is important to mention that my PC already has Windows 7 Home Premium installed, and I have made a separate partition on the hard drive for what I am trying to accomplish.  

I have made multiple DVD's in both formats (i386 and amd64) at different speeds. Please keep in mind I would prefer to have a the 64-bit version. 

So, when I made one of the many DVD's I have gotten the same exact result: I make my computer boot from the DVD drive first, and a black screen appears with a small flashing line in the top left hand corner of the screen. The light flashes a few times, then screen turns black and boots to windows. 

Now for those who are saying install it from a USB, here is the issue that I have been having with that: I have my computer boot to the USB, it brings up the menu, I choose install, it brings me to the point that I need to connect to my wireless Internet (and no I do not have the option of hard wiring it), and It says there is an error, to log it, and the screens become gray and blank, then tell me to try install via the Live portion and freezes again. Now when I try and install in Live, I get the same issue at the same point.

So as you can see I've tried multiple things and I have ran out of ideas. If anyone as ANYTHING to contribute, please feel free to let me know. Like I said I would really prefer to have install of the 64-bit version of Ubuntu Studio 12.04.

Thanks ahead of time for your help.

---

### Post by jejeman on 2012-06-07
No need for usb, dvd is fine.
1. check the integrity of the dvd. In boot menu choose "test dvd..."
2. let's make things clear: does live dvd starts to the end - Desktop enviroment loads completly?
3. You can find your posts and threads in your user page, just click on your name and go to statistics.
4. If you have 64bit cpu, there is no reason why you would not install 64bit Ubuntu. Unless you  have only <=2GB of RAM, then 64bit is not good choice.

---

### Post by MrBalloonHands on 2012-06-07
I can not get anywhere with the DVD. I get the issue of the back screen with the blinking line. I can however get the menu with the USB. So I do not know any other way to check the integrity of the disc. Did I mentioned that I have made 3 discs? 2 at 16x (both i386) and 1 at 8x (amd64). 

Thanks for your input.

---

### Post by jejeman on 2012-06-07
Did you set to boot from dvd in BIOS?
Did you test the downloaded iso files?

---

### Post by MrBalloonHands on 2012-06-07
Yes, I can boot from DVD. I can boot from a Windows Recovery Disk also burnt. 
How do I check the iso?

---

### Post by Totalchaos on 2012-06-07
Here is an idea. Try booting the dvd once again but this time, when the boot starts to going nowhere ;) press ctrl+alt+f2 or ctrl+alt+f1 if this switches to console mode, than the problem is probably video related. The usual command for switching from console mode to graphics mode is "startx" .To reboot press ctrl+alt+delete 
:confused:

---

### Post by jejeman on 2012-06-07
Here are intructions for iso check, see the windows section
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If you downloaded iso via torrent, then you don't need to check.

---

### Post by MrBalloonHands on 2012-06-07
Ok, thanks. I won't be able to check until I get home. Any ideas if the results come back fine? Anything I can look for after that?

---

### Post by jejeman on 2012-06-07
If graphics gives you problem, than you should try boot options. Mainly nomodeset option.

---

### Post by MrBalloonHands on 2012-06-10
Hey guys just wanted to let you know how I made out. To be completely honest none of the suggestions worked, and I tried all of them. I ended up having to install it via a live usb AND the dvd at the same time. It was really weird, one could not work without the other. But it's all good now cause I'm typing this from my newly installed Ubuntu Studio. 

Thanks for all your help,

-Nate

---

### Post by webweave on 2012-08-03
I have a similar sounding problem with Ubuntu Studio 12.04

I'm running Ubuntu 12.04 but I want to try Ubuntu Studio 12.04

I've downloaded the torrent and the version on the download page and burnt both to DVD, I've done the check sum routine and its okay, I've made USB stick/SD memory and USB and Firewire hard drive media from "startup disk creator", I've checked and toyed with the BIOS startup disk settings and I still get the same message.

The first things that pops up on the screen after the bios is "boot error" in very basic terminal type and when I hit any key its goes to the next device until it finds my disk with the regular version of 12.04

Its an Intel mother board and a core duo with 4G or ram.

Any ideas?

Thanks,
Brian

---

### Post by uzumakifahim on 2012-08-04
> **webweave said:**
> I have a similar sounding problem with Ubuntu Studio 12.04

I'm running Ubuntu 12.04 but I want to try Ubuntu Studio 12.04

I've downloaded the torrent and the version on the download page and burnt both to DVD, I've done the check sum routine and its okay, I've made USB stick/SD memory and USB and Firewire hard drive media from "startup disk creator", I've checked and toyed with the BIOS startup disk settings and I still get the same message.

The first things that pops up on the screen after the bios is "boot error" in very basic terminal type and when I hit any key its goes to the next device until it finds my disk with the regular version of 12.04

Its an Intel mother board and a core duo with 4G or ram.

Any ideas?

Thanks,
Brian

May be the problem is with "startup disk creator". Sometimes, I've the same problem with "startup disk creator". Try with "Unetbootin". Hope this will help you to get positive result.

---

### Post by webweave on 2012-08-05
> **uzumakifahim said:**
> May be the problem is with "startup disk creator". Sometimes, I've the same problem with "startup disk creator". Try with "Unetbootin". Hope this will help you to get positive result.

No joy. Tried unetbootin using two different memory sticks and two different downloads, same result.

[FONT="Courier New"]Boot error
_[/FONT]

I didn't think that was it because I made two DVDs and that does not use startup disk creator.

---

### Post by cfhowlett on 2012-08-06
> **webweave said:**
> I have a similar sounding problem with Ubuntu Studio 12.04

I'm running Ubuntu 12.04 but I want to try Ubuntu Studio 12.04

I've downloaded the torrent and the version on the download page and burnt both to DVD, I've done the check sum routine and its okay, I've made USB stick/SD memory and USB and Firewire hard drive media from "startup disk creator", I've checked and toyed with the BIOS startup disk settings and I still get the same message.

The first things that pops up on the screen after the bios is "boot error" in very basic terminal type and when I hit any key its goes to the next device until it finds my disk with the regular version of 12.04

Its an Intel mother board and a core duo with 4G or ram.

Any ideas?

Thanks,
Brian

Brian: as you've already installed ubuntu, just upgrade that to ubuntustudio.  

See "Upgrading From Ubuntu"  [https://help.ubuntu.com/community/UbuntuStudio/InstallingUbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio/InstallingUbuntuStudio)

---

### Post by webweave on 2012-08-09
> **cfhowlett said:**
> Brian: as you've already installed ubuntu, just upgrade that to ubuntustudio.  

See "Upgrading From Ubuntu"  [https://help.ubuntu.com/community/UbuntuStudio/InstallingUbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio/InstallingUbuntuStudio)

Yea I guess that will work, keyword being work as it sure will take a lot of work to do that, its going to take me a few days but I'll try it. I was thinking I found a bug with this distro and my mobo. Took my DVD to another computer (dell P4) and everything worked all right, sure is a pretty OS. It sure is odd that one distro fails to boot on one machine but every other combination works?

---

