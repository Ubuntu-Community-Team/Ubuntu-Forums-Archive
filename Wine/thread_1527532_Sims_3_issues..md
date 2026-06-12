---
title: "Sims 3 issues.?"
date: 2010-07-09
forum: Wine
---

### Post by Cinycyde on 2010-07-09
I've installed the Sims 3 on Ubuntu 8.04. I can hear it but there's no video. I can't get it to work on just WINE so I'm trying to play it on PlayONLinux. 

Why isn't the video working.? Also, when I click fullscreen it shows a bunch of green and blue lines...

---

### Post by Calash on 2010-07-09
Check the WineDB entry, there is some information there that may help.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664)

PlayOnLinux is just a front-end for Wine.  It does a good job but in the end you still have to deal with Wine to get things working.

Another resource is the Wine sub-forum here.

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by The Flying Penguin on 2010-07-09
What graphics card do you have? Check the first link Calash posted. Bug 18948 may shed some light on your situation if you are using an Intel card. It seems other users have had a similar problem to yours on some Intel cards.

Also, what version of Wine are you using? Perhaps a newer/different version may help.

---

### Post by philinux on 2010-07-09
Moved to Wine.

---

### Post by Cinycyde on 2010-07-09
I have an ATI Radeon Xpress 1100 I think.? The Sims runs fine on Windows, so I know the card is supported.

---

### Post by The Flying Penguin on 2010-07-09
Well, working and being supported are two different things. That card is not listed as a supported card for The Sims 3 [www.thesims3.com/game/systemreq](www.thesims3.com/game/systemreq)

I understand it may work in Windows but that is the cards ideal environment since that is where the manufacturer put the most focus so the card is more likely to be functioning to its fullest. Sometimes some features don't work under Linux even when there is a proprietary driver available. Speaking of proprietary drivers, ATI does't even offer a recent driver for that card for Linux. I believe 8.04 is actually the last current version of Ubuntu that can even use the proprietary drivers for that card. Someone correct me if I'm wrong but that card is now legacy and thus ATI will not be releasing any drivers for it that work under new kernel versions.

Are you using the ATI proprietary driver? IMO, enabling it would be the best starting point if you haven't already done so.

And how much memory does that card have? I know it uses hypermemory which means it actually borrows memory from your RAM. The card itself has extremely limited memory, certainly not enough to run the Sims 3. It's possible that hypermemory may not be functioning correctly under Ubuntu with your current configuration resulting in an inadequate amount of memory. Again, enabling the proprietary driver would be your best bet as I'm not sure if the other drivers available will work with hypermemory.

Btw, is this the integrated or pci version?

And here are the specs for your card: [www.vivian.amd.com/us-en/Processors/ProductInformation/0,,30_118_14603_14612%5E14615,00.html](www.vivian.amd.com/us-en/Processors/ProductInformation/0,,30_118_14603_14612%5E14615,00.html)

EDIT: I would most definitely turn off compiz and leave it off while making any attempt to play this game. Compiz can really cause problems when gaming, especially on a low horsepower card like the X1100.

---

### Post by Cinycyde on 2010-07-09
The card has 128mb I think.? I'm not exactly sure as I don't know much about computers or Ubuntu... so I'm definitely confused now. What's IMO.? I am totally new to this stuff. At first, The Sims 3 would load and it would play the loading video, but it was upside down and it was also black and white. I reinstalled Ubuntu, and it isn't showing anything at all now, and just flickers quite a bit. I really have no idea what to do... I noticed that it wasn't supported... does that mean that it wont work with my laptop.?



It says that ATI Accelerated Graphics Driver is a Proprietary driver being used... and that 3D Acceleration is enabled. I don't understand this stuff, really.

---

### Post by Calash on 2010-07-09
IMO = In My Opinion.  


Can you open a terminal and type the following

```

wine --version

```

You said you were running 8.04 and I want to make sure you at least have the latest version of Wine before we go farther.

On a side note, any reason why you have not upgraded from 8.04?

---

### Post by The Flying Penguin on 2010-07-09
IMO= In my oppinion.

Perhaps you were using the proprietary driver before. On a fresh install, Ubuntu defaults to using the open source driver which I do not believe offers full 3D support for your card. I know it it didn't for my Radeon X1270 which is also legacy. Make sure the proprietary driver is activated. I believe you go to System - Hardware and drivers. You should be presented with an option to activate the proprietary driver. Do so and then restart.

I can't remember 100% if that is how you get there or not. I'm posting on my smartphone right now. Give me a few minutes and I'll get on my laptop and double check for you.

Oh, when I say proprietary driver I mean the driver provided by the manufacturer, in this case ATI.

---

### Post by Calash on 2010-07-09
It is System -> Administration -> Hardware Drivers :)

Or you can open a terminal or run prompt (ctrl+F2) and type

```

jockey-gtk

```

---

### Post by The Flying Penguin on 2010-07-09
> **Calash said:**
> 

On a side note, any reason why you have not upgraded from 8.04?

The proprietary driver for his card won't work under current versions of Ubuntu do to changes in the kernel. He would have to use the open source driver which from my experience with my legacy X1270, lacks any real 3d support. Sticking to 8.04 is his best bet to get the full potential out of his card.

Correct me if I'm wrong though, I am still learning Linux myself.

---

