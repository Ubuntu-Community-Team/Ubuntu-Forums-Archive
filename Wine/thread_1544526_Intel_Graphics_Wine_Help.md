---
title: "Intel Graphics Wine Help"
date: 2010-08-02
forum: Wine
---

### Post by Topazkitty on 2010-08-02
Hi, I'm using Wine 1.3.0 from the wine beta ppa and whenever I play a wine game in fullscreen it crashes my Xserver it doesn't matter which version of wine I use it still happens. If I play a linux native game like Frozen-Bubble it doesn't happen. Any ideas? I'm using an Intel GMA965.

---

### Post by cogadh on 2010-08-02
It might help to know what games in particular this is happening with. It sounds like the game is trying to do something the 965 chipset is not capable of doing, which, quite frankly, is not really surprising. The list of what that chipset is capable of is a lot shorter than the list of things it is NOT capable of, so you could very easily be trying to run a game that it simply cannot run.

---

### Post by asdfoo on 2010-08-02
If the X server crashes, you should try updating to the most recent version of Xorg and mesa which is available through ubuntu edgers.   If the problem still happens there it would be worth opening a bug report on ubuntu.

---

### Post by Topazkitty on 2010-08-02
Hi, thanks for responding the game in question that I'm testing is Sonic Adventure DX: Director's cut and thaat ran on my windows parition before. I might try Xorg edgers later but would that conflict with the stable X-updates through ubuntu X?

Thanks!

---

### Post by cogadh on 2010-08-02
You can't really judge a game's performance in Linux through Wine based on what it did through Windows. Despite all of the work the Wine developers have done, it is still not Windows. Additionally, what your hardware is capable of in Windows can be radically different from its capabilities in Linux, mostly due to the differences in the hardware drivers. This is especially true when it comes to the video hardware drivers, in particular the Intel graphics drivers. 

That being said, Sonic Adventure DX should have no problems running on that hardware, however it does require some components of Windows Media Player 9 to run properly. Those components may not be present in the default Wine installation (I'm pretty sure they aren't), so you might try using [winetricks]("http://wiki.winehq.org/winetricks") to install Windows Media Player 9.

---

### Post by Topazkitty on 2010-08-02
Hi, I have installed Windows Media player 9 before I even started playing so that rules out that issue. Also, I've gotten fullscreen to work but only if I adjust the resolution to match the game first it can't switch resolutions automatically and completely logs me out Xorg. 

Thanks for the help and any more suggestions would greatly appreciated

---

### Post by cogadh on 2010-08-02
What resolution is the game trying to run at? When you run the game via the terminal, does Wine produce any error messages?

---

### Post by Topazkitty on 2010-08-02
Hi, I tried the Game in the terminal in fullscreen and it ran but I got the following output from the terminal

fixme:imm:ImmDisableIME (0): stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5f8,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x68f1190,0x68f1930): stub
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 2)
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 2, new mode: 2)

EDIT: I'm running the game at 1024X768

Please Tell me what this means and if there is a fix at all for it.

Thanks!

---

### Post by cogadh on 2010-08-02
Actually, that is all mostly meaningless. The "fixme" errors are just developer notes about what still needs to be worked on in Wine. Unless you plan on spending a bunch of time coding Wine and submitting patches, there really isn't anything you can do to make those go away. 

Frankly, I'm pretty stumped about this one. The game you are trying to run is certainly well within your hardware's limitations, you already addressed the game's additional requirements, the resolution it is running at is nothing unusual, the errors Wine is producing are completely normal... I can see no real reason why it would cause an X crash. If you haven't tried asdfoo's suggestion yet, that might make a difference, but I honestly would have expected Ubuntu's default Xorg and Mesa versions to be sufficient for this game.

---

### Post by Topazkitty on 2010-08-02
Hi, I have installed Xorg Edgers and I tried loading the game a few times and it loads but when I exit it after loading it a few times it still crashes my Xorg.

Any Ideas?

Thanks!

---

