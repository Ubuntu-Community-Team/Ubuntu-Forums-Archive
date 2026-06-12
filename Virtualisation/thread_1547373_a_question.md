---
title: "a question"
date: 2010-08-06
forum: Virtualisation
---

### Post by thelastblack on 2010-08-06
hi guyz!
i have a compaq 510 notebook with the following specs. Can i have a win7 virtualized using any software in ubuntu LTS? im gonna use some scientific softwares( like MATLAB ) and if i can play some not very high games( like WarCraft TFT  or CounterStrike )..
CPU: Core2Duo 2 GHz 2MB Cache
Ram: 2GB 
Graphic: Intel GME956/GLE960 with 64MB dedicated memory

so can i?

---

### Post by thelastblack on 2010-08-07
Actually WinXP is enough for me i dont really need win7.... but of course 7 is better...

---

### Post by howefield on 2010-08-07
Windows XP would run fine virtualised in that hardware.

---

### Post by thelastblack on 2010-08-07
so what software should i use? I am not familiar with this kind of softwares in linux....

---

### Post by Ginsu543 on 2010-08-07
I recommend [_VirtualBox_]("http://www.virtualbox.org/wiki/Linux_Downloads"). It's free, and for virtualizing WinXP, it works great. You do need to choose which version of VirtualBox to use. The version available through the link I gave you is for the PUEL version. This one is not FOSS, but it gives you USB support. There is also the OSE version (which is FOSS) available in the Ubuntu repos. But the OSE version does NOT support USB.

I personally am running a Windows XP guest inside my Lucid host using the latest VirtualBox. As you can see in my siggy, I have enough system resources to throw quite a bit at my VM (1 cpu core and 2 GB of memory), and to be honest my WinXP VM runs faster and more smoothly than it did natively on previous machines. I heartily recommend it.

To show you what it looks like:

---

### Post by thelastblack on 2010-08-08
> **Ginsu543 said:**
> I recommend [_VirtualBox_]("http://www.virtualbox.org/wiki/Linux_Downloads"). It's free, and for virtualizing WinXP, it works great. You do need to choose which version of VirtualBox to use. The version available through the link I gave you is for the PUEL version. This one is not FOSS, but it gives you USB support. There is also the OSE version (which is FOSS) available in the Ubuntu repos. But the OSE version does NOT support USB.

I personally am running a Windows XP guest inside my Lucid host using the latest VirtualBox. As you can see in my siggy, I have enough system resources to throw quite a bit at my VM (1 cpu core and 2 GB of memory), and to be honest my WinXP VM runs faster and more smoothly than it did natively on previous machines. I heartily recommend it.

To show you what it looks like:

ok. Got something.
Cant i just use synaptic package manager to DL virtualbox?
And whats FOSS? I know i should use puel version...

---

### Post by Ginsu543 on 2010-08-08
FOSS stands for Free/Open Source Software, which means that the software is for free (no $) and is free to be used/modified in any way the user sees fit. The Synaptic Package Manager will download and install the OSE (Open Source Edition) version of VirtualBox which does not support USB. The PUEL version available at VirtualBox.org is still for free (no $) but is not free to be used/modified in anyway the user sees fit. But it does support USB. I use the PUEL version myself, so I recommend that one.

---

### Post by thelastblack on 2010-08-08
ok.... seems i cant download from vitrualbox.org
it says: 

[B]Forbidden

Your client is not allowed to access the requested object.[/B]

so do u have any other mirror for this? i googled but found 3.2.6 not 3.2.8 in other sites....
Also i added software source which is said in virtualbox.org but when i use apt-get update it says:
**W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/lucid/non-free/binary-i386/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/lucid/non-free/binary-i386/Packages.gz)  403  Forbidden**
same problem here....
thx

edit: sorry.... no other mirror for that... everysite just gives the virtualbox.org download link not any mirrors.....

what does "USB support" do? e.g. i cant use flash memory with virtualbox ose?
also isnt virtual machine's hdd shared with ubuntu?

---

### Post by thelastblack on 2010-08-08
hey w8!
if there is no usb support it means no usb mouse too,ok?
i think i have to get PUEL version......
i want PUEL really.... Any mirrors?

---

### Post by mendhak on 2010-08-08
No, your USB mouse will still work.  The USB support refers to access to the USB ports.  So if you plug in an external hard drive, your guest OS (in this case Windows XP) can see that you've plugged it in.  If you went for the OSE version then you wouldn't know when something was plugged in. The mouse will work because the host OS (Ubuntu)  is passing those commands along.

---

### Post by thelastblack on 2010-08-08
if mouse works that wouldnt be a gr8 problem .....
what about my other question? can i connect my host and guest to a virtual network in order to share files between them? if it's possible USB support wont be a problem anymore...

---

### Post by Ginsu543 on 2010-08-08
> **thelastblack said:**
> 
i googled but found 3.2.6 not 3.2.8 in other sites....

VirtualBox 3.2.6 should serve you quite well. I suggest you start with that version and get your Windows VM up and running, and then you can easily upgrade to a later version of VirtualBox when it becomes available to you.

---

### Post by thelastblack on 2010-08-09
> **thelastblack said:**
> ok.... seems i cant download from vitrualbox.org
it says: 

[B]Forbidden

Your client is not allowed to access the requested object.[/B]

so do u have any other mirror for this? i googled but found 3.2.6 not 3.2.8 in other sites....
Also i added software source which is said in virtualbox.org but when i use apt-get update it says:
**W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/lucid/non-free/binary-i386/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/lucid/non-free/binary-i386/Packages.gz)  403  Forbidden**
same problem here....
thx

[B]edit: sorry.... no other mirror for that... everysite just gives the virtualbox.org download link not any mirrors.....
[/B]
what does "USB support" do? e.g. i cant use flash memory with virtualbox ose?
also isnt virtual machine's hdd shared with ubuntu?

plz notice the edit section....
i want some mirrors because i cant download from virtualbox.org....

---

### Post by thelastblack on 2010-08-09
i installed VirtualBox OSE from Synaptic Package Manager and it worked... i installed WinXP...
But i cant make Warcraft TFT working on it....
it says i should install DirectX 8.1 or newer but i already installed it...
Is there any issue regarding Graphics of virtual machines?

---

### Post by Ginsu543 on 2010-08-09
I'm not a gamer and I've never tried installing Warcraft on Ubuntu, but it appears that you can run it under Wine. Check out [_this_](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine) website.

Yes, there may be some issues with the graphics on VirtualBox since it allows only 128 MB of ram to be allocated for graphics and it doesn't play with DirectX very well.

---

### Post by thelastblack on 2010-08-09
i said "Warcraft" not "World of Warcraft" ....
they r a whole lot different game....
Warcraft needs much less specs than WOW.
i tried opening it with wine but same error as virtualbox.... no directx although i installed it
when i use "-opengl" for starting warcraft it comes fine in wine but sometimes it would fail and in virtual box its very very bad and laggy....

---