### Post by Cinycyde on 2010-07-09
I'm running 8.04 because this laptop has a bit of a hard drive flaw, and actually will not install anything but this. It doesn't accept any type of Windows, Kubuntu, or Ubuntu 10. 


The version is wine-1.1.42

There's only two things in the Hardware Drivers and that is ATI Accelerated, and Ethernet.. that's it. And they both have a check. I don't exactly know what Compiz is either, though.

---

### Post by The Flying Penguin on 2010-07-09
Compiz is desktop effects. Go to System > Preferences > Appearance and under the Visual Effects tab select none.

Let's make sure fglrx (the ATI Linux driver I've been talking about) is working correctly.

Go to a terminal and type:
```
fglrxinfo
```then post the results.

And the latest version of Wine is 1.2-rc7. It's not a stable release but I've been running the development releases exclusively over the last few months and have had great results.

Unfortunately, the Wine site is only showing packages for 9.10 and newer. Perhaps someone here can fill us in on whether or not you can go ahead and use those packages or if there are any available for 8.04? Can the latest Wine even run on 8.04 without issues? Is compiling from source the only option for older Ubuntu releases?

EDIT: And what is this "hard drive flaw" that prevents you from installing any OS other then 8.04? Frankly, even if you could get a newer Ubuntu installed, I'd keep running 8.04 for as long as possible since it works with the proprietary driver.

To be honest, I'm really skeptical you are going to get acceptable performance even if you do get the game working. You say the game works fine under Windows but then you say you can't install any other OS including Windows on your laptop. So am I understanding correct that you haven't successfully played the game under Windows on this hardware but on another machine?

EDIT AGAIN: I keep thinking of things after I post lol. You could also try installing the ATI Catalyst Control Center (CCC). You can find it through Synaptic package manager. Perhaps there are some useful settings that may help tweak the card enough to get the game working.

---

### Post by Cinycyde on 2010-07-09
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

is what popped up.


The flaw is the laptop can't be moved, at all. It has to sit in one spot, or it turns off and gives an error that the hard disk can't be read, and it has a media test failure and things like that. A guy told me that it was the Hard Drive. It says that the files can't be read on anything but Ubuntu 8.04. It's the only thing that manages to work.

And I've installed the Sims 3 and played it many times on this laptop. It's recently gotten worse to where it will not reinstall Windows [used to have to every 2-3 start ups.] That's my issue now.


After changing the Appearance Effects to none [I don't know if this is what improved it], but the screen has stopped flickering and the cursor shows up. Not a lot changed, though.

---

### Post by The Flying Penguin on 2010-07-09
Well, it looks like fglrx is working correctly based on what you posted.

Did you try installing CCC? 9.3 is the last version that will work with legacy cards such as yours. If the one in Synaptic won't work because it's a newer version you can download CCC plus the display driver from ATI at: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English)

I'm not sure if it will give you the option to just install CCC or if you will have to install the display driver along with it. If you have to install the display driver too I think you will want to remove fglrx before installing the package from ATI's site. To do this in terminal type:
```
sudo apt-get remove fglrx
```Now BEFORE you do this, I would wait for another member to confirm that this will not give you any problems after rebooting. I think you should be able to run in low graphics mode until you install from the link I gave you. I'd just hate for you to reboot and end up having to use terminal to fix things. I know how scary that is when your first learning Linux.

And as far as your hard drive issue. When you say it shuts off when you move it, do you mean just the hard drive or the whole laptop? Since your having hard drive and media test failures (you mean the test you run on a live cd?), I'm almost thinking you may just have a loose or damaged cable. I have a desktop that would only boot after several attempts. I kept getting a no disk error after the BIOS. Laying it on its side and/or banging the side of the case would resolve the problem. When I finally decided to open up the case I found that my SATA cable (the cable that goes from the hard drive to motherboard) was damage. I put on a new cable and I've had no problems since.

I don't know if you feel confident opening it up or not to find out but frankly I wouldn't even be using that laptop until you solve that issue first unless you plan on not storing any important data.

---

### Post by Cinycyde on 2010-07-09
I can't install the thing on the link, because it says incorrect encoding.? And it says that I don't have fglrx when I put that in the terminal. 

The Laptop basically if it moves in anyway the computer in Windows just used to Blue Screen and turn off, and when I turned it back on it would say "fixed disc" and "media test failure" something about PXE and PCI Fast Ethernet Controller I believe. I did actually take the laptop's cover off and look, but nothing seems to be unhooked.? I also don't even know where the hard drive is... the laptop used to work perfectly fine when it was tilted/propped up, but if it was laying flat it would blue screen. With Linux, it hardly ever happens. The screen sort of turns white and restarts. 

I don't know exactly what fglrx is. I installed something earlier called ATI Catalyst Control Center. I believe that is it.?

---

### Post by The Flying Penguin on 2010-07-09
Hmmm. ATI Radeon Xpress Series is listed. Are you 32 or 64 bit?

Fill in the details and download [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

What is your laptop's make/model? Maybe the manufacturer has a Linux driver for your card.

And regarding your fixed disc and media test failure messages, I would say to check in your BIOS boot order and make sure the hard drive is set to boot before the network card. I'd set your optical drive first, then hard drive, and then network card.

---

### Post by asdfoo on 2010-07-09
sounds like the connection on the hard drive is loose, might be worth taking the laptop apart to check that it's secure (it might have cracked or broken)

---

