---
title: "Issues connecting Mini PC with Linux Lite 6.6 to LG TV; no HDMI signal on startup."
date: 2024-04-13
forum: Ubuntu/Debian BASED
---

### Post by emaesen on 2024-04-13
I recently bought a Beelink Mini S mini PC. I connected it (HDMI 1) to an LG TV (HDMI 1).  Video and audio were fine. The Mini S comes with Windows 11 installed, which is too resource intensive for this little machine (the cursor would be seriously lagging at times) and the fan is constantly running at full speed. Thus I decided to install Linux. However, while connected to the TV I could not access the bios - at least, I could not view the bios screen. Apparently the TV screen only became active after the OS had started.


I connected the Mini S to my ASUS computer monitor, was able to access the bios and change boot settings, and installed Linux Lite 6.6 (base: Ubuntu 22.04.3 LTS) from a USB drive. All was well and Linux runs properly, I wasn't able to test audio because that ASUS monitor has no build-in speakers. There's audio output from the Mini S headphone jack.


I re-connected the Mini S to my LG TV, turned on the TV and turned on the Mini S. The TV doesn't receive a video signal, and again I can not access the bios either. 
I tried the 3 different HDMI ports on the TV - each time restarting the Mini S - no video signal on either.
After starting up the Mini S while connected to the TV, I unplugged the HDMI cable from the TV and plugged into my monitor, but now there was no video signal there either. It looked like the booting of Linux had been aborted when connected to the TV. When I restart the Mini S, then the monitor shows the Linux screen. When I then unplug the HDMI cable from the monitor and plug it into the TV, now the TV also shows the Linux screen, the video signal works, however there is no audio. But, once I restart the Mini S, again the TV screen is not recognized.


I tried all above scenarios after changing the Mini S bios such that it would use the second HDMI port as video output, but all behavior was the same. I switched the bios back to use the first HDMI port. Strangely, the next time I checked the bios, the second HDMI port was no longer listed. 


My observations/deductions so far:
- The Mini S doesn't seem to be able to detect that the TV is connected through HDMI on startup.
- When no video device is detected during startup, Linux aborts.
- Linux can detect the TV after it has started successfully.


I have the following questions:
1a) How can I ensure that the Mini S / Linux detects the TV on startup? 
1b) How can I ensure that Linux doesn't abort startup when no video device is detected?
2) Once video connection is successful, how can I ensure that audio will work as well?




I'm a Linux novice and searched through many online resources for a possible solution but couldn't see the forest through the trees. Hopefully someone here can help me or point me in the right direction.

---

### Post by hyperlinxe on 2024-04-13
So, you first tested the pc with it's default operating system, windows 11, on the tv, and it worked. Then you attempted to install linux on the pc, but found a blank screen instead of the typical bootup/bios screen. That is generally a problem if you have two monitors connected at the same time, where output will default to a pc type monitor instead of the tv screen. 

It's not clear to me, whether or not you installed linux initially, then found you had problems, or that you had problems when attempting to install linux.

