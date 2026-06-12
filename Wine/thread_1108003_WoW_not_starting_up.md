---
title: "WoW not starting up"
date: 2009-03-27
forum: Wine
---

### Post by SuperNapalm on 2009-03-27
Been using WoW on Ubuntu for a couple weeks now, everything going fairly well. Today I try and open it and it just doesn't work.

Running from the terminal isn't working, just hangs there without opening the game.

```
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!

```
That's what the terminal is saying after running **wine "c:/Program Files/World of Warcraft/Wow.exe"** which i dont understand because it's been working fine before.

Double clicking on the file in the C drive isn't working, tried both the game directly and the launcher.

Any help?

---

### Post by SuperNapalm on 2009-03-27
I should add that I've added nothing to the system except install updates.

Using Wine 1.1.17

---

### Post by Bios Element on 2009-03-27
> **SuperNapalm said:**
> I should add that I've added nothing to the system except install updates.

Using Wine 1.1.17

Since no one has posted, I'd recommend re-installing WoW using it's own wine prefix. I have a tutorial [here]("http://bioselement.endofinternet.net/blog/2009/01/03/wine-world-of-warcraft/") which you can use. But instead of getting the separate installers for Wow and Burning crusade, Just use the all in one. Still haven't had a chance to update the guide. But I've used it every time and it's worked good for me and 3 other people who've said it worked perfectly.

---

### Post by Naiki Muliaina on 2009-03-27
Have you tried asking on the Ubuntu Forums WINE sub forum? Your much more likely to get a usefull response there :)

Linky : [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

WINE based threads in this sub forum either get locked or moved, check the title of the scound sticky thread :)

---

### Post by SuperNapalm on 2009-03-27
I'd rarther not reinstall the whole thing.
Is there some way to explain why it's not opening? Bear in mind it has worked PERFECTLY before i tried running it today.

---

### Post by miikku on 2009-03-28
$ wine Wow.exe
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:powrprof:DllMain (0x7d760000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d760000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!

got what I think the same error at startup, although from what I can see it doesn't return any errors? Yesterday my Wow crashed, and for some reason I couldn't kill the process at all without killing X (ctrl alt backspace, atleast I think this is used to kill X?). Since then this is where the startup of WoW gets stuck. Perhaps it's good to note I'm a bit newb using linux...

But anyway. I've reinstalled Wow and WINE. I've downgraded WINE and tried it as well (ventrilo client bugs with latest WINE) to no avail. I've used the install instructions provided in this thread. Maybe worth noting is that the ventrilo client is starting up fine, so is the WoW launcher app. But when you try to launch the actual game, from the launcher or using Wow.exe directly it prints the above lines and then just stops, seems to be looping or smthng...

If I'm doing anything wrong in particular or if some more info is needed, please tell me how to get the info as well instead of just saying what's needed, since I'm quite new to this as stated. I have played WoW without this bug (?) for about six months. Also, I can't help but thinking that it's got to do with me updating some packages using the built-in manager that pops up from time to time. This has caused WoW to stop working in the past as well. Any suggestions? I'm guessing that not updating your system is really not the right way to go =) Any help is appreciated

Thanks.

---

### Post by hikaricore on 2009-03-28
Have you installed any updates?  Are your video drivers and hardware working properly?

> glxinfo | grep rendering

---

### Post by miikku on 2009-03-28
wow, thanks for the fast response!

it outputs:
direct rendering: Yes

Although at first it seemed to get stuck, and I found Wow.exe in my process list. After killing it I got the desired output. It was running because I tried starting it with the launcher. Even after killing the launcher Wow.exe was running in the background, stuck at the same position, I presume.

Edit:
And no, Wow.exe hasn't been running in earlier atempts :)

Edit2:
About installing updates, yes I have. Although I only clicked apply in the manager, so I don't recall exactly what updates were installed. I was running Wow up until about 19.00 yesterday CET, and it's been like this ever since. Any way to get a list of apps updated?

---

