---
title: "Wine, Pulseaudio, Hardy, and Simpsons Hit And Run!"
date: 2008-12-22
forum: Wine
---

### Post by hotstovejer on 2008-12-22
Holiday greetings to all my friends here in Open Source Land!

I have a quandry that I need to get resolved.

My children have given me permission to get rid of Windows on the one remaining pc with it on there. I have 3 little ones (and one big one that just won't leave, but that's another story.) 

I got the 2 older kids digging Linux enough, and are sick enough of Windows to let me blow that partition away.

However...

My little one is the gamer in the house. I need to make sure that his games work on Linux. He plays lots of stuff (Pirates of the Carribiean Online, which there is a fix for..., Need for speed, etc), but he loves my old Simpsons Hit and Run game. So do I, so that's why I have been trying to get it to work on my machine (Since when did MY machine become the test machine!?!?!)

The game plays awesome, graphic wise. But, the sound is for crap. No dialogue, intermitten sounds from the game, just lots of hissing and popping.

Now, the dialogue in that game is great. It's part of the experience!

I've heard that it's PulseAudio's fault. Things not playing nice together. I've been thru how to uninstall PA, but it wants to get rid of ubuntu-desktop also. 

So, the question is Do I get rid of PA, disable it, or find some workaround. I want to be Windowsless by the end of the year!

Thanks, all!

Jeremy

---

### Post by idodos on 2008-12-22
you don't have to remove pulse.
just go to the wine configuration utility and set wine to use the OSS sound driver.
then start the game with this command:

padsp wine "game exe"

well i'm quite new to linux myself but i hope this will help you.

---

### Post by hotstovejer on 2008-12-24
Tried that, and got this!

```
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
wine: Unhandled page fault on read access to 0x00000000 at address 0x54cc9f (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0054cc9f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0054cc9f ESP:0032f52c EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:0032f598 ECX:01c8faf8 EDX:001492c0
 ESI:01c8faf8 EDI:0032f578
Stack dump:
0x0032f52c:  01c8fabc 01c8faf8 005f6900 01030000
0x0032f53c:  00000000 00010001 00005dc0 0000bb80
0x0032f54c:  00100002 00040012 00000024 000100e8
0x0032f55c:  00046800 00000000 0032f540 00000000
0x0032f56c:  00000000 00000000 00000000 0054d353
0x0032f57c:  005f6900 0032f598 01c8fabc 01c8fa78
Backtrace:
0x0054cc9f: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (87 modules)
PE	  330000-  347000	Deferred        cmdlineext03
PE	  400000-  7cf000	Export          simpsons
PE	10000000-1006c000	Deferred        pddidx8r
PE	30000000-30072000	Deferred        binkw32
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e112000-7e15c000	Deferred        dsound<elf>
  \-PE	7e120000-7e15c000	\               dsound
ELF	7e3af000-7e3e2000	Deferred        uxtheme<elf>
  \-PE	7e3c0000-7e3e2000	\               uxtheme
ELF	7e3e2000-7e484000	Deferred        oleaut32<elf>
  \-PE	7e3f0000-7e484000	\               oleaut32
ELF	7e484000-7e543000	Deferred        comctl32<elf>
  \-PE	7e490000-7e543000	\               comctl32
ELF	7e543000-7e59c000	Deferred        shlwapi<elf>
  \-PE	7e550000-7e59c000	\               shlwapi
ELF	7e59c000-7e6af000	Deferred        shell32<elf>
  \-PE	7e5b0000-7e6af000	\               shell32
ELF	7e6af000-7e6d5000	Deferred        msacm32<elf>
  \-PE	7e6c0000-7e6d5000	\               msacm32
ELF	7e6d5000-7e6ec000	Deferred        msacm32<elf>
  \-PE	7e6e0000-7e6ec000	\               msacm32
ELF	7e714000-7e71d000	Deferred        libxcursor.so.1
ELF	7e71d000-7e722000	Deferred        libxfixes.so.3
ELF	7e722000-7e725000	Deferred        libxcomposite.so.1
ELF	7e725000-7e72b000	Deferred        libxrandr.so.2
ELF	7e72b000-7e733000	Deferred        libxrender.so.1
ELF	7e733000-7e736000	Deferred        libxinerama.so.1
ELF	7e736000-7e756000	Deferred        imm32<elf>
  \-PE	7e740000-7e756000	\               imm32
ELF	7e756000-7e764000	Deferred        libxext.so.6
ELF	7e764000-7e769000	Deferred        libxxf86vm.so.1
ELF	7e769000-7e77d000	Deferred        midimap<elf>
  \-PE	7e770000-7e77d000	\               midimap
ELF	7e77d000-7e814000	Deferred        winex11<elf>
  \-PE	7e790000-7e814000	\               winex11
ELF	7e85e000-7e87f000	Deferred        libexpat.so.1
ELF	7e87f000-7e8a9000	Deferred        libfontconfig.so.1
ELF	7e8a9000-7e8be000	Deferred        libz.so.1
ELF	7e8be000-7e92b000	Deferred        libfreetype.so.6
ELF	7e93f000-7e958000	Deferred        version<elf>
  \-PE	7e940000-7e958000	\               version
ELF	7e958000-7e96b000	Deferred        libresolv.so.2
ELF	7e96b000-7e97f000	Deferred        lz32<elf>
  \-PE	7e970000-7e97f000	\               lz32
ELF	7e97f000-7e99d000	Deferred        iphlpapi<elf>
  \-PE	7e990000-7e99d000	\               iphlpapi
ELF	7e99d000-7e9fe000	Deferred        rpcrt4<elf>
  \-PE	7e9b0000-7e9fe000	\               rpcrt4
ELF	7e9fe000-7eaa2000	Deferred        ole32<elf>
  \-PE	7ea10000-7eaa2000	\               ole32
ELF	7eaa2000-7eb34000	Deferred        winmm<elf>
  \-PE	7eab0000-7eb34000	\               winmm
ELF	7eb34000-7ec37000	Deferred        wined3d<elf>
  \-PE	7eb50000-7ec37000	\               wined3d
ELF	7ec37000-7ec62000	Deferred        d3d8<elf>
  \-PE	7ec40000-7ec62000	\               d3d8
ELF	7ec62000-7ecb4000	Deferred        advapi32<elf>
  \-PE	7ec70000-7ecb4000	\               advapi32
ELF	7ecb4000-7ed4f000	Deferred        gdi32<elf>
  \-PE	7ecc0000-7ed4f000	\               gdi32
ELF	7ed4f000-7ee96000	Deferred        user32<elf>
  \-PE	7ed70000-7ee96000	\               user32
ELF	7efb6000-7efc1000	Deferred        libnss_files.so.2
ELF	7efc1000-7efcb000	Deferred        libnss_nis.so.2
ELF	7efcb000-7efe3000	Deferred        libnsl.so.1
ELF	7efe3000-7efec000	Deferred        libnss_compat.so.2
ELF	b7b35000-b7b3a000	Deferred        libxdmcp.so.6
ELF	b7b3a000-b7b3d000	Deferred        libxau.so.6
ELF	b7b3d000-b7b55000	Deferred        libxcb.so.1
ELF	b7b56000-b7b58000	Deferred        libxcb-xlib.so.0
ELF	b7b58000-b7c3f000	Deferred        libx11.so.6
ELF	b7c3f000-b7c57000	Deferred        libice.so.6
ELF	b7c57000-b7c5f000	Deferred        libsm.so.6
ELF	b7c5f000-b7c84000	Deferred        libm.so.6
ELF	b7c85000-b7c89000	Deferred        libdl.so.2
ELF	b7c89000-b7c92000	Deferred        librt.so.1
ELF	b7c92000-b7c96000	Deferred        libcap.so.1
ELF	b7c96000-b7ce4000	Deferred        libpulse.so.0
ELF	b7ce4000-b7e33000	Deferred        libc.so.6
ELF	b7e33000-b7e4b000	Deferred        libpthread.so.0
ELF	b7e60000-b7f96000	Deferred        libwine.so.1
ELF	b7f96000-b7fa0000	Deferred        libpulsedsp.so
ELF	b7fa2000-b7fbe000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Vivendi Universal Games\The Simpsons Hit & Run\Simpsons.exe
	00000019   15
	00000018    0
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:

```

