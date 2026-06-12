---
title: "How does an OS which supports the most hardware end up"
date: 2007-07-06
forum: The Cafe
---

### Post by tehkain on 2007-07-06
....being known for its lack of drivers. I understand the fact that we write our own, and that it takes time. So newer hardware is not supported off the bat. Is this just a misfact that continues to be spread because of the few people who try ubuntu and find their windows(driver creator biased) specific hardware unsupported? How did we get branded as not supporting anything when we infact support more out of the box then windows will ever support with all the worlds DLLs? Also, Why are people blind to the fact that windows comes with zero drivers?

I assume too most people it does not matter that our OS can run on over 15 times more CPU types, but does it tweak your mind like it does mine when you hear that 'Linux doesnt support any hardware'?

---

### Post by Istonian on 2007-07-06
People do not know what they are talking about. They are so quick to bash linux when they have had no experience with it.

---

### Post by tgalati4 on 2007-07-06
For desktop use, things like sound, video, USB, bluetooth, etc become important.  It's true that Linux supports a lot of CPU/Disk/Memory architectures, but its the desktop goodies that are only partially supported.

In Windows, at least you can find a driver.  In Linux, if your hardware isn't detected, then you just can't use it.  You can get better performance with some custom-written drivers in Linux, but on the whole, if Linux can't detect your hardware then you are out of luck.

---

### Post by prizrak on 2007-07-06
It's mostly based on the fact that Windows is either already preinstalled on a computer or installed by someone who knows what their doing and have all the drivers on hand. When such people come to Linux they are either completely lost because they never had to configure their own OS and as such have no idea of what actually comes with it or know Windows so well that any other way is completely foreign to them. There is a huge number of drivers that at are not part of the Ubuntu (or other distro) kernel tree and they are all installable. Problem is that with Windows those who know to install the driver also know where to get it. With Ubuntu/Linux it's not necessarily as straightforward.

---

### Post by brim4brim on 2007-07-06
Its just ignorance.  Most of the Computer Science Graduates I know that never reinstalled windows don't know how this fact.  Don't ask me how they've never had to reinstall windows since you always end up doing it for a friend or something at some point.

Windows has really bad driver support.  Even a lot of the drivers for devices aren't good because everyone has to write their own.

Of course a lot of features aren't implemented on Linux drivers especially hardware specific features.

However the fact that there are more drivers for Windows no matter how badly written and the fact that they are installed by vendors for users gives the illusion of better driver support in Windows.

As someone else said, its not about them being included, its about them being installed for the user.  The user thinks they were there when Windows was installed.  Thats what is importnat.  It doesn't matter if they are bad drivers for windows, they exist.   That's what Linux needs.  Drivers for almost all hardware.

---

### Post by jrusso2 on 2007-07-06
Devices that are less then a year old often don't have support in Linux yet.  This means people installing on new computers are going to have problems.

Also, a lot of peripheral devices like video camera's don't have drivers.

Wireless continues to be a problem.

Although its true that windows also has the same problems at least often the mfg will provide people a windows driver with the device.

---

### Post by laxmanb on 2007-07-06
Windows supports all my Hardware/I can install drivers easily enough. Linux plain and simple doesn't. And installing linux drivers is a pain. An OS that has 95% share of the desktop OS market is the first priority of device manufacturers. Given that proprietary drivers can't legally interface with the linux kernel isn't good either. 

PS: If you write your own drivers, good for you. but I can guarantee 99% of computer users can't. So basically, nobody writes their own drivers.

---

### Post by prizrak on 2007-07-06
> **laxmanb said:**
> Windows supports all my Hardware/I can install drivers easily enough. An OS that has 95% share of the desktop OS market is the first priority of device manufacturers.

Try installing Vista on an nVidia based machine and tell me if you can easily find the driver or if the OS supports your card enough ;) As you have said it's about the vendor support. 
> 
Linux plain and simple doesn't. And installing linux drivers is a pain. 

That's somewhat true but it's getting better lately. nVidia driver is no problem with Synaptic and I have installed a driver for special buttons on my keyboard that was nothing more than a simple .deb file and required a double click and telling the kernel to load it at start up, which requires putting the name into a text file, like a 10 second process.
> 
 Given that proprietary drivers can't legally interface with the linux kernel isn't good either. 

Proprietary drivers can legally interface with the kernel, where did you hear that they cannot? They cannot be legally integrated into the kernel and then distributed. They can interface as much as they want and as long as you do not distribute them as part of the kernel you would not be violating the GPL. This is why Ubuntu, among others, allows you to easily install an nVidia driver from the repos as opposed to including it out of the box. 
> 
PS: If you write your own drivers, good for you. but I can guarantee 99% of computer users can't. So basically, nobody writes their own drivers.
Not really true, in FLOSS users are often times developers as well and they will release the driver. Like that French hacker who wrote the driver for 235 webcams.

