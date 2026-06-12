---
title: "Problem with wine under 11.04"
date: 2011-05-08
forum: Wine
---

### Post by sovsj on 2011-05-08
Just upgraded to Ubuntu 11.04. Everything works flawlessly with the exception of MoneyManager ([http://www.moneysoft.co.uk/update/money%20manager%20business%20edition.exe](http://www.moneysoft.co.uk/update/money%20manager%20business%20edition.exe)) under Wine. All my other applications under Wine haven't suffered. I tried reinstalling 1.2, and I tried 1.3 and 1.0 but all to no effect. 
Running moneymanager under wine1.2 from the terminal I get the dialogbox stating: 'The program winevdm.exe has encountered a serious problem, and needs to close...'
Follows the commandline output. 

Any help would be appreciated.

Samuel


wine: Unhandled exception 0xc000008d at address 0x685e33e9 (thread 0039), starting debugger...
Unhandled exception: denormal float operand in 32-bit code (0x685e3310).
fixme:dbghelp:addr_to_linear Failed to linearize address 1f04:6800 (mode 0)
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:685e3310 ESP:0077e060 EBP:0077e0c8 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000003 EBX:68609ff4 ECX:00000012 EDX:00000003
 ESI:00000003 EDI:00000003
Stack dump:
0x0077e060:  0077e098 0077e124 68609ff4 68609ff4
0x0077e070:  7da5de40 7dac9500 0077e0c8 00000012
0x0077e080:  00000000 00000014 682bc3c0 00000003
0x0077e090:  7da5fdb0 00000003 00000003 7da4e6d0
0x0077e0a0:  00000003 00000003 7da5fdb0 00000003
0x0077e0b0:  00000001 7da518d8 685e329b 68609ff4
Backtrace:
=>0 0x685e3310 in libfontconfig.so.1 (+0x7310) (0x0077e0c8)
  1 0x685e4382 FcConfigSubstituteWithPat+0x191() in libfontconfig.so.1 (0x0077e148)
  2 0x685e48e7 FcConfigSubstitute+0x26() in libfontconfig.so.1 (0x0077e168)
  3 0x686b0057 X11DRV_XRender_SelectFont+0xbd6() in winex11 (0x0077e308)
  4 0x686a8b23 X11DRV_SelectFont+0xac2() in winex11 (0x0077e428)
  5 0x684946b3 in gdi32 (+0x246b2) (0x0077e498)
  6 0x684aaeb2 SelectObject+0xb1() in gdi32 (0x0077e4e8)
  7 0x219c8f6d in user.exe16 (+0x8f6c) (0x0077e5e8)
  8 0x219c9955 DialogBoxParam16+0xc4() in user.exe16 (0x0077e628)
  9 0x219c222b in user.exe16 (+0x222a) (0x0077e648)
  10 0x72d4ef5e in krnl386.exe16 (+0xef5d) (0x0077e678)
  11 0x14c7:0x8672 (0x143f:0xd522)
  12 0x14a7:0x1e63 (0x143f:0xd61a)
  13 0x13d7:0x10c4 (0x143f:0xd744)
  14 0x11df:0xeeae (0x143f:0xd84e)
  15 0x1f04:0x6800 (0x143f:0x0000)
0x685e3310: fstpl	0xffffffe0(%ebp)
Modules:
Module	Address			Debug info	Name (112 modules)
ELF	20000000-2002d000	Deferred        gdi.exe16.so
PE	20010000-2002d000	Deferred        gdi.exe16
ELF	2002d000-20206000	Deferred        shell32<elf>
  \-PE	20040000-20206000	\               shell32
ELF	20206000-20267000	Deferred        shlwapi<elf>
  \-PE	20210000-20267000	\               shlwapi
ELF	20267000-20354000	Deferred        comctl32<elf>
  \-PE	20270000-20354000	\               comctl32
ELF	20354000-203c7000	Deferred        rpcrt4<elf>
  \-PE	20360000-203c7000	\               rpcrt4
ELF	203c7000-203db000	Deferred        win87em.dll16.so
PE	203d0000-203db000	Deferred        win87em.dll16
ELF	203db000-20499000	Deferred        comdlg32<elf>
  \-PE	203e0000-20499000	\               comdlg32
ELF	20499000-204e3000	Deferred        libcups.so.2
ELF	204e3000-20513000	Deferred        libgssapi_krb5.so.2
ELF	20513000-20537000	Deferred        libk5crypto.so.3
ELF	20537000-2053b000	Deferred        libcom_err.so.2
ELF	20733000-207c8000	Deferred        winmm<elf>
  \-PE	20740000-207c8000	\               winmm
ELF	20887000-2089c000	Deferred        keyboard.drv16.so
PE	20890000-2089c000	Deferred        keyboard.drv16
ELF	219aa000-219f1000	Export          user.exe16.so
PE	219c0000-219f1000	Export          user.exe16
ELF	305ec000-30603000	Deferred        commdlg.dll16.so
PE	305f0000-30603000	Deferred        commdlg.dll16
ELF	30824000-30828000	Deferred        libkeyutils.so.1
ELF	3134b000-3135f000	Deferred        mouse.drv16.so
PE	31350000-3135f000	Deferred        mouse.drv16
ELF	31725000-31759000	Deferred        uxtheme<elf>
  \-PE	31730000-31759000	\               uxtheme
ELF	37d65000-37d7a000	Deferred        display.drv16.so
PE	37d70000-37d7a000	Deferred        display.drv16
ELF	3b107000-3b122000	Deferred        spoolss<elf>
  \-PE	3b110000-3b122000	\               spoolss
ELF	43a41000-43a59000	Deferred        shell.dll16.so
PE	43a50000-43a59000	Deferred        shell.dll16
ELF	4be3d000-4be5e000	Deferred        localspl<elf>
  \-PE	4be40000-4be5e000	\               localspl
ELF	50aae000-50ab3000	Deferred        libgpg-error.so.0
ELF	575a3000-57639000	Deferred        libgnutls.so.26
ELF	5850a000-5851f000	Deferred        sound.drv16.so
PE	58510000-5851f000	Deferred        sound.drv16
ELF	58d89000-58e88000	Deferred        ole32<elf>
  \-PE	58da0000-58e88000	\               ole32
ELF	5c5e0000-5c5e8000	Deferred        libkrb5support.so.0
ELF	612e0000-61317000	Deferred        winspool<elf>
  \-PE	612f0000-61317000	\               winspool
ELF	6151f000-61593000	Deferred        libgcrypt.so.11
ELF	62538000-62541000	Deferred        librt.so.1
ELF	6410c000-64118000	Deferred        libavahi-common.so.3
ELF	68000000-6801e000	Deferred        ld-linux.so.2
ELF	6801e000-6815e000	Deferred        libwine.so.1
ELF	6815e000-682bf000	Deferred        libc.so.6
ELF	682bf000-682c3000	Deferred        libdl.so.2
ELF	682c3000-682e9000	Deferred        libm.so.6
ELF	682e9000-682f1000	Deferred        libnss_compat.so.2
ELF	682f1000-68308000	Deferred        libnsl.so.1
ELF	68308000-68314000	Deferred        libnss_files.so.2
ELF	68314000-6832a000	Deferred        winevdm<elf>
  \-PE	68320000-6832a000	\               winevdm
ELF	6832a000-6845c000	Deferred        user32<elf>
  \-PE	68340000-6845c000	\               user32
ELF	6845c000-684e7000	Export          gdi32<elf>
  \-PE	68470000-684e7000	\               gdi32
ELF	684e7000-68541000	Deferred        advapi32<elf>
  \-PE	684f0000-68541000	\               advapi32
ELF	68541000-685c7000	Deferred        libfreetype.so.6
ELF	685c7000-685dc000	Deferred        libz.so.1
ELF	685dc000-6860b000	Export          libfontconfig.so.1
ELF	6860b000-68635000	Deferred        libexpat.so.1
ELF	68635000-686d6000	Export          winex11<elf>
  \-PE	68640000-686d6000	\               winex11
ELF	686d6000-686de000	Deferred        libsm.so.6
ELF	686de000-686f6000	Deferred        libice.so.6
ELF	686f6000-68705000	Deferred        libxext.so.6
ELF	68705000-68820000	Deferred        libx11.so.6
ELF	68820000-68839000	Deferred        libxcb.so.1
ELF	68839000-6883d000	Deferred        libxau.so.6
ELF	6883d000-68843000	Deferred        libxdmcp.so.6
ELF	68843000-68847000	Deferred        libxinerama.so.1
ELF	68847000-6884d000	Deferred        libxxf86vm.so.1
ELF	6884d000-68857000	Deferred        libxrender.so.1
ELF	68857000-6885b000	Deferred        libxcomposite.so.1
ELF	6885b000-68865000	Deferred        libxcursor.so.1
ELF	68865000-6886b000	Deferred        libxfixes.so.3
ELF	6886b000-68880000	Deferred        system.drv16.so
PE	68870000-68880000	Deferred        system.drv16
ELF	68880000-68894000	Deferred        comm.drv16.so
PE	68890000-68894000	Deferred        comm.drv16
ELF	68a31000-68a36000	Deferred        libuuid.so.1
ELF	68cf2000-68d0b000	Deferred        libpthread.so.0
ELF	6a719000-6a7c7000	Deferred        libkrb5.so.3
ELF	6d35b000-6d36c000	Deferred        libtasn1.so.3
ELF	72d31000-72dd0000	Export          krnl386.exe16.so
PE	72d40000-72dd0000	Export          krnl386.exe16
ELF	7320f000-73217000	Deferred        libxrandr.so.2
ELF	7516a000-7518b000	Deferred        imm32<elf>
  \-PE	75170000-7518b000	\               imm32
ELF	76429000-7644d000	Deferred        mpr<elf>
  \-PE	76430000-7644d000	\               mpr
ELF	77035000-77072000	Deferred        libdbus-1.so.3
ELF	788ac000-788bc000	Deferred        libavahi-client.so.3
ELF	7940d000-79422000	Deferred        libresolv.so.2
ELF	7b3a8000-7b3d0000	Deferred        mmsystem.dll16.so
PE	7b3b0000-7b3d0000	Deferred        mmsystem.dll16
ELF	7b800000-7b97c000	Deferred        kernel32<elf>
  \-PE	7b810000-7b97c000	\               kernel32
ELF	7bc00000-7bcba000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7cedf000-7ceea000	Deferred        libnss_nis.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c services.exe
	00000024    0
	0000000e    0
	0000000d    0
00000011 explorer.exe
	00000012    0
00000021 winedevice.exe
	00000026    0
	00000025    0
	00000023    0
	00000022    0
00000030 winevdm.exe
	00000031    0
00000037 (D) C:\windows\system32\winevdm.exe
	00000039    0 <==
	00000038    0
Backtrace:
=>0 0x685e3310 in libfontconfig.so.1 (+0x7310) (0x0077e0c8)
  1 0x685e4382 FcConfigSubstituteWithPat+0x191() in libfontconfig.so.1 (0x0077e148)
  2 0x685e48e7 FcConfigSubstitute+0x26() in libfontconfig.so.1 (0x0077e168)
  3 0x686b0057 X11DRV_XRender_SelectFont+0xbd6() in winex11 (0x0077e308)
  4 0x686a8b23 X11DRV_SelectFont+0xac2() in winex11 (0x0077e428)
  5 0x684946b3 in gdi32 (+0x246b2) (0x0077e498)
  6 0x684aaeb2 SelectObject+0xb1() in gdi32 (0x0077e4e8)
  7 0x219c8f6d in user.exe16 (+0x8f6c) (0x0077e5e8)
  8 0x219c9955 DialogBoxParam16+0xc4() in user.exe16 (0x0077e628)
  9 0x219c222b in user.exe16 (+0x222a) (0x0077e648)
  10 0x72d4ef5e in krnl386.exe16 (+0xef5d) (0x0077e678)
  11 0x14c7:0x8672 (0x143f:0xd522)
  12 0x14a7:0x1e63 (0x143f:0xd61a)
  13 0x13d7:0x10c4 (0x143f:0xd744)
  14 0x11df:0xeeae (0x143f:0xd84e)
  15 0x1f04:0x6800 (0x143f:0x0000)

---

### Post by grege on 2011-05-09
I have the same error with my very old copy of "Microsoft Return to the Arcade"

It has run flawlessly with every version of Wine and every distro since there has been Wine. Now with 11.04 it has stopped working with the same error. 

Same wine version running under Debian Testing and I can happily play Galaxians. Runs fine under Maverick.

Something is missing in 11.04.

ps

tried the PPA version, same problem. It is something else. And same error on my daughters natty running Nvidia so I am guessing it is nothing to do with video drivers (mine is ATI).

---

### Post by grege on 2011-05-09
@sovsj

I fixed my issue by removing wine, removing the PPA and uninstalling ia32-libs. Mine is the 64bit version.

then  sudo apt-get clean

Then I downloaded the Debian Wheezy version of ia32-libs and a version of wine meant for debian from

[http://dev.carbon-project.org/debian/wine-unstable/](http://dev.carbon-project.org/debian/wine-unstable/)

Wine 1.3.19, same version as the one in the Ubuntu PPA.It is compiled for Debian Wheezy and that might mean unforeseen errors under Ubuntu.

Now Galaxian plays

Try this approach at own risk.

---

### Post by dacha on 2011-05-10
This is some kind of regression in libfontconfig:

Old Wine + Natty libfontconfig = crash
New Wine + Natty libfontconfig = crash
Old Wine + Maverick libfontconfig = no crash
New Wine + Maverick libfontconfig = no crash

If you have still have Maverick around, you can even do:

LD_PRELOAD=/path/to/maverick/libfontconfig.so.1 wine /path/to/app.exe

and it won't crash.

Looks like yet another thing Natty succeeded to break. I am investigating.

---

### Post by grege on 2011-05-10
@dacha Your assumption is correct. I restored my machine back to normal Ubuntu Wine and ia32-libs and my daughter's to Wine (32 bit).

I then downloaded the debs for libfontconfig from maverick and extracted libfontconfig.so.1.4.4 from the deb and overwrote the natty libfontconfig.so.1.4.4 in /usr/lib/x86_64-linux-gnu and Wine still not working. Crashed KDE when I changed file and crashed Unity on the 32bit machine, nothing a restart would not fix. The 32 bit machine now has Wine working. 

On the 64bit machine the 32bit libfontconfig.so.1.4.4 from Maverick needs to be copied to /usr/lib32 and now Wine is functioning correctly on the 64bit machine. If I had have thought it through changing the 64bit libfontconfig was unnecessary for a Wine problem.

cheers

---

### Post by sovsj on 2011-05-10
Thanks. Substituting libfontconfig.so.1.4.4 with the Maverick version did the trick.

---

### Post by CKP on 2011-05-11
Apologies for the newbie question - how do I deprecate libfontconfig to Maverick?  I didn't see anything obvious when I right clicked the package in synaptic.  Thanks for any and all advice!

---

### Post by sovsj on 2011-05-12
You can find the libs at [http://packages.ubuntu.com/maverick/libs/libfontconfig1](http://packages.ubuntu.com/maverick/libs/libfontconfig1)
As root, extract the files into the appropriate folder (for me: /usr/lib/i386-linux-gnu). Make sure you backup your the old libs first.

---

### Post by dacha on 2011-05-12
> **dacha said:**
> This is some kind of regression in libfontconfig:
If you have still have Maverick around, you can even do:

LD_PRELOAD=/path/to/maverick/libfontconfig.so.1 wine /path/to/app.exe

and it won't crash.

Looks like yet another thing Natty succeeded to break. I am investigating.

Disassembling the Natty libfontconfig wasn't very productive, as the assembly is so well optimized that matching it with the corresponding source code is virtually impossible. GDB is unable to show in which function the crash happens either.

There is no 32 bit debug libraries for libfontconfig in ia32-libs. I tried to build them, but the debian build tools can't easily be set up to build 32 bit libraries on an x86_64 system.

The same version of libfontconfig (2.8.0) is used in both Natty and Maverick packages. There is no major change to the build scripts and there is no patches to the source code itself in either version, which leads me to believe that this could be a GCC bug.

Can somebody on an i686 Natty installation please install the debug packages for libfontconfig and get a full backtrace?

---

### Post by craterib on 2011-05-17
Hello,

After making the changes given in this forum, the program starts but it crashes after a few minutes. This problem did not occur in Ubuntu 10.10. 

The program's name is Sobotta Atlas of Anatomy. I am running the 32 bit edition of Ubuntu with Gnome 3.

Where is the problem? Ubuntu? Gnome?

Please help

---

### Post by New00Folder on 2011-05-29
> **sovsj said:**
> You can find the libs at [http://packages.ubuntu.com/maverick/libs/libfontconfig1](http://packages.ubuntu.com/maverick/libs/libfontconfig1)
As root, extract the files into the appropriate folder (for me: /usr/lib/i386-linux-gnu). Make sure you backup your the old libs first.
Am I really supposed to extract the .deb file I got from the link?
Or do I install it?

---

### Post by bdoe on 2011-08-14
I just wanted to add that I encountered the same issue as the OP when I tried to run SimTower (a 16-bit application) on Wine 1.2.2 on Mint 11 i386 (based on Ubuntu 11.04). Following the suggestion of replacing libfontconfig with the one from the Maverick archive fixed my problem.

Hope this helps pinpoint the problem.

---

### Post by tkoco on 2011-09-18
Ok. I had the same problem as described above (winevdm.exe ...) If you run the 64bit version of natty (11.04), YOU ONLY NEED TO OVERWRITE THE 32 BIT LIBRARY FILES! (Some emphasis there) If you decide to overwrite the 64 bit library files, the desktop will crash and then you will not be able to start up the desktop. You have been warned. 8-)

---

### Post by _____ on 2011-10-12
Sometimes this community is really discouraging. How is this considered solved? Someone please describe how to fix this issue in greater detail. Two sentences is not a valid explaination for a process that contains a lot of steps. No one even knows why it's doing this.

---

### Post by deyka on 2011-10-30
I had the same error message: 'The program winevdm.exe has encountered a serious problem, and needs to close...'
I'm running the 64-bit version of Natty and I did as suggested by Grege and now the problem is gone. 
The only thing to do is to copy the **32bit** *libfontconfig.so.1.4.4* from Maverick to /usr/lib32 
I downloaded the file from here (the i386 version, not the other one)
[http://packages.ubuntu.com/maverick/libs/libfontconfig1]("http://packages.ubuntu.com/maverick/libs/libfontconfig1")
Then I extracted the compressed file, I copied the *libfontconfig.so.1.4.4* file and pasted it in /usr/lib32
And that's it.

Thank you, Grege!

---

### Post by meithan on 2012-04-08
This thread just solved my problem, thank you!

So, I thought I'd post a detailed, newbie guide of the solution, for anyone that runs into this thread in the future. Here goes.

**The Solution**

_Disclaimer_: This solution involves overwriting an installed library in your system with an older version. This might cause some applications to stop working or break your system altogether. While my system is just fine after doing this, I can't guarantee yours will be too. **Proceed at your own risk**.

1) **Download** the Maverick *libfontconfig1* package here:

[http://packages.ubuntu.com/maverick/i386/libfontconfig1/download]("http://packages.ubuntu.com/maverick/i386/libfontconfig1/download")

Just click on any of the mirrors to start downloading the .deb package.

2) **Extract** the files on the package. This can be done by opening a terminal, navigating to where the .deb file was downloaded, and then typing:

```
dpkg-deb -x libfontconfig1_2.8.0-2ubuntu1_i386.deb libfontconfig
```

A directory named 'libfontconfig' will be created in the current directory, with all the package files in it. Navigate to ./usr/lib in that dir:

```
cd ./libfontconfig/usr/lib
```

You should see (type 'ls') three files in there. The file 'libfontconfig.so.1.4.4' is the one we need.

3) Before overwriting the library file in your system, we're going to **back it up**. Type in the terminal:

```
sudo cp /usr/lib32/libfontconfig.so.1.4.4 /usr/lib32/libfontconfig.so.1.4.4.bak
```

You'll need to type in your user password in this step.

4) Now **copy** the library you downloaded into your /usr/lib32 directory:

```
sudo cp libfontconfig.so.1.4.4 /usr/lib32
```

**That should do it**. This fixed my wine problems. So far no other application seems to be affected, and my system works as usual. If it solved your issued too, thank the people in this thread.

---

### Post by FactTech on 2012-11-05
Just a note for anyone still trying to follow the newbie instructions provided by meithan: The link provided for downloading the maverick libfontconfig1 package is no longer active.

The file can still be found at:

[http://archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/](http://archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/)

---

