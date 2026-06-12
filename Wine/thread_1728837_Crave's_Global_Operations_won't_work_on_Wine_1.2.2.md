---
title: "Crave's Global Operations won't work on Wine 1.2.2"
date: 2011-04-14
forum: Wine
---

### Post by NiTuS on 2011-04-14
Hi all

I'm new to this forum, although I have been using Kubuntu since 2009. I have to admit I'm mainly a Windows XP user, but I like switching OS, so I use Linux about 30-40% of the time. :)
But let's get down to business! If you don't know Global Operations, it's an old Counter Srike-like game, which I have been playing more or less regularly since it was released on 2002. Since I first installed Kubuntu, I have been trying to get it to work using Wine, but I never achieved it - the game window disappears, but the sound is still working. This is the output I get from the console:

[I]xavi@xavi:~/.wine/drive_c/Program Files/Crave/Global Operations$ fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33e2f0,0x00000000), stub!
[EMAIL="xavier@xavier-netbook:%7E/.wine"]xavi@xavi-netbook:~/.wine[/EMAIL]/drive_c/Program Files/Crave/Global Operations$ fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33de60,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:state_clipping Clipping disabled, but ARB_depth_clamp isn't supported.
fixme:d3d:state_clipping Clipping disabled, but ARB_depth_clamp isn't supported.

[/I]It looks like a graphical issue, doesn't it? These are my computer's specifications:

**Acer Aspire One D255** (a netbook, as you might have wondered)

[LIST]
[*]Windows 7 Starter Edition OS/Kubuntu 10.10 Maverick Meerkat
[*]1.5GHz Intel Atom N550 dual-core processor
[*]1GB DDR3 RAM
[*]250GB hard drive (5400RPM)
[*]10.1-inch display at 1024 x 600 resolution
[*]Intel GMA 3150 graphics
[/LIST]
This also happens with my another computer, which has the following specifications:

**Desktop computer:**

[LIST]
[*]Windows XP/Kubuntu 10.10 Maverick Meerkat
[*]1.81GHz AMD Athlon +3000 Processor
[*]1GB DDR2 RAM
[*]160GB hard drive
[*]NVidia GeForce 9600
[/LIST]

---

### Post by cogadh on 2011-04-14
Global Operations is a Lithtech Engine based game. Almost none of the Lithtech based games will work in Wine (those that do work usually don't work well). Global Operations itself has a "garbage" rating from Wine's Application Database:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=776](http://appdb.winehq.org/objectManager.php?sClass=application&iId=776)

---

### Post by NiTuS on 2011-04-16
Ooh, such a pity... I see someone could get it to work some years ago though, using the 1.2 patch. By the way, I didn't know about that WineHQ database - thanks for the info!

---