### Post by miikku on 2009-03-28
Ok been googling around for a while without success, but found something that may be of interest. Trying to run Wow.exe causes the process to use ~35% CPU, and ~65% of the CPU is used by Xorg. I have no idea what this means, but perhaps you do :P Also, without changing anything, just restarting terminal, I got much more output in the terminal, but I'm too new to this to interpret it to something of value:

```
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoGetConfigurationInformation, aborting
wine: Unimplemented function ntoskrnl.exe.IoGetConfigurationInformation called at address 0x7b845450 (thread 0015), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoGetConfigurationInformation called in 32-bit code (0x7b8454c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8454c3 ESP:7ec1685c EBP:7ec168c0 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:7ec168e8
 ESI:7ec168e8 EDI:7edecf30
Stack dump:
0x7ec1685c:  7ec168e8 00000008 0000003c 80000100
0x7ec1686c:  00000001 00000000 7b845450 00000002
0x7ec1687c:  7edf4b40 7edf6b3e 57a5ae03 00000000
0x7ec1688c:  7bc42ff7 00000130 00000000 00111160
0x7ec1689c:  7bc41703 7ffd0c00 7ec168b8 00111160
0x7ec168ac:  7bc4202e 7ec168c8 7b84545a 00000000
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x7ec168c0)
  2 0x7edf4ad5 in ntoskrnl (+0x14ad5) (0x7ec168f0)
  3 0x7edecf54 in ntoskrnl (+0xcf54) (0x7ec16918)
  4 0x7eea0f79 in winedevice (+0x10f79) (0x7ec169d8)
  5 0x7ee48aa4 in advapi32 (+0x28aa4) (0x7ec16a28)
  6 0x7bc6c91e call_thread_entry_point+0xe() in ntdll (0x7ec16a38)
  7 0x7bc6df42 in ntdll (+0x5df42) (0x7ec16ad8)
  8 0x7bc6e13d in ntdll (+0x5e13d) (0x7ec173c8)
  9 0xb7db950f start_thread+0xbf() in libpthread.so.0 (0x7ec174c8)
  10 0xb7d35a0e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b8454c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  451e00	Deferred        pgdhdlc.sys
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Export          ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ea9b000-7eb07000	Deferred        msvcrt<elf>
  \-PE	7eab0000-7eb07000	\               msvcrt
ELF	7ec18000-7ec2c000	Deferred        libresolv.so.2
ELF	7ec2c000-7ec42000	Deferred        hal<elf>
  \-PE	7ec30000-7ec42000	\               hal
ELF	7ec42000-7ec61000	Deferred        iphlpapi<elf>
  \-PE	7ec50000-7ec61000	\               iphlpapi
ELF	7ec61000-7ecc4000	Deferred        rpcrt4<elf>
  \-PE	7ec70000-7ecc4000	\               rpcrt4
ELF	7edd5000-7ee0d000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee0d000	\               ntoskrnl
ELF	7ee0d000-7ee60000	Export          advapi32<elf>
  \-PE	7ee20000-7ee60000	\               advapi32
ELF	7ee60000-7ee6c000	Deferred        libnss_files.so.2
ELF	7ee6c000-7ee85000	Deferred        libnsl.so.1
ELF	7ee85000-7ee8e000	Deferred        libnss_compat.so.2
ELF	7ee8f000-7eea4000	Export          winedevice<elf>
  \-PE	7ee90000-7eea4000	\               winedevice
ELF	7efc4000-7efea000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c50000-b7c54000	Deferred        libdl.so.2
ELF	b7c54000-b7db2000	Export          libc.so.6
ELF	b7db3000-b7dcc000	Export          libpthread.so.0
ELF	b7de2000-b7f19000	Deferred        libwine.so.1
ELF	b7f1b000-b7f38000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000015    0 <==
	00000011    0
	00000010    0
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x7ec168c0)
  2 0x7edf4ad5 in ntoskrnl (+0x14ad5) (0x7ec168f0)
  3 0x7edecf54 in ntoskrnl (+0xcf54) (0x7ec16918)
  4 0x7eea0f79 in winedevice (+0x10f79) (0x7ec169d8)
  5 0x7ee48aa4 in advapi32 (+0x28aa4) (0x7ec16a28)
  6 0x7bc6c91e call_thread_entry_point+0xe() in ntdll (0x7ec16a38)
  7 0x7bc6df42 in ntdll (+0x5df42) (0x7ec16ad8)
  8 0x7bc6e13d in ntdll (+0x5e13d) (0x7ec173c8)
  9 0xb7db950f start_thread+0xbf() in libpthread.so.0 (0x7ec174c8)
  10 0xb7d35a0e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoGetCurrentProcess, aborting
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoGetDeviceAttachmentBaseRef, aborting
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoQueryDeviceDescription, aborting
wine: Unimplemented function ntoskrnl.exe.IoQueryDeviceDescription called at address 0x7b845450 (thread 0022), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoQueryDeviceDescription called in 32-bit code (0x7b8454c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8454c3 ESP:7ec1681c EBP:7ec16880 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:7ec168a8
 ESI:7ec168a8 EDI:0045f800
Stack dump:
0x7ec1681c:  7ec168a8 00000008 0000003c 80000100
0x7ec1682c:  00000001 00000000 7b845450 00000002
0x7ec1683c:  7edf4b40 7edf6e66 00000000 00000000
0x7ec1684c:  00000000 00000000 00000000 00000000
0x7ec1685c:  00000000 00000000 00000000 00000000
0x7ec1686c:  00000000 00000000 7b84545a 0000000c
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x7ec16880)
  2 0x7edf4ad5 in ntoskrnl (+0x14ad5) (0x7ec168b0)
  3 0x7eded440 in ntoskrnl (+0xd440) (0x7ec169d8)
  4 0x7ee48aa4 in advapi32 (+0x28aa4) (0x7ec16a28)
  5 0x7bc6c91e call_thread_entry_point+0xe() in ntdll (0x7ec16a38)
  6 0x7bc6df42 in ntdll (+0x5df42) (0x7ec16ad8)
  7 0x7bc6e13d in ntdll (+0x5e13d) (0x7ec173c8)
  8 0xb7e7250f start_thread+0xbf() in libpthread.so.0 (0x7ec174c8)
  9 0xb7deea0e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b8454c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  461e00	Deferred        sentinel.sys
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Export          ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ea9b000-7eb07000	Deferred        msvcrt<elf>
  \-PE	7eab0000-7eb07000	\               msvcrt
ELF	7ec18000-7ec2c000	Deferred        libresolv.so.2
ELF	7ec2c000-7ec42000	Deferred        hal<elf>
  \-PE	7ec30000-7ec42000	\               hal
ELF	7ec42000-7ec61000	Deferred        iphlpapi<elf>
  \-PE	7ec50000-7ec61000	\               iphlpapi
ELF	7ec61000-7ecc4000	Deferred        rpcrt4<elf>
  \-PE	7ec70000-7ecc4000	\               rpcrt4
ELF	7edd5000-7ee0d000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee0d000	\               ntoskrnl
ELF	7ee0d000-7ee60000	Export          advapi32<elf>
  \-PE	7ee20000-7ee60000	\               advapi32
ELF	7ee60000-7ee6c000	Deferred        libnss_files.so.2
ELF	7ee6c000-7ee85000	Deferred        libnsl.so.1
ELF	7ee85000-7ee8e000	Deferred        libnss_compat.so.2
ELF	7ee8f000-7eea4000	Deferred        winedevice<elf>
  \-PE	7ee90000-7eea4000	\               winedevice
ELF	7efc4000-7efea000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d09000-b7d0d000	Deferred        libdl.so.2
ELF	b7d0d000-b7e6b000	Export          libc.so.6
ELF	b7e6c000-b7e85000	Export          libpthread.so.0
ELF	b7e9b000-b7fd2000	Deferred        libwine.so.1
ELF	b7fd4000-b7ff1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000021    0
	0000001b    0
	00000014    0
	00000013    0
	0000000e    0
	0000000d    0
00000018 
	0000001d    0
	0000001c    0
	0000001a    0
	00000019    0
0000001e (D) C:\windows\system32\winedevice.exe
	00000022    0 <==
	00000020    0
	0000001f    0
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x7ec16880)
  2 0x7edf4ad5 in ntoskrnl (+0x14ad5) (0x7ec168b0)
  3 0x7eded440 in ntoskrnl (+0xd440) (0x7ec169d8)
  4 0x7ee48aa4 in advapi32 (+0x28aa4) (0x7ec16a28)
  5 0x7bc6c91e call_thread_entry_point+0xe() in ntdll (0x7ec16a38)
  6 0x7bc6df42 in ntdll (+0x5df42) (0x7ec16ad8)
  7 0x7bc6e13d in ntdll (+0x5e13d) (0x7ec173c8)
  8 0xb7e7250f start_thread+0xbf() in libpthread.so.0 (0x7ec174c8)
  9 0xb7deea0e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoQueryFileDosDeviceName, aborting
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoQueryFileInformation, aborting
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:powrprof:DllMain (0x7c130000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c130000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!

```

