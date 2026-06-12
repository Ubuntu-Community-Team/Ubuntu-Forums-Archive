---
title: "Why can't smartphones processors be used for computers?"
date: 2014-12-05
forum: The Cafe
---

### Post by kccv42 on 2014-12-05
Why can't smartphones processors be used for computers? They are smalll light weight and power effeicent. Desktops and latops have big bulky motherboards and processors.

---

### Post by pqwoerituytrueiwoq on 2014-12-05
performance
different architecture

---

### Post by grahammechanical on 2014-12-05
Except for the small matter of $20 million 40,000 people would now be using Ubuntu smartphones that would also become a PC when connected to a monitor, keyboard and mouse.

> [COLOR=#252525][FONT=sans-serif]The Edge was designed as a hybrid device, which would function as a high-end smartphone (with both [/FONT][/COLOR][Ubuntu Touch]("http://en.wikipedia.org/wiki/Ubuntu_Touch")[COLOR=#252525][FONT=sans-serif] and [/FONT][/COLOR][Android]("http://en.wikipedia.org/wiki/Android_(operating_system)")[COLOR=#252525][FONT=sans-serif]), or&#8212;when used with a monitor, keyboard and mouse&#8212;be able to operate as a conventional desktop PC running [/FONT][/COLOR][Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_(operating_system)")[COLOR=#252525][FONT=sans-serif].[/FONT][/COLOR][SUP][[2]]("http://en.wikipedia.org/wiki/Ubuntu_Edge#cite_note-BBC-2")[/SUP][COLOR=#252525][FONT=sans-serif] The Ubuntu Edge was also designed to support dual boot, and was to run along with Android.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Ubuntu_Edge](http://en.wikipedia.org/wiki/Ubuntu_Edge)

The dream has not died. First, we need Ubuntu phones on the market. Then Ubuntu tablets on the market. And then the convergence of Ubuntu for phones and tablets with Ubuntu for desktops and laptops and maybe, just maybe we may also get the kind of Ubuntu smartphone that the Ubuntu Edge was imagined to be.

Regards.

---

### Post by eight.coffee.beans on 2014-12-05
> **grahammechanical said:**
> Except for the small matter of $20 million 40,000 people would now be using Ubuntu smartphones that would also become a PC when connected to a monitor, keyboard and mouse.



[http://en.wikipedia.org/wiki/Ubuntu_Edge](http://en.wikipedia.org/wiki/Ubuntu_Edge)

The dream has not died. First, we need Ubuntu phones on the market. Then Ubuntu tablets on the market. And then the convergence of Ubuntu for phones and tablets with Ubuntu for desktops and laptops and maybe, just maybe we may also get the kind of Ubuntu smartphone that the Ubuntu Edge was imagined to be.

Regards.

Amen to that!

To get back on the topic: the main reason is in the architecture of the processor where it has lesser I/O and number of registers. :)

---

### Post by buzzingrobot on 2014-12-06
There's also the fact that the Windows/Mac/Linux universe has been rooted in the x86 architecture and codeset for a very long time. A new processor could have all sorts of amazing capabilities, but the world runs on x86. Mundane factors -- money -- would have a big impact on adoption of the new architecture.

---

### Post by PondPuppy on 2014-12-07
Geez. I've been poking around a bit on this topic. Most of you probably know this already...

Most Android and iOS tablets (and Windows RT ones) use ARM processors, and not Intel or AMD x86 processors. ARM chips use less power (= longer battery life) and produce less heat (= no cooling fan needed). But the instruction set is different from x86, so ARM processors can't run x86 applications or operating systems right right out. Different architectures, as noted by pqwoerituytrueiwoq.

However, it appears that an x86 machine can run software written for ARM, as long as any ARM-specific instructions are captured and translated correctly in the code. (Do I  have that right??)

That said, Intel's Atom processors are giving ARM a run for their place in mobile devices. Again, Atom are less power-hungry chips and produce less heat than i3 or i5: suitable for battery-operated, fanless mobile devices. My understanding -- someone correct me if I'm wrong -- is that Atom uses the ISA-standard x86 instruction set. Given a compatible chipset, then, Atom processors should be able to run Ubuntu 64-bit or any other standard operating system. I think.

And so I'm with grahammechanical -- hasten the day when my Ubuntu PC will fit in my jacket pocket.

I'm way outside my area of expertise, though, so take these comments with a bit of salt.




[URL="http://ubuntuforums.org/member.php?u=865458"]
[/URL]

---

### Post by ssam on 2014-12-07
There are plenty of small arm single board computers that work ok as desktop computers.
* raspberrypi [http://www.raspberrypi.org/](http://www.raspberrypi.org/)
* beaglebone [http://beagleboard.org/](http://beagleboard.org/)
* Hummingboard [http://www.solid-run.com/products/](http://www.solid-run.com/products/)
* UDOO [http://www.udoo.org/](http://www.udoo.org/)

---

### Post by Bucky Ball on 2014-12-07
I use an Odroid. Many call it a glorified smartphone without the screen:

[http://www.hardkernel.com/main/main.php](http://www.hardkernel.com/main/main.php)

I have the U3 running Lubuntu and XBMC. Love it. ;)

When you mention 'smartphone processors', do you mean ARM processors or something else? My bold prediction is that within the next decade or so we will see ARM processors in place of where we currently see Intels and AMD.

---

### Post by mastablasta on 2014-12-08
> **PondPuppy said:**
> 
That said, Intel's Atom processors are giving ARM a run for their place in mobile devices. Again, Atom are less power-hungry chips and produce less heat than i3 or i5: suitable for battery-operated, fanless mobile devices. My understanding -- someone correct me if I'm wrong -- is that Atom uses the ISA-standard x86 instruction set. Given a compatible chipset, then, Atom processors should be able to run Ubuntu 64-bit or any other standard operating system. I think.


problem is they need more power to be used as phone CPU. Phones /phablets/ tables with atoms inside have genraly much lower work time compared to ARM devices.

---

### Post by kccv42 on 2014-12-09
So the ARM processors can't handle windows?

---

### Post by pqwoerituytrueiwoq on 2014-12-09
> **kccv42 said:**
> So the ARM processors can't handle windows?
yes and no.
There is windows 8 RT that can
but windows is useless without multiple 3ed parts applications, which are well only offered in 32bit, it is very hard to find 64bit versions i don't even want to imagine looking for something for armv7
unless it can execute 32bit binary blobs, nobody is going to consider it for quite a few years for anything other than a toy

---

### Post by Linuxratty on 2014-12-10
Ok,hijacking the thread a bit. Do ARM devices work the same way secure boot does? In other words,are they locked down so the user can not interact with them,such as changing the os?

---

### Post by PondPuppy on 2014-12-10
No, ARM are not locked down generically. It's just a processor, and AFAIK there is no hardware lockdown.

Rooting an Android device is, essentially, unlocking the OS. You can also install custom operating systems on an ARM device -- CyanogenMod, Xylon, ParanoidAndroid, etc. But because different manufacturers use different chipsets and drivers, this is far from a one-size-fits-all endeavor. For example, this site -- [http://rootmyandroid.org/best-custom-roms-top-custom-rom-2014.html](http://rootmyandroid.org/best-custom-roms-top-custom-rom-2014.html) -- lists some popular custom ROMs for phones, and you'll note that each is followed by a list of specific devices that are known to run the ROM successfully.

---

### Post by pqwoerituytrueiwoq on 2014-12-10
think about running a custom os on these arm chips like flashing a router with ddwrt
you need a minimalist system without bloat for your specific hardware

---

### Post by kccv42 on 2014-12-11
Can ARM be used for gaming in the future? For example, like ps4 or xbox One.

---

### Post by pqwoerituytrueiwoq on 2014-12-11
@kcc42 google retropie
there are more powerful products that the raspberry pi now that can handle more intensive games/system
[http://www.phoronix.com/scan.php?page=news_item&px=MTg1OTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTg1OTQ)
not sure of you were referring to emulation or future consoles, either way they do exist in one form or another

---

### Post by kccv42 on 2014-12-12
I looked at the link you provided. Is there any of them that have aleast two gb of ram. I would perfer that because ubuntu runs better with more ram. Also does the device you showed me have wifi capabitlies?

---

### Post by pqwoerituytrueiwoq on 2014-12-12
this is not a arm system, but it is small and has 2gb ram
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883220572](http://www.newegg.com/Product/Product.aspx?Item=N82E16883220572)

iv never has a issues with xubuntu on 1gb ram, ther is also lubuntu

---

### Post by kccv42 on 2014-12-12
So does ubuntu run fine on 1gb of ram. How abotu lubuntu?

---

### Post by pqwoerituytrueiwoq on 2014-12-12
lubuntu will run ok with 512mb ram, for Xubuntu 1gb is highly recommended

the only hardware that i have that i could test ubuntu with 1gb ram around here are Pentium 4 system which lack the necessary GPU power to run the os

---

### Post by kccv42 on 2014-12-12
I know the pentium 4 processor isn't the best processor. In addition the celeron isn't any better. Where you impress with the performance of xbunutu?

---

### Post by pqwoerituytrueiwoq on 2014-12-12
the GPU on a haswell celeron is far superior on that you get on the motherboard of a Pentium 4 compatible motherboard
i ahve used xubuntu on a old pentium 4 (2.8Ghz) systems with 1gb ram and it flies cranking out 1080p on the integrated video (until you want some bloated adobe flash crud running)
i currently use xubuntu for the customizability
only time i have had issues with xubuntu and speed is on a system with 512mb ram

---

### Post by kccv42 on 2014-12-13
Well ram with 512mb is unrealistic today becuase computers now are coming with 8gb now.

---

### Post by Bucky Ball on 2014-12-14
> **kccv42 said:**
> I looked at the link you provided. Is there any of them that have aleast two gb of ram. I would perfer that because ubuntu runs better with more ram. Also does the device you showed me have wifi capabitlies?

Did you look at the Odroid? [The U3 ]("http://www.hardkernel.com/main/products/prdt_info.php?g_code=G138745696275")has 2Gb of RAM, and so do some of the other models. That link says Ubuntu 13.10 and Android, but there are 14.04 images available. Runs Lubuntu fine. Will probably be installing just XBMC in the near future cos we only really use it for that, although being able to search the net with Firefox is sometimes handy.

Have a Raspberry Pi which I was using as a media server running Xbmc previously. Also worked fine for that purpose with 1Gb RAM.

---

### Post by Jamsheed_Nabi on 2014-12-19
Probably because of different architecture.

---

### Post by Mike_Walsh on 2014-12-20
> **kccv42 said:**
> I know the pentium 4 processor isn't the best processor. In addition the celeron isn't any better. Where you impress with the performance of xbunutu?

You have to remember, the Pentium 4 was smokin' hot stuff in its day. Okay, 10 years or more down the line, they ARE slow compared to modern hardware, like the Ivy Bridge and Haswell 'Core' architecture.....but they are still very capable processors; if you link them with a discrete graphics card.....then they will happily run Xubuntu and Lubuntu. I'm not so sure whether the lack of SSE3s would hamper them with running Ubuntu, because of the 3D requirements of Unity. Probably not, because any halfway decent graphics card would be able to cope with 3D acceleration.

Besides my big ol' Compaq Presario, I'm running an ancient Dell Inspiron lappie, an original 1100 from 2002....it, too, was fitted with a Celeron until very recently; it's just been replaced with a 2.6 GHz P4.....which has improved its performance no end. Back when the 1100 was on the market, 'mobile' processors really were in their infancy, and most laptops were fitted with 'desktop' CPUs; the battery pack alone on this thing weighs more than a MacBook 'Air'. But then, it DOES have to supply the nearly 17 volts that would have normally been supplied by a mains PSU...

Regards,

Mike.

---

