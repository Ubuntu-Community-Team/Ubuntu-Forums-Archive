---
title: "open source phone just around the corner"
date: 2007-10-26
forum: The Cafe
---

### Post by Bannor on 2007-10-26
[http://www.wired.com/gadgets/wireless/news/2007/10/openmoko_firstlook](http://www.wired.com/gadgets/wireless/news/2007/10/openmoko_firstlook)

> A First Tussle With Linux's iPhone Killer: The OpenMoko Neo1973
By Paul Adams  10.25.07 | 12:00 AM 
 
 
The Neo1973's main interface holds the phone's default applications -- an address book, an RSS reader and a media player among them. Under the hood, there's a Linux command line. 
Photo: Paul Adams 
The Neo1973 is the first physical manifestation of a grand idea -- a new breed of wireless handheld built for the open-source age.

It is the first release from the OpenMoko project, a group working to create a fully open source software platform for smartphones, a community-driven alternative to, say, the iPhone. Using Linux as a starting point, the OpenMoko developers have built a system which, although not everyday-usable yet, can be successfully installed and run on a variety of ordinary smartphone hardware: Treos, Motorolas, JasJars and so forth.

But it's not just the software that's malleable. The phone's components are openly documented, making it easy for tinkerers to pull it apart and modify the hardware to run any number of tasks. The phone even ships with a Torx screwdriver, so they can get right down to business.

Even though it's officially a pre-alpha "developer edition" device, the Neo1973 is already generating extreme excitement among the tech elite for its seemingly infinite level of hackability. All that flexibility stands in sharp contrast to Apple's iPhone, whose feature set is nice but rigidly locked in place, and whose software is limited to use on one specific device. Apple recently announced it will offer a software development kit for the iPhone next February, but the saga of users' attempts to crack Apple's iPhone firmware and bend the tool to their needs -- and beyond Apple's wishes -- will continue.

 
The Neo1973 is the first piece of phone hardware designed to run the open source OpenMoko software platform. Although not yet ready for prime time, the Linux-based mobile OS has hackers excited.

Photo: Paul Adams
According to Asheesh Laroia, an early adopter of the Neo1973, the Linux phone's potential for inside-and-out customization is what has hackers truly excited.

"The key for me will not be that I write any particular app," Laroia says, "but that I can customize the apps I'm using on a daily basis. If the e-mail app doesn't have auto-complete, I can add it."

As with the Palm, OpenMoko owners can expect a wealth of third-party applications. But unlike the languishing Palm platform, Laroia points out, the OpenMoko community can customize, evolve and keep OpenMoko alive on future devices even if FIC, the maker of the Neo1973, goes the way of the Newton.

"Open source makes it so that applications created for one device can move to another one," he says.

Eager to put the promise of a Linux-powered iPhone killer to the test, I purchased a prerelease Neo1973 GTA01Bv4 from the OpenMoko website. My kit, which came with some extras for developers, cost $450. The consumer version of the phone will cost $300.

Even before the phone showed up, I knew it wasn't going to be a smooth ride. Perhaps the "I have been warned" check box required by the website for purchase should have given me pause, but I pressed ahead and got it anyway.

The funny-looking silver-and-black plastic device (it also comes in orange) is significantly lighter than my Treo, and its rounded ends make it hard to tell at a glance which end is up. It's outfitted with a touchscreen, a quad-band GSM transceiver, a micro-SD card slot, Bluetooth, onboard GPS and the like. All the features a modern mobile device needs.

Or almost. The promised Wi-Fi, it turns out, won't be added until the next batch rolls off the assembly line, due to some difficulty finding a chip with GPL-friendly drivers. The planned dual accelerometers and graphics accelerator are absent, too. It is, after all, pre-alpha -- which means you shouldn't expect a final version for at least a couple of months.

 
The Neo1973 ships in a portable black box filled with hacker-friendly tools -- including a guitar pick for prying open the phone's case.

Photo: Paul Adams
I unwrapped the device, popped off the back (using the provided guitar pick), slipped in my SIM card and one of the two provided batteries, closed it up, and looked for a charger.

There's no charger. It charges via a USB connection to my computer -- good enough. I powered on the phone and marveled at the scrolling screens of Linux bootup jargon, which terminated after a few seconds with the line, "Kernel panic."

Time to read the manual.

The wiki for new Neo owners assured me that my kernel panic is standard, since in fact the phone ships without a file system. The wiki guided me through downloading software onto my Debian laptop and flashing the phone's firmware with a new kernel and root-file system. Once I had done that, the phone booted up into the OpenMoko system at last.

The installed software has a fine complement of features: the usual calculator, address book and media player, but also an RSS reader and fully two dozen built-in games, as well as the all-important terminal application. The terminal is a crucial tool for using the phone at this stage of its development. Functions like GPS can only be controlled by manually typing in shell commands. To make the phone vibrate, for instance, I can type in:

echo 1 > /sys/class/leds/gta01\:vibrator/brightness 

That command could be used as the basis to write my own little app to signal caller-ID info by Morse-code vibrations in my pocket when someone calls. But I had more pressing projects, like getting the thing to actually let me make a phone call. It wouldn't associate with the T-Mobile network my SIM card uses, no matter what twiddles I tried.

One of the largest and funnest pages on the OpenMoko wiki is the wish list, a communal brainstorming session showing the ambitious spirit driving the project. Ideas range from simple improvements -- speakerphone functionality, a note-taking application -- to supercool, blue-skying hacks: Bayesian spam filtering for text messages, a Palm OS emulator, GPS-based reminders ("You're near the craft store, remember you need more candle wicks"), a walkie-talkie function, and even a feature to automatically give your location to emergency services if the accelerometer detects movement typical of a car crash. Imagination is the only limit -- why not a robust implementation of the Lovegety concept? Or laser tag?

 
The developer release of the Neo1973 comes with a debug board, an essential tool for working out kinks in the software.

Photo: Paul Adams
Acting out of frustration, I eventually violated the whole spirit of the endeavor and installed a different operating system. I deleted OpenMoko from the phone and put on Qtopia, an alternative software platform that's partially proprietary but much more mature.

As soon as I flashed the firmware, I was able to send text messages and make calls. The sound quality on the phone turned out to be excellent. I can always reinstall OpenMoko, and indeed I look forward to doing that. Under the auspices of the open source community, the next iteration of the software is bound to be considerably smoother and cooler.

But for now, I'll wait until OpenMoko is more fully baked -- and remind myself how nice it is the phone gives me the freedom to do so.

---

### Post by rfruth on 2007-10-26
wanna see the Gfone myself

---

### Post by Kingsley on 2007-10-26
That phone definitely needs to be redesigned.

---