One possible solution that I can see is for a central driver repository to be maintained by a distro independent body. They could host compiled drivers for the major distributions as well as the source (for the open ones) for anyone to use. This could remedy the problem with kernel differences between some distros where hardware works on one and does not on the other. It could also help hardware manufacturers get their drivers into distros if they don't want to open them up/wait for them to get into the kernel tree.

---

### Post by Warpnow on 2007-07-06
Well, lets see...when I first installed linux...the following things stopped working:

1. My keyboard
2. My Mouse
3. My Graphics Card
4. One of My DVD burners
5. My Sound Card
6. My WINtv card
7. My Wireless Card
8. My SD card reader
9. My Printer
10. My Video Camera

all of which worked 100% out of the box in windows...so I don't think its "misfact" but rather people seeing linux not work with their stuff ;)

---

### Post by Warpnow on 2007-07-06
In fact, I am STILL unable to run ubuntu on my main pc (though I run it on 2 others) because my wireless keyboard, which works in the frickin bios, stops working when ubuntu boots. Why should something that works in the bios stop working in ubuntu? It makes no sense...

---

### Post by prizrak on 2007-07-06
> **Warpnow said:**
>  	Well, lets see...when I first installed linux...the following things stopped working:

1. My keyboard
2. My Mouse
3. My Graphics Card
4. One of My DVD burners
5. My Sound Card
6. My WINtv card
7. My Wireless Card
8. My SD card reader
9. My Printer
10. My Video Camera

all of which worked 100% out of the box in windows...so I don't think its "misfact" but rather people seeing linux not work with their stuff 
Well that's the thing, it's very individual. For me Ubuntu works 100% out of the box on a clean install (well 99.9% since I do have to install a third party hotkey driver) and Windows requires a couple of hours of installing drivers. That said, out of the box (here I mean clean install not a recovery CD/DVD) Ubuntu and just about any other Linux will support alot more hardware than Windows. Windows however will have a third party driver for pretty much anything you could buy making it more compatible. 

It's more like a misnomer than a misfact, it's not the OS that has to support the hardware it's the hardware that has to support the OS. 
> **Warpnow said:**
> In fact, I am STILL unable to run ubuntu on my main pc (though I run it on 2 others) because my wireless keyboard, which works in the frickin bios, stops working when ubuntu boots. Why should something that works in the bios stop working in ubuntu? It makes no sense...

That IS weird and I think might be a bug. Did you create a support thread for that? If you didn't I suggest you try there may be some random setting that needs tweaking.

---

### Post by moffatt666 on 2007-07-06
It's different for everybody.  Ubuntu supports all my hardware and peripherals out of the box with the exception of the forward and back buttons on my mouse which it interprets as right click and fast-scroll for some reason although these did work under Mandriva.

---

### Post by NBCChimes on 2007-07-13
> **moffatt666 said:**
> It's different for everybody.  Ubuntu supports all my hardware and peripherals out of the box with the exception of the forward and back buttons on my mouse which it interprets as right click and fast-scroll for some reason although these did work under Mandriva.

Do you need to have all peripherals connected when you initially  install Ubuntu for it to recognize them, or is there a way to make Ubuntu recognize them later?

---

### Post by tgalati4 on 2007-07-13
Sometimes yes, sometimes no.  An iPod is usually detected.  An external USB drive that you put /home on would need to be plugged in all the time, otherwise Linux goes wonky.  Some hardware like video cams are better supported when plugged in so that resources can be allocated.  When plugged in later, those resources may not be available.  The web cam may work but at slower rates because it can lock the DMA channel.

Only testing can really answer that question.  If you have some unusual piece of hardware, then search the forums for tips on installing.

---

### Post by user1397 on 2007-07-13
> **prizrak said:**
> 

One possible solution that I can see is for a central driver repository to be maintained by a distro independent body. They could host compiled drivers for the major distributions as well as the source (for the open ones) for anyone to use. This could remedy the problem with kernel differences between some distros where hardware works on one and does not on the other. It could also help hardware manufacturers get their drivers into distros if they don't want to open them up/wait for them to get into the kernel tree.Hmmm...I've never thought of that before...did you just think of that? or is it one of your old ideas that's been lingering for a while?

Now that I think about it, the more it makes sense.  What's stopping people from making such a repo as this?

---

### Post by EdThaSlayer on 2007-07-13
They are scared of the great slumbering beast that is linux, which unlike windows, comes with batteries included(just changed a python slogan).

---