Running WINE 1.1.17, Ubuntu 8.10 Intrepid, Kernel Linux-2.6.27-11-generic

AMD Athlon 64 X2 Dual Core 4400+
2GB RAM
ATI x1900xt 512MB (actually not using proprietary drivers, but the latest linux drivers provided by AMD, is this the wrong approach?) - last updated a month ago
~60GB free hd space (using only one partition)


Now and then after updating the system something gets f'd up and I have to spend hours finding fixes, it's getting really tedious. Is there any fail safe way to update your system, and if not, is there a way to revert recent changes? Thanks for the help.


Edit:
Killing Wow.exe causes Xorg CPU usage to fall down to 0% again as well.

---

### Post by SuperNapalm on 2009-03-28
Lucky for you, Launcher isn't working for me at all.

To recap, I've tried launching the game through both icon on desktop, from the C drive and through the terminal. From the shortcut and the C drive it loads up a background downloader (to get data for the upcoming 3.1 patch I presume) but that doesn't really work either. All the methods i try and use to open it just leave it doing nothing although I can see the process in the monitor going between 0 and 16% CPU. As far as I know there's no noticeable slowdown otherwise on the computer.

---

### Post by miikku on 2009-03-28
Being new to this I'm quite sure my reinstallation of both WoW and WINE perhaps wasn't a complete one, so I've uninstalled both, deleting .wine folder and everything. Upon installing wine again there still were some entries of Blizzard in the registry of wine. I used the command
```
sudo apt-get --purge remove wine
```
when uninstalling, and deleted the .wine-folder before reinstalling, yet there were some entries in the registry. Sounds fishy, but maybe expected...

