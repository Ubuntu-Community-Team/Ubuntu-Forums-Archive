---
title: "Linux for the beginner"
date: 2009-10-03
forum: Testimonials &amp; Experiences
---

### Post by paulgertie on 2009-10-03
I thought I'd give ubuntu a try as the magazines  and online are saying linux is easier to use, they lied. I have another machine that has windows 2000 server on it, I originally installed it, it took a while to set itself up, but I plug things in and it works.  I thought I'd install ubuntu on this machine, installation was fairly quick, but there's not much I can do with it.
I mainly want to use this for storage, email and internet. I have plugged in 3 usb wireless network adapters, none are recognized. one is netgear, so I fired up my xp machine and went to look for drivers. Loaded the drivers onto an usb stick and plugged it into ubuntu machine, starts straight away and files show up, this is good, quicker than xp, read the installation file, it has something called configure, read this, doesn't seem to tell me what to do. I try clicking on different things in the download nothing happens. A text file says it assumes I have configured a source file, but says nothing about how or why to do this. There is nothing in ubuntu that I can see to tell me how to install anything, I start searching the internet on my xp machine and found the ubuntupocketguide, this proudly states that unlike windows ubuntu just works, well in my short experience it doesn't for this beginner. 
   All I want is a system that works, doing the limited amount of things I want to do. I ended up here, searched forums for a solution or at least pointing in the right direction, can't find it. That's how I ended up writng this, if I connect a devce to xp and it doesn't have the drivers I go find them and download and click setup.exe or install.exe and that's it and the 99% of the time it works. I would truly like an alternative to windows, but what I've read in the linux forums  says linux is a good system that works if you persevere with it and that's part of the fun, but I just want to use my computer and linux still doesn't appear to allow that.
Paul

---

### Post by NoaHall on 2009-10-03
Right, tell me what your network adapters are. Then we can work out what you need.
And you'll probably need the .inf file.

---

### Post by HomoGleek on 2009-10-03
I must have been very lucky, I have never installed a non-ms OS before, and Ubuntu was easy, and it just worked. Id say Ive had too install more drivers for XP than I have for Ubuntu.

---

### Post by Bucky Ball on 2009-10-03
I think you should read this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Sounds like you are trying to use Windows drivers on a Ubuntu OS. That is not going to work without some serious coaxing (if at all). Easier to just let us know specifically what you are trying to do and what's happening with as much detail as possible before saying Ubuntu is not this or that and making comparisons with windows (which are pointless as you'll figure if you read the link).

Post back with details of the USB wireless dongles you are trying to use. You can always research this by searching for the name of your dongles and adding Ubuntu like so:
> 
D-Link wireless adapter K510 Ubuntu

---

### Post by Paqman on 2009-10-03
Regarding USB wifi adaptors, make sure you have the latest version of Ubuntu. Support for these types of devices has improved considerably in the last year or two. Many now work without needing any drivers, you just plug 'em in and they work.

---

### Post by 3rdalbum on 2009-10-03
Ubuntu is easier to use than Windows, but it's different. So no, the magazines didn't lie.

You're quite unlucky to have three wireless devices and none supported out-of-the-box on Ubuntu; the majority of devices will just work, no need to install drivers.

In order to install a driver from source code, you need to install the "linux-headers-generic" and "build-essential" packages from Synaptic Package Manager. This requires some sort of internet connection, such as an Ethernet cable from your router, or mobile broadband. While you're at it, install the "nautilus-open-terminal" package.

Log out and log in again, to enable the "open-terminal" menu item. Now go into the directory where you extracted the archive and right-click somewhere in the empty part of the file browser window. Choose "Open In Terminal".

At the terminal prompt that appears, just type the following:

```
./configure
make
sudo make install
```

(the ./configure step is sometimes not necessary - if it tells you "no such file or directory", then forget it).

When that's all done, reboot and you'll have a wireless driver.

If you update your kernel, you will need to perform those three commands again.

See, that was pretty easy once you knew how to do it. What's easier still is to buy Linux-compatible hardware, just like how in 2007 you had to buy Vista-compatible hardware rather than just assume that everything would work; and in a couple of months time people will have to buy Windows 7-compatible hardware.

With a properly-supported Linux-compatible wireless dongle, you just plug it in and connect. I've got two in-built wireless cards and one external dongle, all work out-of-the-box on Ubuntu.

---

### Post by paulgertie on 2009-10-03
My thanks for the quick replies, I am away from my ubuntu machine at the moment, but will try some of the suggestions.
Bucky Ball - I downloaded the netgear linux drivers from their site, but cannot work out how to install them.
DarrenTod - I too have downloaded lots of drivers for xp, my arguement though is that with one click I can install them, but I still haven't been able to do it with ubuntu. I have no doubt I will get it to work, but it isn't as user friendly as touted.
Paqman - I have the latest ubuntu, downloaded yesterday, by the way I tried opensuse 11.1 first and couldn't get it to install, just stalled after about an hour 3 times.
3rdalbum - catch 22 there, I don't have an internet connection and can't get one until I install the packages, which  I can't do because I can only get the machine online wirelessly. I have no access to a wired router directly or mobile broadband, which given the fact the wireless adapter wont work does not bode well for mobile broadband anyway.

---

### Post by celticbhoy on 2009-10-03
First things first Paul, can you give the model number of your netgear dongle. I think we should concentrate on it to get you up and running.

---

