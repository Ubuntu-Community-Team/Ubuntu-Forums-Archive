---
title: "With WINE can you run windows programs or windows games"
date: 2012-07-05
forum: The Cafe
---

### Post by nec207 on 2012-07-05
People say WINE is not emulator it is a Windows compatibility layer. If so how does this work and what is toolkit for porting thing do that wine uses?
 
It some kind of Windows compatibility layer. 
 
 
Also is there other programs like wine out there?

---

### Post by Bucky Ball on 2012-07-05
As to your thread title: That is Wine's only function. It doesn't do anything apart from that. That's what it's intended to do and specifically designed for. 

Go to WineHQ to track what runs and what doesn't. Wine can run many Windows programs - some great, others poorly - but it can't run all. You just install the programs through Wine the same way as you would install a program using Windows.

---

### Post by critin on 2012-07-05
> Also is there other programs like wine out there? 	



[http://www.codeweavers.com/products/#cxlinux](http://www.codeweavers.com/products/#cxlinux)

[http://blogs.computerworld.com/easily_run_windows_apps_on_linux_with_crossover_linux_8](http://blogs.computerworld.com/easily_run_windows_apps_on_linux_with_crossover_linux_8)

---

### Post by kaldor on 2012-07-05
Yes, but it's not always a valid option. Depends on a lot of things.

If you want a simple example of how it works, install WINE from the repositories, download the Windows version (.exe) of Firefox, and right click > open with WINE.

---

### Post by Bucky Ball on 2012-07-06
... but once installed, if you decide you don't want to use it, WINE is almost impossible to completely get rid of, not that it does much but take up space. If you are intending to use a lot of Win software maybe stick with Win, dual-boot, or run Windows as a virtual machine inside Ubuntu. ;)

---

### Post by doorknob60 on 2012-07-06
> **Bucky Ball said:**
> ... but once installed, if you decide you don't want to use it, WINE is almost impossible to completely get rid of

Huh? Just remove it with apt-get/synaptic/software center and remove the $HOME/.wine folder, and remove the wine folder from your apps menu, not too hard.

---

### Post by Bucky Ball on 2012-07-06
Left stuff everywhere when I installed it four years ago. I couldn't get rid of everything. After your method, if you do 'locate wine' in a terminal, do you find anything?

---

### Post by rai4shu2 on 2012-07-06
Unless you permit it, wine doesn't even know how to find anything other than ~/.wine (within the wine environment).

---

### Post by 3Miro on 2012-07-06
> **nec207 said:**
> People say WINE is not emulator it is a Windows compatibility layer. If so how does this work and what is toolkit for porting thing do that wine uses?

Technically emulation refers to hardware, i.e. you can play old Nintendo games on a modern computer, but you need emulation software since the old Nintendo processors were very different form a modern Intel or AMD.

> 
It some kind of Windows compatibility layer. 



Wine works on the same hardware, it just creates an interface between the Linux kernel (and Xorg) and the windows program. When the windows program has to make a system call and communicate with Windows, then wine takes the call and translates to a corresponding call to Linux.

>  
 
Also is there other programs like wine out there?

I don't think so.

Wine aims at working with all windows programs, however, they do put more emphasis on games.

---

### Post by nec207 on 2012-07-06
Okay but what is this  toolkit or porting thing that wine uses ?

---

### Post by 3Miro on 2012-07-06
> **nec207 said:**
> Okay but what is this  toolkit or porting thing that wine uses ?

What do you mean? 

If you have the source-code for a Windows program, you can recompile it and link it to wine libraries directly (as opposed to the Windows libraries). Then the program will run as a native program on Linux. Is this what you are asking about?

---

### Post by nec207 on 2012-07-06
> **3Miro said:**
> What do you mean? 
 
If you have the source-code for a Windows program, you can recompile it and link it to wine libraries directly (as opposed to the Windows libraries). Then the program will run as a native program on Linux. Is this what you are asking about?
 
I'm thinking the port thing must be hardware address port number to control the hardware bypassing the BIOS.
 
The toolkit I think is some kind of service Wine uses for API.

---

### Post by neu5eeCh on 2012-07-06
I've never had any luck using WINE for anything but the most basic Windows software.

If one is willing to pay Crossover or Bordeaux for Linux for a limited support license, then it's possible to install something like WordPerfect, but I've never, ever had any luck trying to do so on Wine alone. It's like trying to use old-school linux with its dependency hell.

I find it much easier to simply install Windows 2000 in Virtualbox. It's just as fast and works better.

---

### Post by CarpKing on 2012-07-06
> **nec207 said:**
> I'm thinking the port thing must be hardware address port number to control the hardware bypassing the BIOS.
 
The toolkit I think is some kind of service Wine uses for API.

Nothing bypasses the BIOS.  Wine is basically a bunch of library files (not sure if that's the proper terminology).  When you use it to run a Windows program, the program thinks these library files are their equivalents on Windows.  The library files are written to copy the functions of the Windows ones, but talk to the Linux kernel, Xorg, etc instead of the Windows kernel and Windows graphics and audio systems.

For instance, when a program run through Wine makes 3d graphics, it outputs them to fake DirectX dlls which actually just translate to OpenGL and output to Xorg.

---

### Post by nec207 on 2012-07-07
Similarly, wine is also Windows emulator under Linux.

Also, cygwin is Linux emulator under windows.
Usually, all emulators works with some limitations!!
 

However, if you have virtual machine SW and other OS's running under it, it just works like respective OS. No limitations or controls or sacrifices

---

### Post by 3Miro on 2012-07-07
> **nec207 said:**
> 
However, if you have virtual machine SW and other OS's running under it, it just works like respective OS. No limitations or controls or sacrifices

You cannot play 3D games under Virtual Box. Wine on the other hand plays many 3D games pretty well. Virtual Box cannot do everything that Wine can and Wine cannot do everything that Virtual Box does.

---

### Post by jonathonblake on 2012-07-07
> **nec207 said:**
> 
However, if you have virtual machine SW and other OS's running under it, it just works like respective OS. No limitations or controls or sacrifices

That assumes that one can obtain the drivers for the version of Windows, or other OS, that works with the hardware one has.

I'd happly run Win2K on a virtual box on my laptop, if I could obtain drivers for it.  I might even consider Win7, but the only drivers I can find, won't run in a virtual environment.

On the desktop I bought, purely to run Win2K, and other versions of Windows as virtual boxes, no drivers are available, since Windows can not run as a native OS. (Seriously, the desktop was "too advanced" and "too new" for Win7, much less the version of Windows that was available when I purchased the machine several years earlier.)

jonathon

---

### Post by UbunHawk on 2012-07-07
Do people actually recommend WINE then? Just out of curiousity do Adobe programmes work well in the program?

---

### Post by 3Miro on 2012-07-07
> **UbunHawk said:**
> Do people actually recommend WINE then? Just out of curiousity do Adobe programmes work well in the program?

Wine is a bit of a "hit and miss". Give it a try and if it works for you, then it will work well. Wine is the only way to play games like Starcraft II and Dragons Age, and those work very well. 

However, if wine doesn't work, then it just doesn't work.

---

### Post by aysiu on 2012-07-08
> **UbunHawk said:**
> Do people actually recommend WINE then? Just out of curiousity do Adobe programmes work well in the program? I don't think there's a blanket recommendation or non-recommendation. It really depends on the situation.

If you can find a native Linux program that does what you want it to do, it's always better to use a native program than a workaround like Wine.

But if you have a Windows-only program you need, and it happens to work well in Wine, it's better to use Wine than to have to dual-boot or virtualize Windows.

You can check how well individual programs work in Wine by looking at the WineHQ AppDB:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Different programs (and different versions of programs) will have various metal ratings. *Platinum* basically means it works flawlessly. *Gold* means it works well. *Silver* means it basically works but has some problems. I think *Bronze* means it basically doesn't work in any useful way (maybe it launches, but that's it). And then I think *Garbage* just means it won't even install or run.

---

### Post by jockyburns on 2012-07-08
I installed Wine, just so I could try and play my favourite game , Eve Online. I must admit I almost gave up, with it. There were unmet dependencies when trying to install Wine, missing Win stuff like core fonts etc. Searching the internet for some of the missing files etc took hours. 
Once it got to the stage of actually loading the game, the graphics were very jittery and the lag made the game almost unplayable. 
Just a pity CCP chose to drop support for Linux players of that great game. 
The  way I solved the problem was to have another computer running Win7. (works great on that), but only when the G/F isn't using it.
I've not yet considered dual boot on this computer because I don't particularly fancy paying Microsoft the extortionate amount they want for their not so secure OS.

---

### Post by nec207 on 2012-07-08
> **aysiu said:**
> I don't think there's a blanket recommendation or non-recommendation. It really depends on the situation.
 
If you can find a native Linux program that does what you want it to do, it's always better to use a native program than a workaround like Wine.
 
But if you have a Windows-only program you need, and it happens to work well in Wine, it's better to use Wine than to have to dual-boot or virtualize Windows.
 
You can check how well individual programs work in Wine by looking at the WineHQ AppDB:
[http://appdb.winehq.org/](http://appdb.winehq.org/)
 
Different programs (and different versions of programs) will have various metal ratings. *Platinum* basically means it works flawlessly. *Gold* means it works well. *Silver* means it basically works but has some problems. I think *Bronze* means it basically doesn't work in any useful way (maybe it launches, but that's it). And then I think *Garbage* just means it won't even install or run.
 
So you can go to that web site and type the name of the game you want to play in wine and it will tell you if the game is *Platinum*  , *Gold* , *Silver* , *Bronze*  or *Garbage* .

---

### Post by sffvba[e0rt on 2012-07-08
I would also recommend trying out CrossOver... It takes a lot of the guess work and hit and miss out of Wine (and it has a nice way to search to see if an application works or not).

[http://www.codeweavers.com/](http://www.codeweavers.com/)


404

---