Anyways. I've deleted everything in the registry concerning Blizzard and I'm currently reinstalling WoW. Having no disks at hand I'm using the installer that's downloadable from the homepage, so it will be a while. I'll post here again when it's complete, hopefully it will get fixed this time.

---

### Post by miikku on 2009-03-28
Ok, posting an update on my progress...

Which is none =P After reinstallation however it started the Blizzard Background Downloader, and then crashed at the same point as before. After seeing this I think I saw the downloader when wow crashed during run last time, so perhaps that's the problem. So anyway, I'm currently downloading patch 3.0.9 to 3.1.0 from another mirror, and hopefully it will work around the usage of the background downloader, and perhaps render the game runable again. File is almost 600MB, so it will be another 1.5 hours or so before I can tell wether it's a success or not. But if it is, I'll do a hard facepalm since my ventrilo client is driving me insane. Again :) Perhaps reinstallation wasn't the answer. I'll keep you posted.

---

### Post by SuperNapalm on 2009-03-28
Stop hijacking my thread :P

Would be nice if there's any suggestion on both mine and miikku's problems, as i dont think they're the same.

---

### Post by miikku on 2009-03-28
Oh,terribly sorry, I was convinced that it was the same since our outputs were close to identical. My mistake. But I can at least say that getting the patch for 3.1.0 didn't help in the matter. Good luck anyway ^^

---

### Post by SuperNapalm on 2009-03-29
Bump

---

