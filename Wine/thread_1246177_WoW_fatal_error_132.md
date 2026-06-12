---
title: "WoW fatal error 132"
date: 2009-08-21
forum: Wine
---

### Post by jalehtor on 2009-08-21
I have Wow downloaded under Wine. When I turn it on, the Blizzard logo appears, and then the thing freezes with a This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7E160045


I don't know if Wine's the culprit:

jaleh@jaleh-desktop:~$ sudo wine WoW.exe --opengl
[sudo] password for jaleh: 
wine: /home/jaleh/.wine is not owned by you
jaleh@jaleh-desktop:~$ wine WoW.exe --opengl
wine: could not load L"C:\\windows\\system32\\WoW.exe": Module not found

When I enable hardware drivers for nvidia (accelerated hardware driver version 96) Wine only shows blank boxes with no text, and the WoW screen goes black, though the sound is on, and I get an error notice as well but the box is blank, so i have no idea what it is.

---

### Post by nomnomnom on 2009-08-21
What graphics card do you have?

---

### Post by jalehtor on 2009-08-21
> **nomnomnom said:**
> What graphics card do you have?

nvidia.

---

### Post by nomnomnom on 2009-08-21
> **jalehtor said:**
> nvidia.

Type?

Is it a GeForce 256/2/3/4/FX/6/7/8/9/2XX?

---

### Post by jalehtor on 2009-08-21
> **nomnomnom said:**
> Type?

Is it a GeForce 256/2/3/4/FX/6/7/8/9/2XX?

How do I find out? Can you help me with a terminal command? Sorry! :confused:

---

### Post by nomnomnom on 2009-08-21
> **jalehtor said:**
> How do I find out? Can you help me with a terminal command? Sorry! :confused:

```
lspci
```Then c&p the result here.

---

### Post by mkrahmeh on 2009-08-21
post the output of ```
lspci | grep -i vga
```

---

### Post by nomnomnom on 2009-08-21
> **mkrahmeh said:**
> post the output of ```
lspci | grep -i vga
```

It would help to see all of his system specs.

---

### Post by jalehtor on 2009-08-21
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17GL [Quadro NVS] (rev a3)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)

---

### Post by nomnomnom on 2009-08-21
> **jalehtor said:**
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17GL [Quadro NVS] (rev a3)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)


Oh wow a Quadro? And an old one at that. GeForce 2 stuff.

Without having that card to test with myself, I suggest that you upgrade to something slightly more modern, like a GeForce 6200 at least.

---

### Post by jalehtor on 2009-08-21
> **nomnomnom said:**
> Oh wow a Quadro? And an old one at that. GeForce 2 stuff.

Without having that card to test with myself, I suggest that you upgrade to something slightly more modern, like a GeForce 6200 at least.

Hmmm...do you think this is why I'm getting the 132 error? 

Btw, in case you looked at the Wine info I included: is that alright?

---

### Post by nomnomnom on 2009-08-21
> **jalehtor said:**
> Hmmm...do you think this is why I'm getting the 132 error? 

Btw, in case you looked at the Wine info I included: is that alright?

Actually no I didn't, I'm sorry. For some strange reason you seem to have a permissions problem with your WINE install.

---

### Post by jalehtor on 2009-08-21
> **nomnomnom said:**
> Actually no I didn't, I'm sorry. For some strange reason you seem to have a permissions problem with your WINE install.

Is there a way of fixing that? :confused:

---

### Post by nomnomnom on 2009-08-21
It needs the chmod 777 command, but I haven't used it in so long I have forgotten the exact command... :S

---

### Post by nomnomnom on 2009-08-21
Try;

```
chmod -R 777 /home/jaleh/.wine
```

---

### Post by nomnomnom on 2009-08-21
Also, you may need to sudo it, I can't remember.

```
sudo chmod -R 777 /home/jaleh/.wine
```

---

### Post by jalehtor on 2009-08-21
Thank you so very, very much for trying, but neither of those is working for the permission problems. I'll do some research. There's too much involved here.

---

### Post by nomnomnom on 2009-08-21
> **jalehtor said:**
> Thank you so very, very much for trying, but neither of those is working for the permission problems. I'll do some research. There's too much involved here.

Jaleh is *your* home folder right?

---

### Post by jalehtor on 2009-08-21
Yes, jaleh's my home folder.

---

### Post by theonlyalterego on 2010-04-26
I'm having the same problem as the OP, and would appreciate any help or suggestions.

My Card:
```

ego@ub-top:~$ lspci | grep -i vga
03:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8700M GT] (rev a1)

```

I've noticed that when I start wow from wine, it seems to flip the permissions back to "read only" and I have to switch them back. I've been using the file browser -> properties -> permissions UI to switch grant me ( the owner

I have tried running the chmod command from the terminal, but it doesn't appear to have any different results.


1) -if I start wow via the Launcher, nothing is displayed.
- if I try to use the wine -> "start wow" option a second time, I receive an error:

 could not launch "world of warcraft" failed to change to directory '/home/ego/.wine/dosdevices/c:/World of Warcraft/' (Permission denied)

2) if I try and start wow via the wow.exe file I get the error the OP listed:

World of WarCraft (build 10192)

> 
Exe:      C:\World of Warcraft\wow.exe
Time:     Apr 26, 2010 12:14:32.362 AM
User:     ego
Computer: ub-top
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\World of Warcraft\wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:2004674F

The instruction at "0x2004674F" referenced memory at "0x29E0D76A".
The memory could not be "written".


When I run wow.exe from the terminal it outputs this below, but then will throw the 132 error.
> 
ego@ub-top:~$ wine "c:\World of Warcraft\wow.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed30,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39eb20,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39eff8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f234,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f348,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f50c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f52c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0c4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x191898,0x191798): stub
failed to open C:/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39de90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39deb8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39de3c,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x33fd9c) using GetSystemInfo()
Killed
ego@ub-top:~$ 


---

### Post by theonlyalterego on 2010-04-26
It appears it's only a permissions issue, but it is somehow wine related. I've now been able to start wow by doing the following hack:

open a terminal with two tabs, in one tab type out the sudo command:
```

ego@ub-top:~$ sudo chmod -R 777 /home/ego/.wine

```

in another terminal tab type out the command to start wow using wine:
```

wine "C:\World of Warcraft\wow.exe"

```

hit enter on the 2nd tab to start wow, the wow window will open, so hit alt-tab immediately to return back to the terminal window. In the terminal window switch to the first tab and run the chmod command.

Doing this I was able to start wow, login and view the cinematics before having to apply a new patch. [s]We'll see if it starts up once the patch is done.[/s] It appears this does let me run wow, however it's very annoying to deal with, so I'm still searching for a work-around or fix.

---

### Post by lahook on 2010-04-26
I had the same error on my laptop. My problem was I didn't have the proprietary Nvidia drivers installed. Once they were installed no more problems.

---

