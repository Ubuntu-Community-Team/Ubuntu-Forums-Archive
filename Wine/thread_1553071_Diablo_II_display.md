---
title: "Diablo II display"
date: 2010-08-14
forum: Wine
---

### Post by xpowerfulxx on 2010-08-14
Alright so I managed to install Diablo II on Ubuntu 10.04 via  PlayOnLinux. However, after the Blizzard Entertainment logo, I get an  error message on my monitor saying "Cannot Access Display" and Analog  Input. How can I fix this?

---

### Post by cogadh on 2010-08-14
What do you have for video hardware and do you have the restricted drivers installed for it?

---

### Post by xpowerfulxx on 2010-08-14
> **cogadh said:**
> What do you have for video hardware and do you have the restricted drivers installed for it?
:confused:I just have nVidia

---

### Post by cogadh on 2010-08-14
An Nvidia what? Nvidia is just a brand name, it doesn't really tell us much more than who manufactured the chip on your video card. It doesn't tell us what chip model it is or anything else about the video card. However, it does tell us that you definitely do need to install the restricted driver in order to get anything resembling 3D hardware functionality, since the basic driver that comes with Ubuntu can't do that.

---

### Post by xpowerfulxx on 2010-08-14
Nvidia X Server? idk thats just what it says

---

### Post by cogadh on 2010-08-14
An X Server is just the backend of your desktop GUI and has nothing to do with the name of your graphics hardware. How about we bypass the question of hardware entirely. Run this in a terminal:
```
glxinfo | grep direct
```
If it comes back saying "Direct Rendering: Yes", then we can stop worrying about your graphics drivers. If it comes back saying "Direct Rendering: No" then you do not have the restricted drivers installed and you will need to do that before the game will ever work.

A minor piece of friendly advice: if you are going to spend any time using Linux, it is in your best interests to learn exactly what hardware is in your system. You should know the make and model of every major component of your PC (processor, video card, sound card, hard drive(s), RAM, motherboard, etc.). There will likely be multiple occasions where having that information readily available will save you a lot of time and trouble. If your PC was bought pre-built, then that info should be available in the machine's documentation or on the manufacturer's website. If it was built for you by someone, then ask them what they put in it.

---

### Post by xpowerfulxx on 2010-08-15
> **cogadh said:**
> An X Server is just the backend of your desktop GUI and has nothing to do with the name of your graphics hardware. How about we bypass the question of hardware entirely. Run this in a terminal:
```
glxinfo | grep direct
```If it comes back saying "Direct Rendering: Yes", then we can stop worrying about your graphics drivers. If it comes back saying "Direct Rendering: No" then you do not have the restricted drivers installed and you will need to do that before the game will ever work.

A minor piece of friendly advice: if you are going to spend any time using Linux, it is in your best interests to learn exactly what hardware is in your system. You should know the make and model of every major component of your PC (processor, video card, sound card, hard drive(s), RAM, motherboard, etc.). There will likely be multiple occasions where having that information readily available will save you a lot of time and trouble. If your PC was bought pre-built, then that info should be available in the machine's documentation or on the manufacturer's website. If it was built for you by someone, then ask them what they put in it.
```
kristopher@ubuntu:~$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
```

So how do I check the model or w/e of everything?

And how do I fix it?

---

### Post by cogadh on 2010-08-15
At least now we know the problem is not your drivers. Try running the game from the terminal to get Wine's error output, it might explain what is happening. To run the game from the terminal, change directories to the game's installation directory, then "wine" the executable:
```
cd /path/to/game
wine game.exe
```
As for where you might get that info about your hardware, as I said, that should all be available in the documentation for your computer, or on the manufacturer's website.

---

### Post by xpowerfulxx on 2010-08-15
> **cogadh said:**
> At least now we know the problem is not your drivers. Try running the game from the terminal to get Wine's error output, it might explain what is happening. To run the game from the terminal, change directories to the game's installation directory, then "wine" the executable:
```
cd /path/to/game
wine game.exe
```As for where you might get that info about your hardware, as I said, that should all be available in the documentation for your computer, or on the manufacturer's website.
This is what I get for game.exe

```
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)
fixme:ntoskrnl:__regs_KfAcquireSpinLock (0x111008) stub!
fixme:ntoskrnl:__regs_KfReleaseSpinLock (0x111008 0) stub!
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x111010, 0, 0, 0, (nil)

```

---

### Post by cogadh on 2010-08-15
No, you misunderstand. I was just providing you a generic example of how to use those commands, you need to replace that "/path/to/game" and "game.exe" with the actual path to the game's installation directory and the actual game executable name.

---

### Post by xpowerfulxx on 2010-08-15
> **cogadh said:**
> No, you misunderstand. I was just providing you a generic example of how to use those commands, you need to replace that "/path/to/game" and "game.exe" with the actual path to the game's installation directory and the actual game executable name.
Oh because in the Diablo II wine directory there really IS a game.exe lol

And I get a never-ending output with a "Put in the Play disc and hit Retry" or something like that even though it's mounted.

---

### Post by cogadh on 2010-08-15
Heh, never would have thought that. I always use "game.exe" as a generic example, I'll have to try something else in the future.

Okay, that play disk message was helpful, it means you haven't patched the game yet. As of patch 1.12, the disk check has been removed. I would highly recommend you do that first, since that disk check is just going to get in the way of anything else we might try to do.

Silly question (and one I should have asked at the start): when you originally installed the game, did you follow one of the "how-tos" like [the one on Wine's AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=49")?

---

### Post by xpowerfulxx on 2010-08-15
> **cogadh said:**
> Heh, never would have thought that. I always use "game.exe" as a generic example, I'll have to try something else in the future.

Okay, that play disk message was helpful, it means you haven't patched the game yet. **As of patch 1.12, the disk check has been removed. I would highly recommend you do that first, since that disk check is just going to get in the way of anything else we might try to do.**
[B]
Silly question (and one I should have asked at the start): when you originally installed the game, did you follow one of the "how-tos" like [the one on Wine's AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=49")[/B]?
1. Where is said patch and how can I use it?
2. No, I just used PlayOnLinux

---

### Post by cogadh on 2010-08-15
Get the patch from Blizzard and just run it like you would anything else in Wine:
[http://us.blizzard.com/support/article.xml?locale=en_US&articleId=20758](http://us.blizzard.com/support/article.xml?locale=en_US&articleId=20758)

---

### Post by xpowerfulxx on 2010-08-15
> **cogadh said:**
> Get the patch from Blizzard and just run it like you would anything else in Wine:
[http://us.blizzard.com/support/article.xml?locale=en_US&articleId=20758](http://us.blizzard.com/support/article.xml?locale=en_US&articleId=20758)
[http://www.youtube.com/watch?v=0e9651T5Ry8](http://www.youtube.com/watch?v=0e9651T5Ry8)

I just re-installed it w/ PoL, and it came with the patch. But the monitor problem still isn't fixed. Watch the video.

---

### Post by xpowerfulxx on 2010-08-16
bump

---

### Post by xpowerfulxx on 2010-08-16
bumpity bump bump

---

