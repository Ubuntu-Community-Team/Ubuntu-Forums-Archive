---
title: "ubiquity-kernelapibot"
date: 2010-01-16
forum: The Cafe
---

### Post by k64 on 2010-01-16
Here's what I would like to see: a bot integrated into Ubiquity that automatically scans devices on your computer for functionality, and automatically enables such functionality by writing, building, and installing a custom kernel via the API, and then automatically, when you reboot upon completed installation, uploads the custom kernel source code onto Launchpad. That way, Linux will support any hardware, anywhere.

Mods, please move this thread into Ubuntu Brainstorm.

---

### Post by 23meg on 2010-01-16
> **k64 said:**
> 
Mods, please move this thread into Lucid Lynx Testing and Discussion.

*puts on Lucid Lynx subforum moderator hat*

Please don't, as it has nothing to do with Lucid. The better place to post your preliminary ideas is Ubuntu Brainstorm.

---

### Post by k64 on 2010-01-16
> **23meg said:**
> *puts on Lucid Lynx subforum moderator hat*

Please don't, as it has nothing to do with Lucid. The better place to post your preliminary ideas is Ubuntu Brainstorm.

Post has been edited.

---

### Post by #11u-max on 2010-01-16
if we could write more drivers and include an "extra drivers/proprietary drivers" package, why would we need to have a custom kernel for a specific type of hardware?

---

### Post by k64 on 2010-01-16
I mentioned that I wanted Ubuntu to include auto-support for hardware on the Kernel API level (adding kernel drivers for the hardware, not customly building a new kernel from scratch) and giving the kernel drivers (automatically) back to the community, so that ALL hardware is supported in Linux. My goal with this is eliminating hardware headaches altogether that people have with Linux at the Kernel API level.

---

### Post by schauerlich on 2010-01-16
So you want someone to write a program which will write drivers?

Do you have the faintest idea how any of this stuff works?

---

### Post by k64 on 2010-01-16
> **schauerlich said:**
> So you want someone to write a program which will write drivers?

Do you have the faintest idea how any of this stuff works?

**Technically, this is the equivalent at the kernel level what Glade, Gazpacho, and Qt Designer are at the GUI level...**

It uses an API to write drivers. The only difference is that this will use your hardware configuration as the basis for the API.

---

### Post by schauerlich on 2010-01-16
> **k64 said:**
> Technically, this is the equivalent at the kernel level what Glade, Gazpacho, and Qt Designer are at the GUI level...

I rest my case.

---

### Post by phrostbyte on 2010-01-16
I'd love some software that could automatically write code for me! I don't think AI is that advanced yet, but what would I know? O:)

---

### Post by k64 on 2010-01-16
I would like to see more replies as to figure out if this is helpful or not. Personally, I know how to write C/C++ programs (but not without reading from a book). However, I can't write this potentially game-changing program by myself. I would like opinion - and help. Also, I am planning to call it a "Device Driver Designer". The only thing is that this "designer" will do it automatically - by scanning your hardware.

One more thing: Are people under 18 allowed to create Launchpad accounts? I would love to know, because I would love to host such a project there.

Edit: I realized that if you're registered here you're registered there.

---