### Post by Paqman on 2009-10-03
> **paulgertie said:**
> it isn't as user friendly as touted.


It is, except for one particluar situation: incompatible hardware. 

Hardware support is Linux's achille's heal. If you're unlucky enough to have hardware made by somebody that doesn't support Linux, then it can be the most frustrating OS in the world. But if your hardware works, it's great.

We've all been where you are at some point, so we feel your pain.

---

### Post by tarps87 on 2009-10-03
> **3rdalbum said:**
> ...
In order to install a driver from source code, you need to install the "linux-headers-generic" and "build-essential" packages from Synaptic Package Manager. This requires some sort of internet connection, such as an Ethernet cable from your router, or mobile broadband. While you're at it, install the "nautilus-open-terminal" package.
...

The build-essential package and I'm sure the linux-headers-generic package is on the Ubuntu cd, if you add the cd to you sources list you can install it using
```
sudo apt-get update && sudo apt-get install linux-headers-generic build-essential
```
To add the cd it is under system -> admin -> softare sources

---

### Post by paulgertie on 2009-10-03
celticbhoy - Netgear WG121, I can borrow this from my sons machine, as I say I picked up the  drivers from Netgear and when I connect it lights up the usb lamp. I won't be able to use this permanently, but I figured being well known  it should be easier to set up. The norm with xp is to show the device but be unable to set up with no drivers, but I cannot see it in ubuntu.
Thanks,  Paul

---

### Post by Bucky Ball on 2009-10-03
I suggest plugging an ethernet cable in and then plug in your dongle and see if you get a response while you are online. Sounds weird but just might work.

---

### Post by juancarlospaco on 2009-10-03
> **bucky ball said:**
> i suggest plugging an ethernet cable 

**+1**

---

### Post by tarps87 on 2009-10-03
> **paulgertie said:**
> celticbhoy - Netgear WG121, I can borrow this from my sons machine, as I say I picked up the  drivers from Netgear and when I connect it lights up the usb lamp. I won't be able to use this permanently, but I figured being well known  it should be easier to set up. The norm with xp is to show the device but be unable to set up with no drivers, but I cannot see it in ubuntu.
Thanks,  Paul

As it is a USB device this will show the device
```
lsusb[code]
Also can you try this command it confirm it in not working
[code]iwconfig
```

If you add the cd to you sources list I believe ndiswrapper is on it too. Search in add/remove for it and ndis-gtk, then all you need is the windows driver.

This thread may help too
[http://ubuntuforums.org/showthread.php?t=263168](http://ubuntuforums.org/showthread.php?t=263168)

The problem not really down to popularity of the device, it's more that some hardware companies just don't write drivers for Linux and that means people have to reverse engineer the drivers

---

### Post by 3rdalbum on 2009-10-03
The only reason why you can "double-click" on a driver installer on Windows is not because of anything Windows does; it's because hardware manufacturers make binary installers for their drivers on Windows, but they often don't bother to make the equivalent on Linux.

Not Linux's fault, and as I've mentioned, it's possible and easy to build or buy a computer that will be supported in Linux out-of-the-box. The ease-of-setup on such a machine will be much better than Windows. On a machine where the wireless doesn't work out-of-the-box, the setup is not much more difficult than on Windows anyway; it's just different.

Most people aren't in the unusual situation of being able to access wifi signals, but not the router where they came from.

---

### Post by celticbhoy on 2009-10-03
> **paulgertie said:**
> celticbhoy - Netgear WG121, I can borrow this from my sons machine, as I say I picked up the  drivers from Netgear and when I connect it lights up the usb lamp. I won't be able to use this permanently, but I figured being well known  it should be easier to set up. The norm with xp is to show the device but be unable to set up with no drivers, but I cannot see it in ubuntu.
Thanks,  Paul

As this is only a borrowed dongle, what is the dongle manufacturer and model number of the one you want to use permanently?

If you waste time setting up the Netgear, you will just have to do it all again for new one.

---

### Post by paulgertie on 2009-10-04
Thanks to all of you, I think I am making progress, especially [tarps87]("http://ubuntuforums.org/member.php?u=605890") for his advice to add cd to source file. This has enabled me to add the drivers for the Azurewave USB wireless adapter I will be using. Unfortunately ubuntu doesn't seem to recognize it's connected to the PC, it recognizes and I can use my USB stick straight away, it's how I got the drivers in. Is there something I need to do to get it recognized, the drivers are in and just need to activate.
Again thanks for your help, Paul

---

### Post by halitech on 2009-10-04
with the wireless adapter plugged in, can you open the terminal and run
```
lsusb
```
and post the results back here

---

### Post by cariboo on 2009-10-04
I would suggest starting a thread in [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336"). All of the op's posts are in this thread, he hasn't asked for help with his problem.

---

### Post by satishbhawra46 on 2009-10-05
I thought I'd give ubuntu a try as the magazines and online are saying linux is easier to use, they lied. I have another machine that has windows 2000 server on it, I originally installed it, it took a while to set itself up, but I plug things in and it works.

---

### Post by Bucky Ball on 2009-10-06
> **satishbhawra46 said:**
> I thought I'd give ubuntu a try as the magazines and online are saying linux is easier to use, they lied. I have another machine that has windows 2000 server on it, I originally installed it, it took a while to set itself up, but I plug things in and it works.

Simple, use Windows.

---

### Post by running_rabbit07 on 2009-10-06
Ask for help?

---

