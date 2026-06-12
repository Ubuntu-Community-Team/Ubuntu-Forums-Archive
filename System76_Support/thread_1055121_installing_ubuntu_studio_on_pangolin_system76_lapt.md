---
title: "installing ubuntu studio on pangolin system76 laptop"
date: 2009-01-30
forum: System76 Support
---

### Post by bbrace on 2009-01-30
I wish ubuntu studio came already installed on system 76 computers -- (linux has always frustrated the bejesus out of me!) I'm considering purchasing the pangolin laptop but won't if it's going to be another expensive headache -- are there any problems installing ubuntu studio? Should I be using a different flavor of studio? Can I order the machine with a partion for ubuntu studio? (Does anyone sell computers will studio pre-installled?)   tia /:brad

---

### Post by thomasaaron on 2009-01-30
I spoke to this gentleman on the phone and explained to him that we do not install Ubuntu Studio.

Are there any 76ers out there who have given Studio a spin? If so, what is involved with getting it up and running?

Also, we image with a separate home partition that can be shrunk to create a new partition for Studio. I can walk you through that process when you're ready. It's very simple.

---

### Post by MorphWVUtuba on 2009-01-30
I've never had ANY trouble with adding UbuntuStudio on ANY Ubuntu machine, S76 or otherwise.  I think all the way back to the previous LTS 6.06, it's been included in the official Ubuntu repos.

SO.  On to the steak & taters:

```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

( Pulled from [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy) )

If you don't want something, like the video apps, just remove "ubuntustudio-video" from the command.  

The linux-rt loads the low-latency, real-time kernel to your computer.  This allows for better performance in audio/video capturing/processing.

You have to reboot & select this at the GRUB menu to utilize, and you may want to change the amount of time GRUB is displayed.  Since my machine is a dual-boot with Windows, I have "timeout 60" to give me a minute to change the option.  Change it to whatever # of seconds you wish, but I have a tendency to wander off & miss it before it boots into whatever the default option is.  Anywayz...

THAT.  IS.  IT.

ENJOY!!!:popcorn:

---

### Post by bbrace on 2009-01-30
ok thanks; it may be possible to install but...
do all the ubuntu studio applications function correctly?

/:b


> **MorphWVUtuba said:**
> I've never had ANY trouble with adding UbuntuStudio on ANY Ubuntu machine, S76 or otherwise.  I think all the way back to the previous LTS 6.06, it's been included in the official Ubuntu repos.

SO.  On to the steak & taters:

```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

( Pulled from [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy) )

If you don't want something, like the video apps, just remove "ubuntustudio-video" from the command.  

The linux-rt loads the low-latency, real-time kernel to your computer.  This allows for better performance in audio/video capturing/processing.

You have to reboot & select this at the GRUB menu to utilize, and you may want to change the amount of time GRUB is displayed.  Since my machine is a dual-boot with Windows, I have "timeout 60" to give me a minute to change the option.  Change it to whatever # of seconds you wish, but I have a tendency to wander off & miss it before it boots into whatever the default option is.  Anywayz...

THAT.  IS.  IT.

ENJOY!!!:popcorn:

---

### Post by MorphWVUtuba on 2009-01-31
I haven't used the JACK applications, because I'm too much of a n00b to know how to set it up.  But I do know everything else works.  I think at one time the rt kernel didn't allow me to connect to wireless, but if I remember correctly that's not the case anymore.  

<strike>Have you purchased a machine already or is this just part of your evaluation?  Cuz if you've got one, you could always try a livecd.</strike>  If there's something specific you'd like to know about, I'd be happy to test it for you on my Serval Pro.

---

### Post by bbrace on 2009-01-31
> **MorphWVUtuba said:**
> I haven't used the JACK applications, because I'm too much of a n00b to know how to set it up.  But I do know everything else works.  I think at one time the rt kernel didn't allow me to connect to wireless, but if I remember correctly that's not the case anymore.  

<strike>Have you purchased a machine already or is this just part of your evaluation?  Cuz if you've got one, you could always try a livecd.</strike>  If there's something specific you'd like to know about, I'd be happy to test it for you on my Serval Pro.

thanks very much! this is reassuring ;)
I'm ready to buy the Pangolin -- hopefully it will behave like your Serval
does installing studio replace all of ubuntu?
(would it make sense to keep both on partions?)

/:brad

---

### Post by MorphWVUtuba on 2009-01-31
> **bbrace said:**
> thanks very much! this is reassuring ;)
I'm ready to buy the Pangolin -- hopefully it will behave like your Serval
does installing studio replace all of ubuntu?
(would it make sense to keep both on partions?)

/:brad

This is what I love about package managers in Linux & Ubuntu specifically.  You can install this on a separate partition using a livecd, replace the default ubuntu desktop, or just pick & choose which elements you want from synaptic!

I just have the audio & video packages installed, (see screenshot).  I did install the graphics applications, but I removed all mono-based apps to keep at least my Ubuntu partition ms-free.

---

### Post by bbrace on 2009-02-20
OK I've purchased the Pangolin and installed UbuntuStudio on a separate partition -- the wireless connection doesn't work or very slowly -- I also installed Network Manager, which only appears in the taskbar, allowing me to see that I'm connected to my wireless network, but something's still wrong... (no wireless problems with plain Ubuntu on the other partition)

I'd appreciate any suggestions!

(if there are other tweaks needed, please tell!)

tia, /:brad

---

### Post by bbrace on 2009-02-20
> **bbrace said:**
> OK I've purchased the Pangolin and installed UbuntuStudio on a separate partition -- the wireless connection doesn't work or very slowly -- I also installed Network Manager, which only appears in the taskbar, allowing me to see that I'm connected to my wireless network, but something's still wrong... (no wireless problems with plain Ubuntu on the other partition)

I'd appreciate any suggestions!

(if there are other tweaks needed, please tell!)

tia, /:brad

Tom @ system76 quickly provided this remedy:

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).   





Best Regards,
Tom Aaron
System 76 Technical Support

---

