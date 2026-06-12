---
title: "System freeze when playing Team Fortress 2"
date: 2009-04-15
forum: Wine
---

### Post by blaise69 on 2009-04-15
Hi there,

I've been having massive trouble with trying to get Team Fortress 2 running on Intrepid with any version of Wine or graphics drivers.

Firstly my problem, I load up Steam, lunch TF2, select a server and start playing. after anything from 2-20 minutes my system will completely freeze, no key combinations will let me escape and the only way to get out of this state is to reset, I hate having to do this.

My system specs:

Intel Core 2 Duo,
Ati Radeon X1950,
With Catalyst 9.3 drivers
Wine version 1.1.19

This problem has been happening since I've installed Ubuntu and the stable build of Wine at the time (1.x). I've also had the same results using fglrx drivers.

My Wine registry Direct3D settings:

OffscreenRenderingMode = fbo
PixelShaderMode = enabled
UseGLSL = enabled
VideoMemorySize = 512
VideoRamSize = 512

My Launch settings for TF2:

-dxlevel 80 -w 1280 -h 1024 -sw -noborder -novid -heapsize 512000 +map_background none

the only thing I've noticed to have made any difference is setting the details in-game down to the very minimum.  the higher the detail the sooner it will crash.

I do play other games on this system without any sign of hardware failure, and watch video also.  Finally I'm pretty certain that with a previous version of Ubuntu, perhaps 7.10, I did have TF2 running much more successfully.

Any ideas how to stop my system from freezing?

Cheers,

Blaise.

---

### Post by u235sentinel on 2009-04-15
> **blaise69 said:**
> Hi there,

Firstly my problem, I load up Steam, lunch TF2, select a server and start playing. after anything from 2-20 minutes my system will completely freeze, no key combinations will let me escape and the only way to get out of this state is to reset, I hate having to do this.

My system specs:

Intel Core 2 Duo,
Ati Radeon X1950,
With Catalyst 9.3 drivers
Wine version 1.1.19

This problem has been happening since I've installed Ubuntu and the stable build of Wine at the time (1.x). I've also had the same results using fglrx drivers.

Blaise.

I've had a lot of issues with ATI cards myself.  With my Nvidia 9800GTX I had issues with 1.0.1 so I upgraded to 1.1.15 then eventually to 1.1.17 last night.

Seems to be working pretty good.  Not sure if 1.1.19 is what you want at this time.  Something to try.

Also try replacing your card or updating the driver if you can.

Good Luck!

---

### Post by blaise69 on 2009-04-15
I appreciate that ATI cards are not the best choice for gaming on Linux at this time, but I'm not going to change to NVidia right now.

I've experimented with a few settings, and it seems that running in regular full screen mode at native resolution is a little more stable, I'm not sure it's a fix just yet though, I may have had a lucky run through.

---

### Post by AidanPryde on 2009-04-18
How do you connect to the internet?
I have the same problem. 

I'm using Ubuntu 8.10 64bit.
Athlon X2 4850e
Onboard ATI HD3300 (790GX chipset)

I tried lots of possible solutions, but none helped. Since all the singleplayer Source Games (HL2:Ep2 & Portal) *work* as well as CounterStrike on private (self created) Server with bots, but the Multiplayer Games (CS:S, HL2: DM, TF2) freeze the system randomly after 10sec - 15min, this seems related to **network/multiplayer**.

Christian

---

### Post by blaise69 on 2009-04-18
I've also noted that starting my own games seems fairly stable, so I wondered if it's a performance related or network related thing.

I connect via a router, I'm cable connected to.

---

### Post by AidanPryde on 2009-04-18
hmm, I connect via VPN to my university. There sure is some infrastructure there, but in fact I get a public IP, so NAT cannot be the problem.
Following appdb.winehq.org there are also NVidia users with this problem, so the ATI drivers cannot be the sole problem.

I tried eleminating Sound as the Problem:
- killed pulseaudio
- chose OSS instead of Alsa
- added -nosound to mute TF2 itself
- chose no sounddriver as well

The desktop:
- deactivated all visual effects
- switched off Screensaver

Memory leaks:
- let "top" run in the background, when the system "freezes" there is still lots of unused memory
- the game runs flawlessly for hours singleplayer but can freeze after 5 seconds online
- added the BIOS-fixed amount of 512MB of RAM for the graphics chip cia the -heapsize command

Driver:
- used the standard ubuntu fglrx drivers as well as the latest catalyst package from ATI/AMD website

Hardware:
- Temperature of CPU and Board after Freeze/Reset 24°C / 34°C

Connection:
- I tried vpnc and the official Cisco cient

