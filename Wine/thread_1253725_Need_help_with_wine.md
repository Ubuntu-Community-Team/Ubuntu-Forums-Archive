---
title: "Need help with wine"
date: 2009-08-30
forum: Wine
---

### Post by raggisnorra on 2009-08-30
Hi,

I'm a complete beginner on Ubuntu (or Linux for that matter), so you guys have to bare with my stupidity for a bit.

I installed wine couple of weeks ago so I could open Football Manager 08 (FM) and Full Tilt poker, which were already installed on the "windows side" on my computer. I had no problems at all until recently.

First I started getting an error message when I was trying to open FM (I cant remember exactly what it said but it was somewhere on the lines of "your system does not meet the minimum requirements to run this program"). At that point I could open Full Tilt. After trying to read about it on-line and trying plenty of suggestions I gave up and decided to uninstall and delete everything Wine related that i could find. After reinstalling it (and repeating this proses 2 or 3 times) the same thing always happens when I try opening these two programs = NOTHING, not even an error message. 

Also what really annoys me is when I click "open with other applications" I get a list of like million applications where more then half are "A wine application" and then there is only one "Wine windows program loader" which seems to me that doesn't work.

If you wasted your time reading all this I'll have to thank you in advance whether you can help or not.

---

### Post by ackanao on 2009-08-30
You need to get familiar with Wine, then you can expect better results; First, there's no need for uninstalling Wine - if you messed up something, just delete **.wine** folder and create it again; To recreate default wineprefix (**.wine** folder) fire up terminal and type:

```
winecfg
```

If you want to use Windows applications on Linux it's recommended to  install them with Wine - copying installation folder from Windows install to Wine folders may or may not work (usually it will not work as expected but there are some exceptions).

It's not recommended to run applications from an existing Windows partitions - although it's possible and some programs may work there's a risk of corrupting your Windows installation (Windows Registry) so it's better to avoid that.

Basically, if you want to use Windows applications just install them with Wine.

About your "Open With" dialog box:

Backup your **"~/.local/share/applications**" folder (just copy it somewhere else); This folder is hidden and located in your "home" directory.

Then delete all "**wine-extension-desktop**" files - if everything went well you can delete your backup folder.

These links may help you:

Wine User Guide:
[http://www.winehq.org/docs/wineusr-guide/index]("http://www.winehq.org/docs/wineusr-guide/index")

Wine FAQ:
[http://wiki.winehq.org/FAQ]("http://wiki.winehq.org/FAQ")

---

### Post by raggisnorra on 2009-08-30
Thanks ackanao, this did not however completely help me. I have re-installed the game using wine so that its on my Ubuntu partition. The same problem occurs as before, I opened however my system monitor where I could see that the game was running (using a ton of my cpu) but still I see nothing. I had been opening the game with no problems for 2 weeks and now suddenly this happens. 

Thanks again, the "open with" dialog box looks sooooo much better now.

---

### Post by ackanao on 2009-08-30
Which version of Ubuntu and which version of Wine do you use? Could you start the game from a terminal and post terminal output so we can see what's the problem?

---

### Post by raggisnorra on 2009-08-30
Ubuntu 9.04 - the jaunty jackalope
Wine 1.0.1

terminal output for fulltilt:

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc45ee0

terminal output for football manager:

fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x336a520,0x00000004,0x336a51c) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x336940c): Stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3369258,0x00000000), stub!
wine: Unhandled page fault on write access to 0x003f2000 at address 0x27c1778 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x003f2000 in 32-bit code (0x027c1778).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:027c1778 ESP:0336a8e0 EBP:0336a8f0 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:ffffffff ECX:3fff3801 EDX:00000003
 ESI:003c0000 EDI:003f1ffe
Stack dump:
0x0336a8e0:  0336a924 0336ad2c 003c0006 48590000
0x0336a8f0:  0336ad3c 027bbf27 003c0006 ffffffff
0x0336a900:  02ca5b80 00000000 0335cfba 02effe3c
0x0336a910:  02f5d000 00000001 00000000 00032000
0x0336a920:  00000030 5c3f3f5c 756c6f56 307b656d
0x0336a930:  30303030 2d303030 30303030 3030302d
Backtrace:
=>1 0x027c1778 in fm (+0x23c1778) (0x0336a8f0)
  2 0x027bbf27 in fm (+0x23bbf27) (0x0336ad3c)
  3 0x0284619f in fm (+0x244619f) (0x0337f93c)
  4 0x026e5116 in fm (+0x22e5116) (0x0337fdbc)
  5 0x00000008 (0x028a3568)
