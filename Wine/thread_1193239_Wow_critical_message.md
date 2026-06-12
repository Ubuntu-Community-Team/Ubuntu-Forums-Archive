---
title: "Wow critical message?"
date: 2009-06-21
forum: Wine
---

### Post by Adavur on 2009-06-21
Hi.

I use Ubuntu 9.04 Jaunty and I know that similar questions have been asked before, but I can't find any answer.

I have installed World of Warcraft from the online installer from Wow's website and I used the newest beta-version of Wine because older and stabile versions won't let you accept the agreements.
I installed and updated but when I launch Wow it gives me a "critical message" (see scrennshot).

SCREENSHOT:
[http://img38.imageshack.us/img38/9224/skrmbillede.png](http://img38.imageshack.us/img38/9224/skrmbillede.png)

Does enyone know what the problem is?

Mathias

---

### Post by Adavur on 2009-06-21
Maybe I should tell that I can't press the OK-button at the window with the red cross :S!

---

### Post by NightMKoder on 2009-06-21
Video card/drivers? Terminal output?

---

### Post by Adavur on 2009-06-21
Sorry, what do you mean? Which terminal command do you want me to use?

---

### Post by NightMKoder on 2009-06-21
What is your video card & drivers? (IE lspci should tell you)
Terminal output refers to the output you get from running wine from the terminal (at least in this forum).

wine WoW.exe 2>&1 | tee wine.log

or whatever your filename is, will give you the output and also save it in wine.log. 

I don't know WoW though, so you need to replace 'WoW.exe' by however you start WoW (you also have to be in the wow directory)

---

### Post by Adavur on 2009-06-21
Well, I went into Uinstall Wine Software and uninstalled WoW. Then nothing happened and I tried to launch WoW again and it seemed to work fine. I pushed the cinematic trailer button, but after the film was over it gave me the message again :?

Anyway, here is the output of the terminal:

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 6700 XL (rev a2)
02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:05.0 Communication controller: Agere Systems Device 0620

```

---

### Post by NightMKoder on 2009-06-21
Ok, that's lspci, and you have an nvidia card. Either start nvidia-settings or do `cat /proc/driver/nvidia/version` to get the version of the driver.

Still want the wine terminal output...

---

### Post by Adavur on 2009-06-21
> **NightMKoder said:**
> wine WoW.exe 2>&1 | tee wine.log

I just get this (sorry I'm new at Ubuntu :S)

```
wine: could not load L"C:\\windows\\system32\\WoW.exe": Module not found


```

And my Wow.exe is placed in "Homefolder"\.Wine\drive_c\Program Files\World of Warcraft\Wow.exe

---

### Post by NightMKoder on 2009-06-21
Uy, I said to cd into the folder with the file. Here:

```

wine 'C:\Program Files\World of Warcraft\WoW.exe'

```
Assuming that WoW.exe was installed there.

The error message is really a mistake - system32 is the last place wine looks for a file (the first place is your current directory).

---

### Post by Adavur on 2009-06-22
Oh, I'm sorry I don't understand.

Now I changed directory to the World of Warcraft folder and gave the terminal this command:

```
wine "C:\Program Files\World of Warcraft\WoW.exe" 2>&1 | tee wine.log
```

But it just launches the program :S

What do I do wrong?

Ps. This is the output of the *cat /proc/driver/nvidia/version* -command.

```
NVRM version: NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4)
```

---

### Post by noenter1 on 2009-06-22
You didn't do anything. It should be working. Are you still getting the same error message when you start the game that way? Find the log file and post it. If you cant find it just do a search for the file "wine.log".

And FYI you can accept the agreements in all versions of wine by opening up the wow config file and replacing the "0" with a "1" in the correct feilds. Ill get back on later after work with the exact location and file name as I cannot access my computer from work.

Edit: And don't worry about not understanding unix and wine. It will come to you with practice and patience.

---

### Post by K.Y.A on 2009-06-22
WoW requires Windows to have Virtual Memory. This is most likely the issue. You can also try changing your windows version with wineconfig, sometimes that helps. Wine does not have virtual memory and last I checked it can't use swap, but I may be wrong on that. Do you have sufficient memory to run the game? You can also try running the  game in virtualbox....


EDIT: just saw your machine's specs. Nice!!! Not far from mine, lol. You should be able to run the game, no problems. You have enough memory to run Win7 in a virtualmachine. Simply install virtualbox and then use it to install a windows os on top of your Ubuntu one, then u will be able to run ze Wow.

---

### Post by FATMANCHO on 2009-06-22
WoW on WindowsXP requires 512Mb of RAM. As a kind of general rule on running Windows games under WINE, add 25% to the minimum Windows requirements.

---

### Post by noenter1 on 2009-06-22
First im not the one that needed the help. And I don't think Adavur ever gave us his comp specs. I don't mean to distract from the person who is requesting help.

But that aside yes my comp is a gaming comp. I plan on actually upgrading my graphics cards in about 5-6 months to a single GTX 295(water cooled) I also planed on messing with virtual machines as well. I am currently test Windows 7 because I know some close relatives that are wanting to switch to win7(from vista) as soon as it comes out. And that absolutely refuse to switch to any form of unix. I also have a mac book pro I use when I travel. And yes I dump most of my money into my computers.

---

### Post by overdrank on 2009-06-22
> **noenter1 said:**
> First im not the one that needed the help. And I don't think Adavur ever gave us his comp specs. I don't mean to distract from the person who is requesting help.



Correct please lets stay on topic. :) We do not want to highjack the thread.

---

### Post by noenter1 on 2009-06-22
The "Config" file is located in the "WTF" folder in your WoW directory just open it in any text editor. You need to look for these two lines:
```
SET readTOS "0"
SET readEULA "0"
```
Change the "0" in both of these lines to a "1"
This allows you to accept the TOS and EULA in any version of wine. And best of all you don't have to read them!

---

### Post by NightMKoder on 2009-06-22
> **K.Y.A said:**
> WoW requires Windows to have Virtual Memory. This is most likely the issue. You can also try changing your windows version with wineconfig, sometimes that helps. Wine does not have virtual memory and last I checked it can't use swap, but I may be wrong on that. Do you have sufficient memory to run the game? You can also try running the  game in virtualbox....

Virtual memory and swap are two names for the same idea. Wine doesn't manage virtual memory (well it can issue a few "instructions" but it doesn't take care of it) - the linux kernel does. Virtual memory is actually a very old solution to a problem as old as unix :P.

Just FYI: Next time, you can just tell us that you have 180.44 nvidia drivers.

And for the command - yes it launches the program. That's what it's supposed to do. The idea is: it spits some stuff out in the file wine.log and we can help you find the problem if you paste the contents of that file here.

---

### Post by Adavur on 2009-06-24
Thank you for the answers :). I will try it tomorrow. Anyways, here is the post of my wine.log:

```
fixme:mixer:ALSA_MixerInit No master control found on VF0415 Live! Cam Vid. IM Ultra, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebd0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f008,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5dc,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x39f008,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1652f0,0x1651f0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39dee0,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 196 requests (196 known processed) with 325 events remaining.