### Post by k64 on 2010-01-16
I have created the new project on Launchpad: [https://launchpad.net/devicematic](https://launchpad.net/devicematic)

I certainly need programmers for it.

---

### Post by schauerlich on 2010-01-16
> **k64 said:**
> I would like to see more replies as to figure out if this is helpful or not.

While a magical program that writes drivers on the fly would be nice, it's not going to happen.

> Personally, I know how to write C/C++ programs (but not without reading from a book). 

gl;hf

---

### Post by Keyper7 on 2010-01-16
I vote for closing this thread.

It's pretty clear nothing good will come out of it.

---

### Post by 3rdalbum on 2010-01-16
> **Keyper7 said:**
> I vote for closing this thread.

It's pretty clear nothing good will come out of it.

I'm sure somebody will get a good laugh out of it.

You can't write drivers magically just by knowing what the hardware is. The kernel compiling process doesn't write drivers, it just lets you enable/disable drivers that have already been written.

And having a different kernel for each different piece of hardware? What happens if you want to play a music file out of your X-Fi sound card AND access said file across a wireless network at the same time?

---

### Post by k64 on 2010-01-16
> **3rdalbum said:**
> I'm sure somebody will get a good laugh out of it.

You can't write drivers magically just by knowing what the hardware is. The kernel compiling process doesn't write drivers, it just lets you enable/disable drivers that have already been written.

And having a different kernel for each different piece of hardware? What happens if you want to play a music file out of your X-Fi sound card AND access said file across a wireless network at the same time?

That's because Make Xconfig configures devices from existing drivers, but who said it can't be hacked to configure at the API level instead of the filesystem level? 

You see, the Kernel API is absolutely immense, not to mention that the API pretty much contains total support of hardware, even though not all of it is written.

Personally, I was thinking of automatically digging already defined functions out of the API, not creating new ones unless I really needed to. And even new functions will be based on existing ones. So, technically, everything will already be defined.

As for the hardware scan, it will tell the computer what functions to use.

And NO, I do not intend on creating new kernels for each piece of hardware. I plan on using the API to create new .ko files (kernel modules).

-Kenny Strawn

P.S. The Kernel API can be found at [http://kernelbook.sourceforge.net/kernel-api.pdf](http://kernelbook.sourceforge.net/kernel-api.pdf)

---

### Post by schauerlich on 2010-01-17
> **k64 said:**
> That's because Make Xconfig configures devices from existing drivers, but who said it can't be hacked to configure at the API level instead of the filesystem level? 

You see, the Kernel API is absolutely immense, not to mention that the API pretty much contains total support of hardware, even though not all of it is written.

Personally, I was thinking of automatically digging already defined functions out of the API, not creating new ones unless I really needed to. And even new functions will be based on existing ones. So, technically, everything will already be defined.

As for the hardware scan, it will tell the computer what functions to use.

You seem to have a plan. Draw up some plans, write an alpha version and you might just get some interest.

Until then, lolz.

---

### Post by Mr. Picklesworth on 2010-01-17
So what do I do when my modem starts playing music, the power button becomes the sole means of text input and the DVD drive is given the job of console output by opening and closing its tray with morse code?

---

### Post by phrostbyte on 2010-01-17
> **k64 said:**
> That's because Make Xconfig configures devices from existing drivers, but who said it can't be hacked to configure at the API level instead of the filesystem level? 

You see, the Kernel API is absolutely immense, not to mention that the API pretty much contains total support of hardware, even though not all of it is written.

Personally, I was thinking of automatically digging already defined functions out of the API, not creating new ones unless I really needed to. And even new functions will be based on existing ones. So, technically, everything will already be defined.

As for the hardware scan, it will tell the computer what functions to use.

And NO, I do not intend on creating new kernels for each piece of hardware. I plan on using the API to create new .ko files (kernel modules).

-Kenny Strawn

P.S. The Kernel API can be found at [http://kernelbook.sourceforge.net/kernel-api.pdf](http://kernelbook.sourceforge.net/kernel-api.pdf)

All a device looks to the kernel is an address range. It's up to a programmer to read/write data to this address range. If it's a wifi card or something, then there is specific API to invoke on certain actions the device exposes. So in a way, the Linux API makes is EASIER to write drivers, by having a very big API and massive code reuse between similar drivers. But you still need to write the low level driver for the device. This will not write itself. 

Here is some of the drivers included with the Linux kernel (source code):

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers;h=b3353acb1ce363a82c9ca0dacbc491f80f4d8408;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers;h=b3353acb1ce363a82c9ca0dacbc491f80f4d8408;hb=HEAD)

Now, if you are talking about building a custom kernel BASED on your hardware, this might be worth perusing (although not really needed because in Ubuntu, the kernel is split into many parts which are loaded on demand by udev). 

This will involve wiring lspci/lsusb to generate a custom build config. Then you pass the build config to the Linux build system. You could do this easily with perl/python, and probably even a bash script.

---

### Post by Mr. Picklesworth on 2010-01-17
> **phrostbyte said:**
> All a device looks to the kernel is an address range. It's up to a programmer to read/write data to this address range. If it's a wifi card or something, then there is specific API to invoke on certain actions the device exposes. So in a way, the Linux API makes is EASIER to write drivers, by having a very big API and massive code reuse between similar drivers. But you still need to write the low level driver for the device. This will not write itself. 

Here is some of the drivers included with the Linux kernel (source code):

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers;h=b3353acb1ce363a82c9ca0dacbc491f80f4d8408;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers;h=b3353acb1ce363a82c9ca0dacbc491f80f4d8408;hb=HEAD)

Now, if you are talking about building a custom kernel BASED on your hardware, this might be worth perusing (although not really needed because in Ubuntu, the kernel is split into many parts which are loaded on demand by udev). 

This will involve wiring lspci/lsusb to generate a custom build config. Then you pass the build config to the Linux build system. You could do this easily with perl/python, and probably even a bash script.

Of interest to this end, one amazing video:
[http://video.google.ca/videoplay?docid=2671867977172003291](http://video.google.ca/videoplay?docid=2671867977172003291)

---

### Post by Frak on 2010-01-17
> **schauerlich said:**
> I rest my case.
Agreed.

---

### Post by Techsnap on 2010-01-19
> I plan on using the API to create new .ko files (kernel modules).

You're wasting time.

---

### Post by Frak on 2010-01-19
I just learned C++, so I'll develop the most difficult project known to mankind?

---

### Post by Queue29 on 2010-01-19
There's no reason to crush dreams like that! Do you think Linus ever demoralized himself when he though about how much work there was to be done when he started writing the Linux kernel?

I changed the code so that it actually compiles now, and I added a Circle struct so we can use those too.

```

//Search.cpp: The DeviceMatic Device Scanner

#include <iostream>
#include <string>
#include "structs.h"

int main (int argc, char** argv)
{
	std::cout << "DeviceMatic Device Scanner" << std::endl;
	Rectangle rect;
	rect.width = 5;
	rect.height = 4;
	std::cout << "Rectangle Area: " << calcRectArea(&rect) << std::endl;
	return 0;
}


void idMotherboard(std::string str)			//Identify all motherboards
{
	std::cout << "Scanning Motherboard" << std::endl;
}

void idCPU (std::string str)				//Identify all processors
{
	std::cout << "Scanning the CPU" << std::endl;
	
}

void idRAM (std::string str)		//Identify all Random Access Memory
{
	std::cout << "Scanning RAM, Memory" << std::endl;
	
}

void idGraphicsCard (std::string str)		//Identify all video cards and TV tuners
{
	std::cout << "Scanning Graphics Card, TV Tuner" << std::endl;
	
}

void idNetworkAdapter (std::string str)		//Identify all network adapters, wired and wireless
{
	std::cout << "Scanning Network Adapter" << std::endl;
	
}

void idHardDrive (std::string str)			//Identify all hard disks and SSDs
{
	std::cout << "Scanning Hard Drive, SSD" << std::endl;
	
}

void idWebcam (std::string str)			//Identify all webcams
{
	std::cout << "Scanning Webcam" << std::endl;
	
}

void idDvdDrive (std::string str)			//Identify all DVD drives
{
	std::cout << "Scanning DVD Drive" << std::endl;
	
}

void idCDDrive (std::string str)			//Identify all CD drives
{
	std::cout << "Scanning CD Drive" << std::endl;
	
}

void idBluRayDrive (std::string str)		//Identify all Blu-Ray drives
{
	std::cout << "Scanning Blu-Ray Drive" << std::endl;
}

```

```

//Structs.h: Defines new functions used in DeviceMatic

#include <iostream>
#include <string>
#include <cmath>
//#include <kernel-api/*>

struct hardware 
{
	std::string mobo;
	std::string cpu;
	std::string ram;
	std::string graphicscard;
	std::string networkadapter;
	std::string harddrive;
	std::string webcam;
	std::string dvddrive;
	std::string cddrive;
	std::string bluraydrive;
};

struct scan
{
	/* TODO: implement this */
	//find (hardware);		//Scan hardware configuration
};

struct Rectangle
{
	int X;	//Top left
	int Y;	//corner coordinates

	int width;	//Bottom right
	int height;	//corner coordinates
	
};

struct Circle
{
	int X;	// x coordinate
	int Y;  // y coordinate
	int radius; // the radius
};

long calcRectArea(struct Rectangle* r)
{
	return r->width * r->height;
}

double calcCircleArea(struct Circle* c)
{
	return 2 * 3.14159 * c->radius;
}

```


To compile and run it:
```

$ g++ -o search search.cpp
$ ./search 
DeviceMatic Device Scanner
Rectangle Area: 20

```

---

### Post by Frak on 2010-01-19
> **Queue29 said:**
> There's no reason to crush dreams like that! Do you think Linus ever demoralized himself when he though about how much work there was to be done when he started writing the Linux kernel?

I changed the code so that it actually compiles now, and I added a Circle struct so we can use those too.

To compile and run it:
```

$ g++ -o search search.cpp
$ ./search 
DeviceMatic Device Scanner
Rectangle Area: 20

```
The output makes me lol. "So, here's what we found: The Rectangle Area was 20".

---

### Post by schauerlich on 2010-01-19
> **Queue29 said:**
> There's no reason to crush dreams like that! Do you think Linus ever demoralized himself when he though about how much work there was to be done when he started writing the Linux kernel? There's a difference between "difficult but possible" and "difficult, as in impossible". See [CptPicard/phrostbyte discussion here](http://ubuntuforums.org/showthread.php?t=1383317&page=2).

> I changed the code so that it actually compiles now, and I added a Circle struct so we can use those too.

You do realize it still accomplishes nothing of value, right? And besides, the rectangle was for the GUI designers... what would they need with a circle? </sarcasm>

---