Wine:
- tried to let the hl2.exe run in win98 mode
- switched pixel shaders and/or vertex shaders off

Time:
- mostly around 4:30 until freeze, but not stable

Game:
- switched servers
- didn't move
- stayed in "option" Menu
- stayed in heavy action

Effect: Nothing
Game works fine, then suddendly freezes.


This is sooo frustrating. What on earth could cause this?

---

### Post by ross232 on 2009-06-05
Finally! Some other people with the exact same issue I'm experiencing.
I've tried many things to resolve this. CS:Source and TF2 work perfectly in offline mode (CSS against Bots is fine) but if I attempt to play online I get a hard lockup of the system within minutes.

I cannot for the life of me determine what is causing this issue.

Dell Studio 1555 Laptop
Ubuntu 9.04 x64
Wine v1.1.22 (other versions tested)
4GB Memory
512MB ATi 4570HD

---

### Post by ross232 on 2009-06-05
I wonder if maybe this is an x64 related bug?

---

### Post by spicydonuts on 2009-06-06
i have the same issue, and also run 64bit (9.04, wine 1.1.19, but had the same problem with 1.0.1)

the idea that it could be a networking problem is interesting.  i've tried connecting via ethernet and wireless (atheros with madwifi)

i also have an nvidia card (quadro 570m)

tf2 worked great under 8.10 as well as arch linux

---

### Post by ross232 on 2009-06-06
> **spicydonuts said:**
> i have the same issue, and also run 64bit (9.04, wine 1.1.19, but had the same problem with 1.0.1)

the idea that it could be a networking problem is interesting.  i've tried connecting via ethernet and wireless (atheros with madwifi)

i also have an nvidia card (quadro 570m)

tf2 worked great under 8.10 as well as arch linux

Was your 8.10 install x64 or x32? If it was x64 and TF2 played ok- perhaps a new kernel issue has snuck in. I was trying to update my kernel to a newer version but the ATi driver doesnt support .29 or higher yet.

Also, I tried disabling my onboard wireless and using a USB key but the issue remains.

I wish I could find some way of debugging this further. If we could just isolate the source of the freeze!

---

### Post by spicydonuts on 2009-06-06
it was x64, as was my arch linux install, but arch runs a significantly newer kernel... perhaps they just skipped the bug a few months ago haha

---

### Post by whisp71 on 2009-08-14
Same exact issue.

Ubuntu 9.04 x32
ATI fglrx 9.7
Wine 1.1.27

What i have tried:
-Dxlevel 81
-Native resolution
-Editing HKEY_CURRENT_USER\Software\Wine\Direct3D keys (various values of
  OffScreenRenderingMode fbo
  PixelShaderMode Enabled
  UseGLSL Disabled
  VideoMemorySize
-Adding some commands to autoexec.cfg - reducing eye-candy effects.

Nothing of above helped, tf2 freeze system after 3-12 min of (a little choppy) playing for 3-4 min ,then it's possible to soft reboot by Alt-Ctrl-Del or Alt-PrntScrn-R.

Something to take into consideration:
1) Some windows users are experiencing freezes too ([http://forums.steampowered.com/forums/showthread.php?t=709526](http://forums.steampowered.com/forums/showthread.php?t=709526) for example); on winXP i have "Retrieving server info" going on for ~1 min when running tf2 first time after booting PC - every time without exception;
2) Lots of windows users reported sudden drop of fps (mostly after updates).

Something is definitely flawed in tf2 engine/networking code.

Nonetheless, if someone would find a solution and post it here, it would be cool :)

---

### Post by PureLoneWolf on 2009-08-14
TF2 runs almost flawlessly for me, with the following command (goto the properties of the game in steam and choose launch options)

```
-windowed -width 1280 -height 1024 - heapsize 2097152 -dxlevel 81
```

Heapsize is half my ram, windowed is because of my dual monitor setup.  I didn't notice anyone mention heapsize in the thread.

Admittedly, I am running an Nvidia 9600GT, but still - maybe this could help.

I read on the steam forums some time ago that running windowed mode, when running through Wine, has had more success.

Hopefully it helps someone

---

### Post by NightMKoder on 2009-08-15
ATI only problem - so nvidia isn't affected. It's bugs in ATI's drivers.

Your best bet is to try offscreenrenderingmode=pbuffer.

---

### Post by whisp71 on 2009-08-15
Tested -heapsize 2097152 and -window - no result. Even in windowed mode it hangs system completely.

With offscreenrenderingmode=pbuffer game is not even starting.

Seems like it's really narrowing down to ATI drivers.

---

