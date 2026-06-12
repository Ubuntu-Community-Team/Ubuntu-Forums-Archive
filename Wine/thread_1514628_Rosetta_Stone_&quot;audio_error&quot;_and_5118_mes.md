---
title: "Rosetta Stone &quot;audio error&quot; and 5118 message..."
date: 2010-06-21
forum: Wine
---

### Post by i_baked_cookies on 2010-06-21
I've been working on fixing this for a few hours now, and I've dug up every thread imaginable trying to resolve this audio issue...

Wine 1.2 rc4
Rosetta Stone 3.4.5
Ubuntu 10.04
Winepulse


Rosetta Stone installed fine though wine, and I added the language .iso without a problem.  When I start the program, it runs fine, but any time I click the volume adjustment bar (in Rosetta Stone), or a little speaker to play a sound, it gives me a dialog box "5118 error," and then another with "5118,5118,5118,5118,5118 error..." and of course it exists the application.

Here's the output when the error occurs... and I'm running Rosetta Stone after I cd to the directory where the .exe is.

```
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
wine client error:39: pipe: Too many open files
err:wave:wodOpen Error open: Input/output error
err:wave:wodOpen Error open: Input/output error
err:winediag:FILE_CreateFile Too many open files, ulimit -n probably needs to be increased
```


I tried all combinations of audio settings in winecfg, and the "test audio" button always works... however, when I have the sound settings window open, and the last tab selected (which shows slider-bars for the volumes of running programs), the "test audio" fails.  

I've also tried reinstalling wine and Rosetta Stone, but I keep having the same issues... I don't really know what to do next.

---

### Post by kiwiot on 2010-07-05
I have the same problem. Used to work fine before I updated Wine.

Wine 1.2 rc6

fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
wine client error:46: pipe: Too many open files
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
ERROR: cannot create wakeup pipe
err:wave:wodOpen Error open: Input/output error
ERROR: cannot create wakeup pipe
err:wave:wodOpen Error open: Input/output error
ERROR: cannot create wakeup pipe
err:wave:wodOpen Error open: Input/output error

---

### Post by peacewithall on 2010-07-06
I had this error too, I suspect rosetta stone is broken in the latest WINE (versions 1.2 and above). I did a lot of googling, and it seems WINE 1.2 is a real mess at the moment, and it seems company's are making it harder to run software via WINE too, only solution for me was to 'downgrade' WINE to the Ubuntu repository supplied version, (version I have is 1.1.42).

---

### Post by Occam's Razor on 2010-10-12
Strange. While running 10.04 and Wine 1.3 (dev), Rosetta Stone worked just fine.

I've recently reinstalled 10.04 and chose to install Wine 1.2.1 and now I'm getting Error 5118

I'm going to try using Wine 1.3 again, and see if that works. If it does, I'll reply and let ppl know.

---

### Post by Occam's Razor on 2010-10-12
K. Just upgraded to Wine 1.3.4 (dev). Audio is working perfectly.

---

### Post by steem on 2011-01-09
I use Rosetta Stone V 3.4.7 and WINE 1.3.11, but i still get this audio error message in terminal. 

Here is the output of the terminal, it seems that there are some more errors:

> osx@ubuntu:~/.wine/drive_c/Programme/Rosetta Stone/Rosetta Stone Version 3$ wine RosettaStoneVersion3.exe
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
fixme:win:EnumDisplayDevicesW ((null),0,0x32f740,0x00000000), stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programme\\Gemeinsame Dateien\\Macrovision Shared\\FLEXnet Publisher\\\\fnp_registrations.xml" 1 4 (nil) (nil) 0x3248440 (nil)
fixme:psapi:EnumDeviceDrivers ((nil), 0, 0x32c4b4): stub
fixme:psapi:EnumDeviceDrivers (0x382daa0, 0, 0x32c4b4): stub
fixme:psapi:EnumDeviceDrivers ((nil), 0, 0x32c258): stub
fixme:psapi:EnumDeviceDrivers (0x382dbb0, 0, 0x32c258): stub
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c10
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x16d748, L"root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xb28e9a4)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:wbemprox:wbem_locator_ConnectServer 0x156018, L"root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xb58e974)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Anwendungsdaten/FLEXnet" 1 1 0x4acfe0 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Anwendungsdaten/FLEXnet" 1 4 (nil) (nil) 0x4b0cf8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Anwendungsdaten/FLEXnet\\rosetta_003da900_event.log" 1 1 0x4b0c40 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Anwendungsdaten/FLEXnet\\rosetta_003da900_tsf.data" 1 1 0x4b0c40 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Anwendungsdaten/FLEXnet" 1 4 (nil) (nil) 0x4b0d50 (nil)