0x027c1778: repe stosl    %es:(%edi)
Modules:
Module    Address            Debug info    Name (122 modules)
PE      400000- 3075000    Export          fm
ELF    7b800000-7b93d000    Deferred        kernel32<elf>
  \-PE    7b820000-7b93d000    \               kernel32
ELF    7bc00000-7bca7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bca7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cb1e000-7cc33000    Deferred        wined3d<elf>
  \-PE    7cb30000-7cc33000    \               wined3d
ELF    7cc33000-7cc64000    Deferred        d3d9<elf>
  \-PE    7cc40000-7cc64000    \               d3d9
ELF    7cc64000-7cc68000    Deferred        libgpg-error.so.0
ELF    7cc68000-7ccd1000    Deferred        libgcrypt.so.11
ELF    7ccd1000-7cce3000    Deferred        libtasn1.so.3
ELF    7cce3000-7cd07000    Deferred        libk5crypto.so.3
ELF    7cd07000-7cd99000    Deferred        libkrb5.so.3
ELF    7cd99000-7ce36000    Deferred        libgnutls.so.26
ELF    7ce36000-7ce61000    Deferred        libgssapi_krb5.so.2
ELF    7ce61000-7ce98000    Deferred        libcups.so.2
ELF    7d235000-7d23e000    Deferred        libkrb5support.so.0
ELF    7d266000-7d299000    Deferred        uxtheme<elf>
  \-PE    7d270000-7d299000    \               uxtheme
ELF    7d299000-7d2ae000    Deferred        midimap<elf>
  \-PE    7d2a0000-7d2ae000    \               midimap
ELF    7d2ae000-7d2d6000    Deferred        msacm32<elf>
  \-PE    7d2b0000-7d2d6000    \               msacm32
ELF    7d2d6000-7d2ef000    Deferred        msacm32<elf>
  \-PE    7d2e0000-7d2ef000    \               msacm32
ELF    7daf0000-7daf6000    Deferred        libattr.so.1
ELF    7daf6000-7dafd000    Deferred        libgdbm.so.3
ELF    7dafd000-7db5c000    Deferred        libpulse.so.0
ELF    7db5c000-7dc24000    Deferred        libasound.so.2
ELF    7dc24000-7dc28000    Deferred        libkeyutils.so.1
ELF    7dc31000-7dc35000    Deferred        libcom_err.so.2
ELF    7dc35000-7dc6c000    Deferred        winealsa<elf>
  \-PE    7dc40000-7dc6c000    \               winealsa
ELF    7de7c000-7e0c1000    Deferred        r300_dri.so
ELF    7e0c1000-7e0ca000    Deferred        libxcursor.so.1
ELF    7e0ca000-7e0ce000    Deferred        libxcomposite.so.1
ELF    7e0ce000-7e0d6000    Deferred        libxrandr.so.2
ELF    7e0d6000-7e0e0000    Deferred        libxrender.so.1
ELF    7e0e2000-7e0e7000    Deferred        libcap.so.2
ELF    7e0e7000-7e0ee000    Deferred        libasound_module_pcm_pulse.so
ELF    7e0f1000-7e18c000    Deferred        winex11<elf>
  \-PE    7e100000-7e18c000    \               winex11
ELF    7e1eb000-7e212000    Deferred        libexpat.so.1
ELF    7e212000-7e23f000    Deferred        libfontconfig.so.1
ELF    7e23f000-7e242000    Deferred        libxinerama.so.1
ELF    7e250000-7e266000    Deferred        libz.so.1
ELF    7e266000-7e2dd000    Deferred        libfreetype.so.6
ELF    7e2dd000-7e2f8000    Deferred        wsock32<elf>
  \-PE    7e2e0000-7e2f8000    \               wsock32
ELF    7e2f8000-7e30d000    Deferred        lz32<elf>
  \-PE    7e300000-7e30d000    \               lz32
ELF    7e30d000-7e328000    Deferred        version<elf>
  \-PE    7e310000-7e328000    \               version
ELF    7e328000-7e3ce000    Deferred        oleaut32<elf>
  \-PE    7e340000-7e3ce000    \               oleaut32
ELF    7e3ce000-7e405000    Deferred        winspool<elf>
  \-PE    7e3e0000-7e405000    \               winspool
ELF    7e405000-7e4ca000    Deferred        comctl32<elf>
  \-PE    7e410000-7e4ca000    \               comctl32
ELF    7e4ca000-7e525000    Deferred        shlwapi<elf>
  \-PE    7e4e0000-7e525000    \               shlwapi
ELF    7e525000-7e639000    Deferred        shell32<elf>
  \-PE    7e540000-7e639000    \               shell32
