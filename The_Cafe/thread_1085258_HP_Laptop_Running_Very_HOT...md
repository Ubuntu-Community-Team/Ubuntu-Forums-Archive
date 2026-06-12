---
title: "HP Laptop Running Very HOT.."
date: 2009-03-02
forum: The Cafe
---

### Post by Reaper29 on 2009-03-02
im new to linux, im actually running Mint 6 x64bit (was running Ubuntu 8.10, but was alittle to hard for me). i was directed here to see if maybe anyone can help me. i have an HP DV2610us, and my laptop runs extreamly hot. i have lm-sensors installed, and my cpu temps at this very moment are:
matt@DV2610us ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +98.0°C  (crit = +120.0°C)                  
temp2:       +87.0°C  (crit = +120.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +81.0°C                                    
Core0 Temp:  +77.0°C                                    
Core1 Temp:  +81.0°C                                    
Core1 Temp:  +77.0°C 

i know this has to be WAY WAY to hot. my fan does not even come on, and i know it works cause it was just working fine in Vista. Any suggestions?

---

### Post by Gramps on 2009-03-02
On my Dells I have to install and run gkrellm and a plugin for Dells you may just need gkrellm
```
sudo apt-get install gkrellm
```

my cpu temp runs about 33[SIZE="2"]O[/SIZE]C goes into the 40's with heavy activity. I start gkrellm on startup so I don't have to remember to start it each time.

---

### Post by Reaper29 on 2009-03-02
> **Gramps said:**
> On my Dells I have to install and run gkrellm and a plugin for Dells you may just need gkrellm
```
sudo apt-get install gkrellm
```

my cpu temp runs about 33[SIZE="2"]O[/SIZE]C goes into the 40's with heavy activity. I start gkrellm on startup so I don't have to remember to start it each time.

i thought gkrellm was just a system monitor?

---

### Post by miegiel on 2009-03-02
Personally I don't trust the k8temp-pci-00c3 sensor readout. Here's my machine's sensors output

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +19.0°C                                    
Core0 Temp:  +20.0°C                                    
Core1 Temp:  +17.0°C                                    
Core1 Temp:  +17.0°C                                    

it8716-isa-0228
Adapter: ISA adapter
VCore:       +1.07 V  (min =  +0.00 V, max =  +4.08 V)
VDDR:        +1.17 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.33 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +4.97 V  (min =  +0.00 V, max =  +5.99 V)
+12V:       +12.10 V  (min =  +0.00 V, max = +16.32 V)
in5:         +1.18 V  (min =  +4.02 V, max =  +4.08 V)
in6:         +1.94 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:        +4.87 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.33 V
fan1:       1347 RPM  (min = 3245 RPM)
fan2:          0 RPM  (min = 3245 RPM)
fan3:          0 RPM  (min = 3245 RPM)
temp1:       +34.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermal diode
temp2:       +44.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = transistor
temp3:       +47.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = transistor
cpu0_vid:   +1.550 V
```

temp1: of the it8716-isa-0228 sensor is my CPU, and it's more or less the same value as the CPU temperature in my BIOS.

Try running ```
sensors-detect
``` to detect more of your machines sensors.

---

### Post by smartboyathome on 2009-03-03
My HP runs hot too, especially when compiling or doing any semi-heavy CPU work. I had to buy an external laptop fan just to keep it from overheating during long compile sessions. :(

---

### Post by swoll1980 on 2009-03-03
Is it clean? Dust can over heat a computer real fast.

---

### Post by smartboyathome on 2009-03-03
> **swoll1980 said:**
> Is it clean? Dust can over heat a computer real fast.

Have never checked. I guess it makes sense that dust might be on the CPU, since whenever it gets close to 212 degrees fahrenheit, it starts to smell like something is burning.

---

### Post by FuturePilot on 2009-03-03
> **smartboyathome said:**
> Have never checked. I guess it makes sense that dust might be on the CPU, since whenever it gets close to 212 degrees fahrenheit, it starts to smell like something is burning.

That doesn't sound too good. :shock:

---

### Post by Reaper29 on 2009-03-03
the problem with my laptop, is my fan isnt even coming on. and i know it work cause i just switched from vista and it was working fine.

---

### Post by konqueror7 on 2009-03-03
> **smartboyathome said:**
> Have never checked. I guess it makes sense that dust might be on the CPU, since whenever it gets close to 212 degrees fahrenheit, it starts to smell like something is burning.

thats scary...it could explode anytime...hehe:KS

---

### Post by JECHO on 2009-03-03
> **Reaper29 said:**
> the problem with my laptop, is my fan isnt even coming on. and i know it work cause i just switched from vista and it was working fine.

that was a problem with the macbooks as well... fortunately there was a fix for them but all i would recommend is that you check the bios settings, maybe the fan was disabled or something. that's strange that it isn't even coming on.

---

### Post by jomiolto on 2009-03-03
> **Reaper29 said:**
> the problem with my laptop, is my fan isnt even coming on. and i know it work cause i just switched from vista and it was working fine.

I have this same problem when I'm running 64-bit Ubuntu 8.04 or 8.10. The 32-bit versions work normally and so does the 64-bit Alpha of 9.04. My laptop came pre-installed with 32-bit Vista, but I'm not sure if that's in anyway related...

---

### Post by eagleliu on 2009-03-03
> **Reaper29 said:**
> im new to linux, im actually running Mint 6 x64bit (was running Ubuntu 8.10, but was alittle to hard for me). i was directed here to see if maybe anyone can help me. i have an HP DV2610us, and my laptop runs extreamly hot. i have lm-sensors installed, and my cpu temps at this very moment are:
matt@DV2610us ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +98.0°C  (crit = +120.0°C)                  
temp2:       +87.0°C  (crit = +120.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +81.0°C                                    
Core0 Temp:  +77.0°C                                    
Core1 Temp:  +81.0°C                                    
Core1 Temp:  +77.0°C 

i know this has to be WAY WAY to hot. my fan does not even come on, and i know it works cause it was just working fine in Vista. Any suggestions?

I bought HP laptop 2 years ago,the CPU was made by AMD,the CPU always very hot even use laptop cooler,and HP office repaired 2 times for me,at last,I bought ASUS laptop last year,the CPU was made by Intel,my laptop is not hot without cooler.

-----------------------------------------
[http://www.pc-adapter.net](http://www.pc-adapter.net)
[http://www.shopsintech.com](http://www.shopsintech.com)

---

### Post by Reaper29 on 2009-03-03
> **JECHO said:**
> that was a problem with the macbooks as well... fortunately there was a fix for them but all i would recommend is that you check the bios settings, maybe the fan was disabled or something. that's strange that it isn't even coming on.

there are no setting in my bios for the fan..:(

---

### Post by mips on 2009-03-03
> **swoll1980 said:**
> Is it clean? Dust can over heat a computer real fast.

+1

Experienced this two weeks ago with a friends PC. Every now and again that shrill bios alarm would sound when his pc was working a bit harder. I opened the case and the entire top of the heatsink was covered in dust, fluff & cat hairs so effectively no air was being drawn over the heatsink fins.

---

### Post by Reaper29 on 2009-03-03
> **mips said:**
> +1

Experienced this two weeks ago with a friends PC. Every now and again that shrill bios alarm would sound when his pc was working a bit harder. I opened the case and the entire top of the heatsink was covered in dust, fluff & cat hairs so effectively no air was being drawn over the heatsink fins.

i blew out the fan and fins through the casing with canned air a few days ago, but as i stated, the fan does not come on, AT ALL... not even when the laptop is first started and booted up.

---

### Post by swoll1980 on 2009-03-03
> **Reaper29 said:**
> i blew out the fan and fins through the casing with canned air a few days ago, but as i stated, the fan does not come on, AT ALL... not even when the laptop is first started and booted up.

Try a live cd of a simple repair cd like parted magic,(or even a full sized distro) see if your fan comes on, if it does file a bug report. If it doesn't it might be the kernel, try a few, if non of them work file a bug report with the kernel devs.

---

### Post by FuturePilot on 2009-03-03
> **swoll1980 said:**
> Try a live cd of a simple repair cd like parted magic,(or even a full sized distro) see if your fan comes on, if it does file a bug report. If it doesn't it might be the kernel, try a few, if non of them work file a bug report with the kernel devs.

I agree. At this point this sounds more like a bug than anything else.

---

### Post by mips on 2009-03-03
> **Reaper29 said:**
> i blew out the fan and fins through the casing with canned air a few days ago, but as i stated, the fan does not come on, AT ALL... not even when the laptop is first started and booted up.

That could be one of two issues, a dead fan or a kernel bug. I have experienced a fan not working on a Fujitsu laptop before and the cause was related to the kernel.

Does the fan work under windows or a older livecd?


[http://ubuntuforums.org/showthread.php?t=441036](http://ubuntuforums.org/showthread.php?t=441036)

Edit:

I did a quick google search and the problem seem common with linux on your laptop. I assume you have a AMD cpu? With the amd cpu the fan never comes on, the models with Intel cpu the opposite happens in the the fan never goes off.

First check if there are any BIOS updates for your laptop.

Do you have any power management options in the bios?

I'll look around a bit more for you.

---

### Post by Reaper29 on 2009-03-03
thanks for the quick reply, well all day yesterday i switched from 2 other operating sytems Mint 6, from what someone was saying that its because im running the 64bit editions of linux. can this be true? when you run a live cd, you just put it in and use it right? i have Ubuntu 8.10 intrepid Ibex, Mint 6 and Fedora on a live cd. They are all the 64bit edition though.

---

### Post by Reaper29 on 2009-03-03
> **mips said:**
> That could be one of two issues, a dead fan or a kernel bug. I have experienced a fan not working on a Fujitsu laptop before and the cause was related to the kernel.

Does the fan work under windows or a older livecd?


[http://ubuntuforums.org/showthread.php?t=441036](http://ubuntuforums.org/showthread.php?t=441036)

.

it was working before i switched from vista, which has been less then a month.

do you think when i blew the fan/heatsink with the canned air that maybe it jammed the fan up?

i dont have any old versions of linux to try, only new live cd's.

---

### Post by swoll1980 on 2009-03-03
> **Reaper29 said:**
> it was working before i switched from vista, which has been less then a month.

do you think when i blew the fan/heatsink with the canned air that maybe it jammed the fan up?

i dont have any old versions of linux to try, only new live cd's.

The live cds run all the same drivers and apps that the installed one do, so for trouble shooting they will work fine. just boot them and select the run from cd option, might be worded differently, like try w/o changes, or something like that.

Mint, and Ubuntu are virtually the same, so they would more likely have the same bugs

---

### Post by mips on 2009-03-03
> **Reaper29 said:**
> 
do you think when i blew the fan/heatsink with the canned air that maybe it jammed the fan up?


Nah, I highly doubt it. I'm pretty sure it is OS related.

Could you possibly try and download a small 32bit livecd like Slitaz for example and test with that.

Or try one of these, [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by Reaper29 on 2009-03-03
ok got it..im new to linux, only been using for a month or so.. i will make a new live cd running the 32bit, what operating system do i use? 32bit mint or ubuntu? those are really the only 2 i have messed with. and kubuntu, but that one kind of had me lost a bit.

---

### Post by Reaper29 on 2009-03-03
well my fan has now come on and is working so far. with lm-sensors, my temps are:
matt@DV2610us ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +44.0°C  (crit = +120.0°C)                  
temp2:       +47.0°C  (crit = +120.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +39.0°C                                    
Core0 Temp:  +35.0°C                                    
Core1 Temp:  +42.0°C                                    
Core1 Temp:  +32.0°C    

i did this fix from this post, [http://ubuntuforums.org/showthread.php?t=951838](http://ubuntuforums.org/showthread.php?t=951838) , but can someone tell me (be specific, im new to linux) how i can get kpowersave to automaticly start when i boot up.

---

### Post by Gramps on 2009-03-03
gkrellm is a monitor but it also lets you set the trigger points for the fans.

i8krellm utilities
On Dell laptops and serveral others and maybe some desktops you will need this to get the fans to kick in. The kernal still doesn't do this well yet.

Install the i8kutilities and gkrellm

To get it to work do the following

```

sudo apt-get install gkrellm i8kutilities
sudo modprobe i8k force=1
sudo gedit /etc/modules
add the following line to the end of the file: i8k force=1
```

To load gkrellm automaticlly on startup goto system/Preferences/Sessions and ad usr/bin/gkrellm, this works for Ubuntu 8.10 using gnome desktop.

---

### Post by mips on 2009-03-03
> **Reaper29 said:**
> ok got it..im new to linux, only been using for a month or so.. i will make a new live cd running the 32bit, what operating system do i use? 32bit mint or ubuntu? those are really the only 2 i have messed with. and kubuntu, but that one kind of had me lost a bit.


Try and download something small first instead of wasting time/bandwidth on a large iso file as you just want it for testing purposes. Try Slitaz, all you wan to do is boot it and see if the fan comes on.

---

### Post by Gramps on 2009-03-03
Isn't kpowersave from kde which means that if you are using it that the a bunch of kde libs will also be loaded.  Just a thought...

---

### Post by Reaper29 on 2009-03-03
> **Gramps said:**
> Isn't kpowersave from kde which means that if you are using it that the a bunch of kde libs will also be loaded.  Just a thought...

thats what i was thinking also, but so far, its the only thing that has worked, or got the fan to kick on. my temps arent going over 50c so far. i havent restarted yet so im not sure what will happen, but should i remove what i did and try something esle?

---

### Post by Gramps on 2009-03-03
Remove kpowersave and see if gkrellm & i8kutilities will work for you

If gkrellm work for you then you can remove all the extra packages kpowersave installed by
```
sudo apt-get purge kpowersave
sudo apt-get autoremove
```
apt-get autoremove will remove all the orphaned packages.

---

### Post by Reaper29 on 2009-03-03
> **Gramps said:**
> Remove kpowersave and see if gkrellm & i8kutilities will work for you

If gkrellm work for you then you can remove all the extra packages kpowersave installed by
```
sudo apt-get purge kpowersave
sudo apt-get autoremove
```
apt-get autoremove will remove all the orphaned packages.

i have gkrellm already installed also, just not using it

and i cant find i8kutilities, when i try to download it, it says package not found.

---

### Post by blackvd on 2009-03-03
I had a similar problem with a friends HP and turned out there was a recall on it. Apparently the motherboard on some models run hot and eventually end up burning up the wi-fi chips. Check the HP site to see if your model is included in the recall.

---

### Post by Gramps on 2009-03-03
I can't find it now either but I'm not on my Dell laptop so I can't check it right now to see just what I did install.

Look in gkrellm and see if it will let you set the fan triggers. At least you know now that you have kpowersave to fall back on. 

I don't understand why the fans just don't work with the newer distros, even the newer motherboards have fan controls built into them.

I do know that when I boot my laptop off a live-cd to look at a distro haven't had one yet that turned my fans on. 

When I get back to my laptop I'll look and see what the name of i8kutilities really is.

---

### Post by Reaper29 on 2009-03-03
ok thanks again gramps. like you said, i have kpowersave to fall back on, so ill try something else.

btw, the program is called i8kutils..and still not found...lol

---

### Post by mips on 2009-03-03
> **Reaper29 said:**
> 
btw, the program is called i8kutils..and still not found...lol

I don't think there is a 64bit version available.
[https://launchpad.net/ubuntu/intrepid/+source/i8kutils](https://launchpad.net/ubuntu/intrepid/+source/i8kutils)

Here is the upstream bug, [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=480938](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=480938)

---

### Post by Reaper29 on 2009-03-03
> **mips said:**
> I don't think there is a 64bit version available.
[https://launchpad.net/ubuntu/intrepid/+source/i8kutils](https://launchpad.net/ubuntu/intrepid/+source/i8kutils)

yes i was told that there wasnt a 64bit version also.

so the link you posted about the uptream bug, what is it? what do i do?

---

### Post by mips on 2009-03-03
> **Reaper29 said:**
> yes i was told that there wasnt a 64bit version also.

so the link you posted about the uptream bug, what is it? what do i do?


The upstream bug is basically a bug request logged with the Debian developer to create a amd64 package. What has this got to do with Ubuntu? Ubuntu is built on Debian and everything essentially comes from debian.

I would suggest you either try and build the package with the patch or ask someone to help you do it.

---

### Post by Reaper29 on 2009-03-03
> **mips said:**
> The upstream bug is basically a bug request logged with the Debian developer to create a amd64 package. What has this got to do with Ubuntu? Ubuntu is built on Debian and everything essentially comes from debian.

I would suggest you either try and build the package with the patch or ask someone to help you do it.

can you do it for me? :D:P ....when it comes to things like that im stuck.

---

### Post by mips on 2009-03-03
> **Reaper29 said:**
> can you do it for me? :D:P ....when it comes to things like that im stuck.

Sorry but I don't use Ubuntu or any Debian based distro so I cannot do it. Hopefully someone else offers to do it.

---

### Post by Reaper29 on 2009-03-03
no problem, thanks for the help though in finding that for me.

---

### Post by Gramps on 2009-03-03
Reaper29: This might work for you instead of kpowersave
```
sudo apt-get install powersaved
```

That might explain things, the machine I was on when I was looking for i8kutils was a amd64. You may have already tried this but search for the problem on Google using your laptop model and see if you can find something. Maybe even look at the HP site as they are Linux friendly. 


The packages that I am using with gkrellm are i8kutils & gkrellm-i8k the description says that it is for Dell laptops but maybe it will help you out too.

There is also a lot of information in this [thread about fans]("http://ubuntuforums.org/showthread.php?t=41927")

---

### Post by mexlinux on 2010-05-10
Might be related to this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156)

---