> Apparently the TV screen only became active after the OS had started.[/QUOTE

That is a typical problem with tv screens, that I've seen, and I think it can occur whether or not there are two monitors hooked up. Therefore it can be resolved by using a typical pc monitor in order to install the OS initially, and then starting the OS with a TV screen after installation.

[QUOTE]I connected the Mini S to my ASUS computer monitor, was able to access  the bios and change boot settings, and installed Linux Lite 6.6

So then you installed linux on the mini pc, and using a typical pc monitor you were able to access bios settings.

> I re-connected the Mini S to my LG TV, turned on the TV and turned on  the Mini S. The TV doesn't receive a video signal, and again I can not  access the bios either. 

It seems you are attempting to use the TV screen as your primary monitor. For that to work nicely, without knowing what kind of tv it is, assuming it might be a high resolution screen, you are going to need to install graphics drivers.

[QUOTE]After starting up the Mini S while connected to the TV, I unplugged the  HDMI cable from the TV and plugged into my monitor, but now there was no  video signal there either.[/QUOTE

You are going to want to make sure to cleanly shutdown your system, and plug in your hdmi cable to your desired monitor, so that it is properly detected during bootup, and the system is configured to work with it. 

Please add the general specs of the tv you are attempting to use as your primary monitor, and what the graphics card of your computer is.

You should attempt to get proper graphics drivers for your card, before attempting to use the tv screen as your primary display, or even as a second monitor.

You can look up guides online for properly installing graphics drivers on linux very quickly, and use your typical pc monitor as a base to get it working with your tv screen.

If you have proper drivers for your graphics card, and the proper input selected in the tv settings, like for example hdmi 1 if it's plugged into the tv's hdmi 1 port, than you should be able to use it as your primary monitor, even though you may not see the typical bios messages you expect to see, like what you get with a pc monitor.

---

### Post by emaesen on 2024-04-13
Thank you for your reply.

I have just one display connected to the Mini S PC at any time. Although it has two HDMI outputs, only one is active depending on bios settings. Thus, even if I connect both the monitor and the TV to the PC, only the one on the active HDMI port receives a signal.

The TV is an LG 49UH6090, 3840 x 2160, and I want to use it as my primary, and only, display device.

> [COLOR=#000000]It's not clear to me, whether or not you installed linux initially, then found you had problems, or that you had problems when attempting to install linux.

[/COLOR]The Linux install went without issues - I had the Mini PC connected to the monitor at that time. The issues started to become apparent when I switched back to the TV as my display device.

> [COLOR=#000000]You are going to want to make sure to cleanly shutdown your system, and plug in your hdmi cable to your desired monitor, so that it is properly detected during bootup, and the system is configured to work with it.

[/COLOR]My primary problem seems to be that the LG TV is not detected during bootup. I assume that since during installation the Mini PC was connected to the ASUS monitor it somehow detected that and configured the OS specifically for that? And now I need to add specifications for the LG TV?

I'm having trouble finding documentation for the Mini S... 

> [COLOR=#000000]You should attempt to get proper graphics drivers for your card, before attempting to use the tv screen as your primary display, or even as a second monitor.[/COLOR]


I will try to look into this more.

---

### Post by hyperlinxe on 2024-04-13
> My primary problem seems to be that the LG TV is not detected during  bootup. I assume that since during installation the Mini PC was  connected to the ASUS monitor it somehow detected that and configured  the OS specifically for that? And now I need to add specifications for  the LG TV?

If you don't manually configure your display settings, and save them, than this process is generally automatic. Your biggest concern is simply getting proper drivers for your graphics card, otherwise the stock drivers aren't going to function well, especially with a 4k tv.

---

### Post by coffeecat on 2024-04-13
*Thread moved to **Ubuntu/Debian BASED** sub-forum.*

---

### Post by emaesen on 2024-04-13
It seems to me that the graphics drivers are ok though, because if I start the Mini PC while connected to the ASUS monitor, and after Linux has properly loaded I switch the HDMI cables to connect the LG TV instead of the ASUS monitor then everything displays fine on the TV (aside from the no-sound issue).

So my main problem seems to be that if no display device is detected during boot time, Linux start-up appears to be aborted. Am I correct in that observation?

---

### Post by hyperlinxe on 2024-04-13
If you have your display working on the tv, and you have no audio output, check your audio settings, to see that they are set to use the hdmi output. (in the operating system, and then on the tv)

You don't know what kind of graphics driver your mini pc needs? It's gotta have some kind of graphics card. 

There's basically some autoconfiguration related to your display during bootup, and if there's no display connected, it will break the boot process, and that can look a variety of different ways. You might have a frozen boot process, or you might have a frozen boot process on the default tty that you bootup through, and can press cntrl+f1-f7 to switch to a different tty terminal, where you can interact with your system via the command line.

The really basic steps, like getting the right graphics driver, and configuring the basic settings are the main thing that you need to do, besides worrying about all the low level details.

---

### Post by him610 on 2024-04-14
Is this [Beelink Mini S]("https://www.amazon.com/Beelink-4-Cores-Desktop-Computer-Ethernet/dp/B0B12VPNKD?ref_=ast_sto_dp&th=1") your device?

I have a similar mini pc that I normally connect to a monitor; however, there is a TV near it, so whenever I can find the time I will attempt to boot with TV as primary. I use Xubuntu 22.04.4 LTS as only OS installed on it.

---

### Post by emaesen on 2024-04-14
> [COLOR=#000000] if there's no display connected, it will break the boot process[/COLOR]
But isn't it possible to run Linux in a headless server setup?

I'm looking into the graphics drivers...

Meanwhile, I had an idea... booted the MINI S while connected to the ASUS monitor with the Linux Lite USB stick in place and choose live preview. Then when all was booted switched the HDMI cable from ASUS monitor to LG TV. Display came up fine as expected. Now, with the TV connected I choose the Install Linux option from the preview boot. I was hoping that during the install process the TV would be recognized and configured. Install was successful, but after shutdown and restart with the TV connected again no signal to the TV. Booting while connecting to the ASUS monitor and switching HDMI cables to the LG TV still works fine: I see the screen properly on the TV - still no sound though.

Because I can properly see everything on the LG TV (after switching HDMI cable from monitor) doesn't that mean the graphics driver is ok? 

I'm currently in the process of looking through the database on Linux Lite's website to see how other MINI S PCs have been configured - maybe that can give me a clue in the right direction what to change. I'm in a stage of my life where I try to understand the situation first before jumping into a trial-and-error approach... ;)

---

### Post by emaesen on 2024-04-14
> [COLOR=#000000]Is this [/COLOR][Beelink Mini S]("https://www.amazon.com/Beelink-4-Cores-Desktop-Computer-Ethernet/dp/B0B12VPNKD?ref_=ast_sto_dp&th=1")[COLOR=#000000] your device?[/COLOR]
Yes! With 8G/256G/N95 configuration.

---

### Post by him610 on 2024-04-14
Good news, it can be done.

I went down to the basement where my mini pc resides. One has to tinker a little bit with the settings. Not necessary to change anything in BIOS setup. Configuration settings are all in TV and in *buntu Settings > Display

Boot with both PC nonitor and TV monitor connected, mirrowing
[https://imgur.com/DWz4qzil.png]("https://imgur.com/DWz4qzil.png")

Boot to TV Monitor (prime)
[https://imgur.com/1OHaWqDl.png]("https://imgur.com/1OHaWqDl.png")

[COLOR="#FF0000"]Note:[/COLOR] When I tried to go to the imgur links I got a 404 not found.
I will resubmit the before and after screenshots as attachments.

---

### Post by him610 on 2024-04-14
1.  Boot with both PC monitor and TV monitor connected, mirrowing

2.  Boot to TV monitor (prime) with HDMI cable to PC monitor disconnected.

One other thing I should add, mine uses an AMD APU with integrated AMD graphics.
```
hugh@MA90:~$ sudo inxi -CGMxxz
[sudo] password for hugh: 
Machine:
  Type: Mini-pc System: ATOPNUC product: ATOPNUC MA90 v: V1.0
    serial: <filter>
  Mobo: ATOPNUC model: ATOPNUC MA90 v: Version 1.0 serial: <filter>
    UEFI: American Megatrends v: ASB20008 date: 07/19/2022
CPU:
  Info: dual core model: AMD A9-9400 RADEON R5 5 COMPUTE CORES 2C+3G bits: 64
    type: MCP arch: Excavator rev: 0 cache: L1: 192 KiB L2: 2 MiB
  Speed (MHz): avg: 1400 min/max: 1400/2400 boost: enabled cores: 1: 1400
    2: 1400 bogomips: 9581
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] driver: amdgpu v: kernel
    ports: active: HDMI-A-1 empty: DP-1,HDMI-A-2 bus-ID: 00:01.0
    chip-ID: 1002:98e4
  Display: server: X.org v: 1.21.1.4 compositor: xfwm driver: X:
    loaded: ati unloaded: fbdev,modesetting,radeon,vesa gpu: amdgpu
    display-ID: localhost:10.0
  Monitor-1: HDMI-A-1 model: 32S305 res: 1920x1080 dpi: 69
    diag: 815mm (32.1")

```

Note: The screenshot on the left is most recent showing where I booted to TV monitor only.

---

### Post by emaesen on 2024-04-15
ISSUE SOLVED!

I contacted Beelink support and they suggested to install the latest kernel.

[COLOR=#000000][FONT=garamond]I installed the latest linux kernel 6.8.6 using "Mainline Kernels" tool. Although there was a warning about missing dependencies, the install finished. After reboot all looked fine on my monitor. I switched the HDMI cable to my TV, restarted the MINI S and there it worked as well. At first only video, but audio worked as well after changing output settings in the audio mixer. The TV display is now also properly identified in my display settings so I can change the resolution as well if need be.[/FONT][/COLOR]

---