ELF    7e639000-7e6e7000    Deferred        comdlg32<elf>
  \-PE    7e640000-7e6e7000    \               comdlg32
ELF    7e6e7000-7e6fc000    Deferred        wtsapi32<elf>
  \-PE    7e6f0000-7e6fc000    \               wtsapi32
ELF    7e6fc000-7e729000    Deferred        ws2_32<elf>
  \-PE    7e700000-7e729000    \               ws2_32
ELF    7e729000-7e73f000    Deferred        libresolv.so.2
ELF    7e73f000-7e75e000    Deferred        iphlpapi<elf>
  \-PE    7e750000-7e75e000    \               iphlpapi
ELF    7e75e000-7e7c1000    Deferred        rpcrt4<elf>
  \-PE    7e770000-7e7c1000    \               rpcrt4
ELF    7e7c1000-7e867000    Deferred        ole32<elf>
  \-PE    7e7d0000-7e867000    \               ole32
ELF    7e867000-7e8fb000    Deferred        winmm<elf>
  \-PE    7e870000-7e8fb000    \               winmm
ELF    7e8fb000-7e947000    Deferred        dsound<elf>
  \-PE    7e900000-7e947000    \               dsound
ELF    7e947000-7e968000    Deferred        imm32<elf>
  \-PE    7e950000-7e968000    \               imm32
ELF    7e968000-7ea08000    Deferred        gdi32<elf>
  \-PE    7e980000-7ea08000    \               gdi32
ELF    7ea08000-7eb54000    Deferred        user32<elf>
  \-PE    7ea20000-7eb54000    \               user32
ELF    7eb54000-7eb5d000    Deferred        librt.so.1
ELF    7eb5d000-7eb62000    Deferred        libxdmcp.so.6
ELF    7eb62000-7eb6c000    Deferred        libdrm.so.2
ELF    7eb6c000-7eb71000    Deferred        libxfixes.so.3
ELF    7eb71000-7eb8b000    Deferred        libxcb.so.1
ELF    7eb8b000-7eb8f000    Deferred        libxau.so.6
ELF    7eb8f000-7ebf2000    Deferred        libgl.so.1
ELF    7ebf2000-7ece1000    Deferred        libx11.so.6
ELF    7ece1000-7ecf1000    Deferred        libxext.so.6
ELF    7ecf1000-7ed09000    Deferred        libice.so.6
ELF    7ed09000-7ed12000    Deferred        libsm.so.6
ELF    7ed23000-7eda5000    Deferred        opengl32<elf>
  \-PE    7ed40000-7eda5000    \               opengl32
ELF    7eda5000-7edbb000    Deferred        psapi<elf>
  \-PE    7edb0000-7edbb000    \               psapi
ELF    7edbb000-7ee07000    Deferred        dbghelp<elf>
  \-PE    7edc0000-7ee07000    \               dbghelp
ELF    7ee07000-7ee5a000    Deferred        advapi32<elf>
  \-PE    7ee10000-7ee5a000    \               advapi32
ELF    7ee5a000-7ee6f000    Deferred        faultrep<elf>
  \-PE    7ee60000-7ee6f000    \               faultrep
ELF    7ef99000-7efa5000    Deferred        libnss_files.so.2
ELF    7efa5000-7efb0000    Deferred        libnss_nis.so.2
ELF    7efb0000-7efc9000    Deferred        libnsl.so.1
ELF    7efc9000-7efef000    Deferred        libm.so.6
ELF    7efef000-7eff2000    Deferred        libxdamage.so.1
ELF    7eff2000-7eff7000    Deferred        libuuid.so.1
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    b7c30000-b7c36000    Deferred        libxxf86vm.so.1
ELF    b7c37000-b7c3b000    Deferred        libdl.so.2
ELF    b7c3b000-b7d9e000    Deferred        libc.so.6
ELF    b7d9f000-b7db8000    Deferred        libpthread.so.0
ELF    b7dc9000-b7f00000    Deferred        libwine.so.1
ELF    b7f02000-b7f20000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Sports Interactive\Football Manager 2008\fm.exe
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
=>1 0x027c1778 in fm (+0x23c1778) (0x0336a8f0)
  2 0x027bbf27 in fm (+0x23bbf27) (0x0336ad3c)
  3 0x0284619f in fm (+0x244619f) (0x0337f93c)
  4 0x026e5116 in fm (+0x22e5116) (0x0337fdbc)
  5 0x00000008 (0x028a3568)

---

### Post by NightMKoder on 2009-08-30
Update to the latest wine (1.1.28)

---

### Post by raggisnorra on 2009-08-31
THank you guys so much!!! I finally can use my computer doing something not productive at all haha.

Cheers!

---