I even tried just launching the game again, and no go!

What happened?

Thanks!

Jeremy

---

### Post by hotstovejer on 2008-12-29
Anyone? I was thinking that over the weekend, maybe I should try installing it with sudo? It runs just great, but there is something horribly wrong with the sound. I even went to the measure of installing 7.10 (cause it doesn't have pulseaudio) and trying it that way! Nothing!

Anyone with some ideas, it would be great. Thanks!

Jeremy

---

### Post by KaiZ51 on 2008-12-29
Well, I have something for you that I'm pretty sure that will work. So, first of all, change the Wine audio settings back to ALSA. Then, save it, and close winecfg. Now, open a terminal and write "killall pulseaudio" in it without the quotes. The game should be now working :)

---

### Post by PeteyMcPetenPete on 2009-09-18
Hi guys, well I have the solution that should get this game working flawlessly! It seems to be a bug to do with Wine's DirectX Audio DLL.It works perfectly for me, and hopefully you too! :)

[COLOR="Red"]I have to warn you that this guide can be intrusive to your current wine setup, PROCEED WITH CAUTION! This guide has not broken any other program installed in wine on my end, but it doesn't mean it won't with you![/COLOR]

[LIST=1]
[*]Download DirectX files from [here]("http://zdnana.bay.livefilestore.com/y1py_esrdkCcMWP1E00fSDyMA0s2QW_YXQNJ2PNfoW3UNc3JSfXf9VPMDOBE33V8QVjpS9KMiuLwiLP_fqrJkg1zgHQzHUNakUm/directx.tar.gz?download")
[*]Save it to the root of your home folder
[*]Right click it and choose Extract Here
[*]Load up the terminal
[*]Type in "cd directx" without quotes
[*]Copy and paste the following without quotes, replacing USERNAME with your home folder name "gksu cp *.* /home/USERNAME/.wine/drive_c/windows/system32"
[*]Type in "winecfg"
[*]Click "Add Application"
[*]Navigate to the simpsons hit and run EXE (Simpsons.exe) and select it
[*]Change Windows Version to Windows XP
[*]Select the Libraries tab and create a new entry for "dsound". Edit the new entry to be "Native"
[*]Select the Audio Tab and choose ALSA and OSS, with Sample rate set to "48000"
[*]Finally, check the graphics tab to confirm that shader support is Hardware with Pixel shader ticked
[*]Press Apply then OK and Good luck saving springfield from Aliens!
[/LIST]

---

### Post by sherl0k on 2009-09-21
[PHP]sudo aptitude purge pulseaudio[/PHP]

pulse does three things:

1. per-application volume levels
2. network streaming
3. breaking tons of apps that want to use alsa (wine in particular)

the third it does *extremely* well.

if you can live without the first two, removing pulse is the way to go.

---