```

---

### Post by xx58 on 2009-06-28
:confused:I have exactly same error message and I did everything change 0 to 1 , but nothing help. I have Ram memory 4 GB, BUT problem still exist. I try everything. If this problem will be resolved, please leave message. Thanks Just don't know what can I do too??

---

### Post by Adavur on 2009-06-29
Hi again. I've now tried downgrading Wine to the compatible version (should be 1.1.24) and I changed the system to Windows Vista, but nothing happened.
I ran the Wine.log-command again and this is what the terminal gives me:

```
**adavur@Adavur-Ubuntu:~$ wine "C:\Program Files\World of Warcraft\WoW.exe" 2>&1 | tee wine.log**
fixme:mixer:ALSA_MixerInit No master control found on VF0415 Live! Cam Vid. IM Ultra, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f408,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5ec,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df30,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

```

I'm still a new Linux-user, I can't really see if the problem has something to do with my graphic card, a RAM error or if I did somthing wrong through the installation... :(

Are any of you sure which category we're in?

Thank you.

Mathias

---

### Post by noenter1 on 2009-06-29
Well i don't know much about wine, however there are 3 lines that look familiar in the error code to me:

```
fixme:mixer:ALSA_MixerInit No master control found on VF0415 Live! Cam Vid. IM Ultra, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer

```

These errors look like you are missing the ALSA sound drivers. Search syaptyc package manager for the ALSA sound mixers and install the. That should take care of those 3 errors.

And for these errors it looks to me as if your "C:" drive isn't set up in wine: 

```
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
```

---

### Post by noenter1 on 2009-06-29
This many help a bit with some of the sound and display errors:
-----------------------------------
Configuration

Config.wtf

WoW uses DirectX by default, but for most people it will not perform well in this mode. If this is the case for you, then you should change it to run in OpenGL mode instead. To do this you need to find the file wtf/Config.wtf in your main WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name. Note that since .wine begins with a period, you will not be able to see it, but you may still access it in a terminal. In the Nautilus file manager, you can press Ctrl + h to see hidden files. If config.wtf does not exist, run the game and log into a character. The game should then create the file. Open it using a text editor, and add the following line to it:

```
SET gxApi "opengl"
```

If you experience poor performance, graphical glitches, or the game does not run at all, then add the following options as well:

```
SET ffxDeath "0"
SET ffxGlow "0"
```

Note that disabling ffxGlow may also enable antialiasing for some users.

If you experience a problem with missing character and object models, and/or the login windows background is black, add:

```
SET M2UseShaders "0"
```

If you experience stuttering, bad sound or no sound what so ever, then add the following options as well:

```
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
```
-----------------------------------
This was taken from: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by firewall_03 on 2009-07-02
I have the same error, but I don't have another installation to go off of.

---