C:\Programme\Rosetta Stone\Rosetta Stone Version 3\support\bin\win\\RosettaStoneLtdServices.exe [v072420082200] 

AUDIO ERROR
AUDIO ERROR

I´ve tested several audio driver settings in Wine, only ALSA-Driver and EsounD-Driver works until I try to log in my user in Rosetta Stone. All other audio driver settings doesn´t work. Rosetta then gives me the message that no audio device was found.

Does anybody have an idea how to get it working?

---

### Post by mrmoney on 2011-01-10
Hey,

I am in the exact same boat. 
AUDIO ERROR
AUDIO ERROR
wine client error:26: pipe: Too many open files

when I try to sign into my user account. Anyone gotten around this?

---

### Post by mrmoney on 2011-01-12
Hey,

anyone make any headway on this?

I've tried Wine 1.1.42, 1.2, 1.3.11. I tried a bunch of audio settings including Alsa, OSS and Wine 1.2 with WinePulse and get the same error regardless. I can boot Rosetta Stone no problem, but I get stuck at at the point of accessing the language course, the only error I get in the terminal is "Audio Error", and Rosetta Stone just hangs.

If anyone is successfully running it, could you please detail me your version and settings for your setup?

Thanks

---

### Post by go_beep_yourself on 2011-01-23
I spoke to Wine developers in #winehq. Ubuntu has patched up the linux kernel so much to the point it's uncertain whether it's even called Linux anymore. Patches are being used also for bleeding edge software not ready for production systems at all, still early in development. That broke real time audio. Boot to an older ubuntu kernel or use a main line linux kernel.

---

### Post by Mia1990 on 2011-01-25
I had the same problem with wine 1.2 you need to upgrade to wine 1.3.11 Rosetta stone works great with that version of wine.

---

### Post by steem on 2011-01-28
I use Wine 1.3.11 already but it doesn´t work :( I really do not know what to do to get rosetta stone working. 
Maybe Vmware or something like that? :S

---

### Post by ktucker on 2011-02-05
With Kernel 2.6.35-22-generic on Maverick and wine 1.2 (via Synaptic 1.2.2-0ubuntu2~maverick2) it worked for me. But I wanted it working on Lucid (LTS) and have succeeded by installing that 2.6.35-22 kernel. Some of the steps below may be unnecessary:

$ sudo gedit /etc/apt/sources.list 

uncomment the back-ports entry and save.

Then via Synaptic install linux-headers-2.6.35-22-generic (which also installs linux-headers-2.6.35-22) and linux-image-2.6.35-22-generic

The latter suggests installing the meta-package:
linux-backports-modules-compat-wireless-2.6.35-lucid-generic
to ensure that upgrades work correctly, and that supporting packages are also installed (I did this but am not sure if it is really necessary or a good idea).

Now, re-comment the back-ports entries in /etc/apt/sources.list to ensure the update manager wont continue to update packages from there.

Try running Rosetta Stone, and if you are lucky it will be fine. In my case it wasn't and I tried a bunch of things before it worked.

In case some default sound setting needed to be reset, via Synaptic I reinstalled gnome-media alsa-base alsa-utils audacity (I don't think this helped). 
I also reinstalled wine1.2 in case it needed to communicate with the new kernel (I don't think this helped either).

Then I experimented with my sound preferences (to ensure input and output were going to/from the headset - using Sound Recorder) and with the settings in wine-cfg.

In winecfg:

under Applications: Windows version: Windows 2000
under Audio: Both "ALSA Driver" and "OSS Driver" are selected (and none of the others).

Hope this helps and that someone knows who to tell to get this working seemlessly in future kernel releases.

---

### Post by tase1 on 2011-10-26
Hi, i recently upgraded to Ubuntu 11.10 and no my microphone isn't working anymore in Rosetta Stone :/. 
I'm using the newest wine version (wine-1.3.31) and i don't know what it could be. 

I would be _really_ glad, if you could help me - i don't want to install Windows . 

thanks!

---

### Post by 1kenthomas on 2011-11-12
Not able to use the immediately above method in 11.10-- AFAIK will not boot from that kernel.

---

### Post by 1kenthomas on 2011-12-11
At this point it seems RS cannot detect microphones under recent kernels on Ubuntu (at least).  Using USB mic and setting microphone manually does not work here -- confirmation from someone else would be appreciated.

At this point I'm running RS under VirtualBox,   where it runs... reasonably.

---

