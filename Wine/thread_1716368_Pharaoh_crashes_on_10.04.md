---
title: "Pharaoh crashes on 10.04"
date: 2011-03-28
forum: Wine
---

### Post by Anuovis on 2011-03-28
Hello,

I remember trying this old game [Pharaoh]("http://en.wikipedia.org/wiki/Pharaoh_%28video_game%29") a while ago, maybe on Ubuntu 9.10 or so and it seemed to be working but I'm not really sure since I only tried it to see whether it launched at all, assuming there wouldn't be problems afterwards. Wine test seems to be more favorable from those times though.

Now I am using 10.04 and can't really play this game. I managed to install and run it both on Wine and through Win XP in Virtual Box but in both instances the game crashes. 

I suspect this might have to do something with the resolutions. The game itself is running at 1024x768x16 and my display is at 24/32 bit. I even tried setting the 16 bit depth on the Virtual Machine but it still crashed soon after launching.

Since the game seems to be running, just unstable, I also have a suspicion there might be a workaround for this.

Of course, I might be wrong on both accounts, just my guesses. Anyone who could help with this problem?

---

### Post by howefield on 2011-03-28
Thread moved to "*Wine*" forum.

---

### Post by Anuovis on 2011-03-28
Things I've tried so far that didn't work:


[LIST]
[*]Downgrading Wine to 1.2.x and later to 1.1.42
[*]Switching between full-screen/windowed mode in both VirtualBox and Wine
[*]Setting the virtual desktop to 16 bit depth in VirtualBox
[*]Switching off compiz
[*]Running the game without patching
[/LIST]

I'm a bit out of ideas what to do next, except maybe for trying to run Ubuntu in 16 bit but I am very inexperienced with creating xorg.conf files and are likely to break my system so I put that aside for a while.

Anything else I might try or is it hopeless?

My video card is ATI Radeon x1300.

This is the output I get when running the game through the terminal:

```

Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f66c,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x189458,0x1893e0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x189458,0x1893e0): stub
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f614,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f614,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2f0,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:seh:setup_exception_record nested exception on signal stack in thread 0009 eip 7bc747b0 esp 7ffdbc7c stack 0x232000-0x330000
Terminated

```

---

### Post by Anuovis on 2011-03-28
I think I got it working. After reading the Wine app database comments I decided to try the PlayOnLinux installation once again. Not sure what was wrong on my previous attempt after which I ditched the software and worked with vanilla Wine... but this time it just worked.

It would seem that the difference lies in the version of the Wine itself. PlayOnLinux chose 1.1.29 (the one I couldn't really find in the Wine archive of older apps) and there was another comment on Wine pages stating that 1.1.30 somehow messed things up with the kernel.

For some reason the Wine bugzilla says it's "Not a Wine bug"
[http://bugs.winehq.org/show_bug.cgi?id=23032](http://bugs.winehq.org/show_bug.cgi?id=23032)
[http://bugs.winehq.org/show_bug.cgi?id=20380](http://bugs.winehq.org/show_bug.cgi?id=20380)

I completed a few short missions with very minor sound glitches and no crashes at all, so the game is probably fine. Saving/loading also works.

---

