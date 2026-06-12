---
title: "E-Sword with wine - new update"
date: 2006-12-24
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2006-12-24
Has anyone else tried the new update for e-Sword?  I went ahead and installed it everything works fine.  I also kept having msls31 errors at times.  In short I went to my Windows partition and grabbed the msls31.dll file from the system32 folder and plugged it into my .wine/drive_c/windows/system32 folder, changed the owner, group, and permissions and ran e-Sword.  Out of curiosity, I ran e-Sword and allowed the Strongs # tools tip to work, and it all worked great!!!  Also the book marks.  Oh, there was a wine update I'm running wine-0.9.28.  Wow, wine has really improved since before.  I just thought I would share this with anyone who would like to know.  I have never had e-Sword running this great under wine!  I still can't install new Bibles, but that is another story.

Shane

---

### Post by ksandell on 2006-12-31
I have not tried the update yet - but will do so now based on your post.  I was using a prior version of wine and for the most part it worked fine.  As for installing bibles - I still am running winXP on my laptop and dual booting with hopes of switching completely to linux one day.  With that said I have been using E-Sword for a year on my xp machine and love it and have installed many different bibles and commentaries.  When I tried the install programs under wine  for those modules I noticed it would hang up on the installation.  So I tried going into the programs directory under windows and pulled out the corresponding bible files and commentary files and simply placed them in the e-sword directory under wine on my linux box.  When I restarted wine / e-sword - everything appeared.  I have done that for my memory verses and bible reading files as well.

---

### Post by shane2peru on 2007-01-01
Yes, that works well, just copying and pasting everything from the Windows partition e-Sword directory.  I did find out to install Bibles or other things from wine you need to put it into the wine - e-Sword directory, and then run it, and it installs without a problem.  Also if you run it with the terminal and look for any dll problems, I located them from my Windows side, and copied them into my wine directory, and now everything works great!  Even the Strong's numbers.  The Background even works, however occasionally it hides the text, so I don't use it.

Shane

---

### Post by oeb on 2007-01-05
Shane, et al.,
In Edgy, I installed Wine 0.9.22 using Synaptic.  I then installed e-Sword 7.8.5.  The only way I could get e-Sword to start was through winefiles, however, when started e-Sword will not display any modules at all.  It will not even display the words inside tips.  I put a copy of msls31.dll inside the System32 folder under .wine but to no avail.  Will you be kind enough to set out in detail a howto for newbies trying to get and utilize e-Sword under Wine in Edgy.  Failing that, how about links to any howtos for any versions, etc. that will actually work (I tried Franks's Corner without success).  Thanks in advance for your election to help and, in any event, blessings. oeb

---

### Post by shane2peru on 2007-01-05
> **oeb said:**
> Shane, et al.,
In Edgy, I installed Wine 0.9.22 using Synaptic.  I then installed e-Sword 7.8.5.  The only way I could get e-Sword to start was through winefiles, however, when started e-Sword will not display any modules at all.  It will not even display the words inside tips.  I put a copy of msls31.dll inside the System32 folder under .wine but to no avail.  Will you be kind enough to set out in detail a howto for newbies trying to get and utilize e-Sword under Wine in Edgy.  Failing that, how about links to any howtos for any versions, etc. that will actually work (I tried Franks's Corner without success).  Thanks in advance for your election to help and, in any event, blessings. oeb

Let me see what I can work up.  It may be a week as we quite busy for the next week, and I will have very limited access to my computer.  I think the newest version didn't work correctly.  I will see what I can work up in the next hour or so.  I will double check the newest version too.  They went through some changes and went from version 7.7.7 to 7.8.2 to 7.8.3 to 7.8.5 the 7.8.x changed very rapidly within a few days as a few windows users had problems with the update.  I tried to update to the 7.8.5 and was unable to.  If I can't get it to work I will look for the 7.7.7 version because I know that works fine.

Shane

---

### Post by oeb on 2007-01-05
Great!  I'll be happy to get any help as you can provide same.  BTW, sorry about the repeat of request in e-Sword Group.  I hadn't yet checked your reply here when I caught your post there.  Thanks again and God bless, oeb

---

### Post by shane2peru on 2007-01-06
> **oeb said:**
> Great!  I'll be happy to get any help as you can provide same.  BTW, sorry about the repeat of request in e-Sword Group.  I hadn't yet checked your reply here when I caught your post there.  Thanks again and God bless, oeb

Hey no problem, I was surprised to see you over there!  Well, I submitted my how to to the how to threads.  I guess it needs to be approved by a moderator, so check the how to's forums for anyone interested.  I would think it should be posted shortly.

Shane

---

### Post by shane2peru on 2007-01-06
Ok, this how to can be found [here]("http://www.ubuntuforums.org/showthread.php?t=332566&highlight=e-sword")  It is a how to install e-Sword via wine.  I don't care to try and up keep two of them, so if you need any further help with this please go and post there.  Thanks!

Shane

---

### Post by jagwah on 2007-01-06
Good to know

---

### Post by oeb on 2007-01-06
Success!  Thank you very much.  Do your maps display?  That's the only problem I'm still having.  oeb

---

### Post by shane2peru on 2007-01-06
> **oeb said:**
> Success!  Thank you very much.  Do your maps display?  That's the only problem I'm still having.  oeb

No mine never did work, so when you said that it inspired me to look at it and figure it out, (I love a mental challenge!)  Here is what you need to do in a terminal ```
winecfg
``` click on the library tab, and then in the box type: **oleaut32 **  then click on the add button.  The next time you run e-Sword 1.  it will load faster!  2.  Your maps will work.  

The way I trouble shoot it, is to start the e-Sword program with the command in a terminal, when I find something that doesn't work, or creates a problem, I look at the terminal and see what errors are popping up.  In this case it was an ole error.  In the Library if you type ole and then click the down arrow button, you can see that there are several options.  I just added them all, and then started to eliminate what wasn't needed.  In case anyone is interested.  :-D 

Shane

---

### Post by oeb on 2007-01-07
Terrific!  I tried it running in PuppyLinux, since that's what was booted when I read your post, and it works like a charm.
Did you update your howto?  If you find time to do that it will be a help to those who follow; blessings to you for it.
BTW:   Basically, I followed the instructions you've given in the howto to load and run e-Sword under Puppy as well as other Distros in addition to Ubuntu.  The main difference is that under Puppy there are some strange sources of software, installation procedures, and file locations.  That's only some minor speed bumps, however.
Again, un million de gracias!!!!   oeb (Juzme)

---

### Post by musings on 2007-01-08
Shane,

Thanks for your howto posted here. I get through the first half without a hitch, but copying and then changing permissions on the msls31.dll file doesn't help activate the tool tips for me.

Also, I get a fair few warnings in the terminal window when e-Sword starts up. I presume that's normal?

Regards, Gary

---

### Post by mysticrider92 on 2007-01-08
> Also, I get a fair few warnings in the terminal window when e-Sword starts up. I presume that's normal?

Warnings in the terminal are common, and unless it is a fatal error (very unlikely, and usually not anything to worry about), just ignore it, and go by the performance of the program you are running.

---

### Post by fazza on 2007-01-09
hi, don't know if your trying to use e-sword so you can play aroud with wine, but did you know there is a linux version called gnome-sword? I don't want to sound rude, just thought I'd let you lot know so you don't waste any valuable studuing time! ;)

---

### Post by oeb on 2007-01-09
Ping fazza, 
Some of us have been using e-Sword for years to study various documents that were not at the time available under any other free, electronic Bible study programs.  It is still the case that many of the resources available from the e-Sword using community are not functional in Sword based applications.  Simply put, it was easier in my case (and likely that of many other e-Sword users) to make e-Sword run in Wine than it was to construct Sword modules to run dozens of resources I now call up in e-Sword.  Nevertheless, I acknowledge that it is possible to convert most e-Sword resources to the very different format used by Sword modules, e.g.:

                                      [http://www.cs.cmu.edu/People/karl/sword/](http://www.cs.cmu.edu/People/karl/sword/)

Blessings...

---

### Post by shane2peru on 2007-01-10
> **musings said:**
> Shane,

Thanks for your howto posted here. I get through the first half without a hitch, but copying and then changing permissions on the msls31.dll file doesn't help activate the tool tips for me.

Also, I get a fair few warnings in the terminal window when e-Sword starts up. I presume that's normal?

Regards, Gary


Musings,

It should activate the Strong´s tool tips, where when you use the KJV+ if you move the mouse over the Strong´s number the strong´s definition should pop up in a little box.  If this doesn´t work there is probably a permissions problem.  Go to your .wine/drive c/windows/system32/ directory in the terminal, and do a ```
ls -l *.dll
```  This will display the owner and permissions of all the dll files.  Find the msls31.dll and see what the difference is. I´m not at my Ubuntu machine, but I think all those directories are correct.  Except the one drive c it should have an underscore between the c and drive, but I can´t find it on this keyboard.  Anyway, if you have any difficulty just copy and paste the results of the above command here, and we can get it switched around for you!

Shane

It may take me a day or two to get back to you please be patient.

---

### Post by musings on 2007-01-11
> **shane2peru said:**
> Musings,

[snip]

Find the msls31.dll and see what the difference is. I´m not at my Ubuntu machine, but I think all those directories are correct.  Except the one drive c it should have an underscore between the c and drive, but I can´t find it on this keyboard.  Anyway, if you have any difficulty just copy and paste the results of the above command here, and we can get it switched around for you!

Shane

It may take me a day or two to get back to you please be patient.

Hi Shane,

I checked the onwership & permissions of my msls31.dll and they seem OK so there must be something else at play here. At this stage I'm just glad to have e-Sword running under Linux because it was one of the last things holding up a complete migration.

Regards, Gary

---

### Post by shane2peru on 2007-01-11
Ok, I'm back.  if you want to troubleshoot it we can.  It may take some time doing over the forums.  If you want to just type```
wine ~/.wine/drive_c/Program\ Files/e-Sword/e-Sword.exe 
```  Then enable the tool tips and move your mouse over the tool Strong's number this should crash e-Sword.  When it does copy and paste all the errors in the Terminal here, and we can see what is going on.  It will be the last error, there are usually a lot of 'error' messages in the terminal, but not big problems.   Also are you using Dapper, or Edgy?  Glad to know I can be of help!  I too greatly enjoy E-Sword!

Shane

---

### Post by musings on 2007-01-12
> **shane2peru said:**
> Ok, I'm back.  if you want to troubleshoot it we can.  It may take some time doing over the forums.  If you want to just type```
wine ~/.wine/drive_c/Program\ Files/e-Sword/e-Sword.exe 
```  Then enable the tool tips and move your mouse over the tool Strong's number this should crash e-Sword.  When it does copy and paste all the errors in the Terminal here, and we can see what is going on.  It will be the last error, there are usually a lot of 'error' messages in the terminal, but not big problems.   Also are you using Dapper, or Edgy?  Glad to know I can be of help!  I too greatly enjoy E-Sword!

Shane

Shane,

Here's the terminal output from after e-Sword has started until I enable Strong's Tool Tips and then hover over one of Strong's number:

I'm using Dapper.

Regards, Gary

```

fixme:ole:OLEPictureImpl_Invoke (dispid: 0):Stub
fixme:ole:OleLoadPictureEx (0x7e4bcc54,3334,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x7fb9d510), partially implemented.
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x7cef0fec), stub!
fixme:ole:OLEFontImpl_Invoke property put for Size with vt 3 unsupported!
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:00000000 ESP:7fb9cc94 EBP:7fb9ce24 EFLAGS:00010202(   - 00      - -RI1)
 EAX:000a650c EBX:7d8bdb30 ECX:7fc946dc EDX:00000000
 ESI:7fc946dc EDI:7fb9c1c0
Stack dump:
0x7fb9cc94:  48001b59 00000000 7fb9cda0 48001b19
0x7fb9cca4:  7d8b03e0 48001dc0 7d8b03e0 7fb9d6fc
0x7fb9ccb4:  00000000 7d8bdb30 00009aec 00000000
0x7fb9ccc4:  7fb9ccfc 7ff8df80 00040134 7fa43664
0x7fb9ccd4:  00000020 7fc946dc 7fa5ddc0 00000002
0x7fb9cce4:  7fb9cd24 7fc71b35 7fa5ddc0 7cef10b8
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x00000000 (0x00000000)
fixme:dbghelp:sffip_cb NIY on 'F:\DUMP40\x86\bbt\riched20.opt.pdb'
  2 0x48022b4c in riched20 (+0x22b4c) (0x48022b4c)
  3 0x48014683 in riched20 (+0x14683) (0x48014683)
  4 0x480226f3 in riched20 (+0x226f3) (0x480226f3)
  5 0x7fa1ed3a WINPROC_wrapper+0x1a in user32 (0x7fa1ed3a)
  6 0x7fa1f842 in user32 (+0x9f842) (0x7fa1f842)
  7 0x7fa2313d CallWindowProcA+0x1b5 in user32 (0x7fa2313d)
  8 0x1107f650 in richedit (+0xf650) (0x1107f650)
  9 0x7fa1ed3a WINPROC_wrapper+0x1a in user32 (0x7fa1ed3a)
  10 0x7fa1f842 in user32 (+0x9f842) (0x7fa1f842)
  11 0x7fa2558e CallWindowProcW+0x122 in user32 (0x7fa2558e)
  12 0x7f9ed85c in user32 (+0x6d85c) (0x7f9ed85c)
  13 0x7f9f16c1 SendMessageTimeoutW+0x186 in user32 (0x7f9f16c1)
  14 0x7f9f171e SendMessageW+0x50 in user32 (0x7f9f171e)
  15 0x7f9cf950 in user32 (+0x4f950) (0x7f9cf950)
  16 0x7f9d022f SetFocus+0x135 in user32 (0x7f9d022f)
  17 0x11091f4b in richedit (+0x21f4b) (0x11091f4b)
  18 0x1107f676 in richedit (+0xf676) (0x1107f676)
  19 0x7fa1ed3a WINPROC_wrapper+0x1a in user32 (0x7fa1ed3a)
  20 0x7fa1f842 in user32 (+0x9f842) (0x7fa1f842)
  21 0x7fa2558e CallWindowProcW+0x122 in user32 (0x7fa2558e)
  22 0x7f9ed85c in user32 (+0x6d85c) (0x7f9ed85c)
  23 0x7f9f16c1 SendMessageTimeoutW+0x186 in user32 (0x7f9f16c1)
  24 0x7f9f171e SendMessageW+0x50 in user32 (0x7f9f171e)
  25 0x7f9cf950 in user32 (+0x4f950) (0x7f9cf950)
  26 0x7f9d022f SetFocus+0x135 in user32 (0x7f9d022f)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file DLL\MSVBVM60.dbg ("\xff")
  27 0x6604d59f in msvbvm60 (+0x4d59f) (0x6604d59f)
  28 0x66072200 in msvbvm60 (+0x72200) (0x66072200)
  29 0x6602ada8 in msvbvm60 (+0x2ada8) (0x6602ada8)
  30 0x66034b01 in msvbvm60 (+0x34b01) (0x66034b01)
  31 0x56531055 (0x56531055)
  32 0x00000000 (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (100 modules)
PE      0x00400000-008d2000     Deferred        e-sword
PE      0x0f9a0000-0f9ab000     Deferred        vbajet32
PE      0x0f9c0000-0fa22000     Deferred        expsrv
PE      0x10000000-10013000     Deferred        vsthes6
PE      0x11070000-110ab000     Export          richedit
PE      0x1b000000-1b170000     Deferred        msjet40
PE      0x1b270000-1b2bc000     Deferred        msrd3x40
PE      0x1b2c0000-1b2cd000     Deferred        msjter40
PE      0x1b2d0000-1b2f6000     Deferred        msjint40
PE      0x1b5d0000-1b665000     Deferred        mswstr10
PE      0x1b740000-1b7c8000     Deferred        dao360
PE      0x1b810000-1b84a000     Deferred        msjtes40
PE      0x27580000-27686000     Deferred        mscomctl
PE      0x48000000-4807f000     Export          riched20
PE      0x66000000-66152000     Export          msvbvm60
ELF     0x716b1000-71710000     Deferred        winedos<elf>
  \-PE  0x716c0000-71710000     \               winedos
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7c2bd000-7c2d2000     Deferred        usp10<elf>
  \-PE  0x7c2c0000-7c2d2000     \               usp10
ELF     0x7c2d2000-7c2e6000     Deferred        lz32<elf>
  \-PE  0x7c2e0000-7c2e6000     \               lz32
ELF     0x7c2e6000-7c2ff000     Deferred        version<elf>
  \-PE  0x7c2f0000-7c2ff000     \               version
ELF     0x7ce6f000-7ced0000     Deferred        msvcrt<elf>
  \-PE  0x7ce80000-7ced0000     \               msvcrt
PE      0x7d760000-7d797000     Deferred        vsspell6
ELF     0x7d7f8000-7d86a000     Deferred        wineps<elf>
  \-PE  0x7d820000-7d86a000     \               wineps
ELF     0x7d9c1000-7d9e0000     Deferred        libjpeg.so.62
ELF     0x7df10000-7df5c000     Deferred        libgcrypt.so.11
ELF     0x7df5c000-7df89000     Deferred        libcrypt.so.1
ELF     0x7df89000-7dff2000     Deferred        libgnutls.so.12
ELF     0x7dff2000-7e020000     Deferred        libcups.so.2
ELF     0x7e05c000-7e08d000     Deferred        uxtheme<elf>
  \-PE  0x7e060000-7e08d000     \               uxtheme
ELF     0x7e08d000-7e0b9000     Deferred        winspool<elf>
  \-PE  0x7e0a0000-7e0b9000     \               winspool
ELF     0x7e0b9000-7e179000     Deferred        comctl32<elf>
  \-PE  0x7e0c0000-7e179000     \               comctl32
ELF     0x7e179000-7e1d4000     Deferred        shlwapi<elf>
  \-PE  0x7e190000-7e1d4000     \               shlwapi
ELF     0x7e1d4000-7e2a0000     Deferred        shell32<elf>
  \-PE  0x7e1f0000-7e2a0000     \               shell32
ELF     0x7e2a0000-7e33d000     Deferred        comdlg32<elf>
  \-PE  0x7e2b0000-7e33d000     \               comdlg32
ELF     0x7e370000-7e380000     Deferred        libtasn1.so.2
ELF     0x7eb20000-7eb24000     Deferred        libgpg-error.so.0
ELF     0x7eb4b000-7eb4f000     Deferred        libxfixes.so.3
ELF     0x7eb4f000-7eb58000     Deferred        libxcursor.so.1
ELF     0x7eb58000-7eb74000     Deferred        imm32<elf>
  \-PE  0x7eb60000-7eb74000     \               imm32
ELF     0x7eb74000-7eb7c000     Deferred        libxrender.so.1
ELF     0x7eb7c000-7f33f000     Deferred        libglcore.so.1
ELF     0x7f33f000-7f3c4000     Deferred        libgl.so.1
ELF     0x7f3c4000-7f4aa000     Deferred        libx11.so.6
ELF     0x7f4aa000-7f4c2000     Deferred        libice.so.6
ELF     0x7f4c2000-7f545000     Deferred        winex11<elf>
  \-PE  0x7f4d0000-7f545000     \               winex11
ELF     0x7f545000-7f564000     Deferred        libexpat.so.1
ELF     0x7f564000-7f592000     Deferred        libfontconfig.so.1
ELF     0x7f592000-7f5a6000     Deferred        libz.so.1
ELF     0x7f5a6000-7f60f000     Deferred        libfreetype.so.6
ELF     0x7f60f000-7f6a5000     Deferred        oleaut32<elf>
  \-PE  0x7f630000-7f6a5000     \               oleaut32
ELF     0x7f6a5000-7f6c4000     Deferred        iphlpapi<elf>
  \-PE  0x7f6b0000-7f6c4000     \               iphlpapi
ELF     0x7f6c4000-7f70d000     Deferred        rpcrt4<elf>
  \-PE  0x7f6d0000-7f70d000     \               rpcrt4
ELF     0x7f70d000-7f79e000     Deferred        ole32<elf>
  \-PE  0x7f720000-7f79e000     \               ole32
ELF     0x7f79e000-7f7de000     Deferred        advapi32<elf>
  \-PE  0x7f7b0000-7f7de000     \               advapi32
ELF     0x7f8b3000-7f964000     Deferred        gdi32<elf>
  \-PE  0x7f8d0000-7f964000     \               gdi32
ELF     0x7f964000-7fa90000     Export          user32<elf>
  \-PE  0x7f980000-7fa90000     \               user32
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb3000-7fbb6000     Deferred        libxrandr.so.2
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86vm.so.1
ELF     0x7fbee000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe00000-7fe0a000     Deferred        libgcc_s.so.1
ELF     0x7fe0a000-7fe14000     Deferred        libnss_files.so.2
ELF     0x7fe14000-7fe1d000     Deferred        libnss_nis.so.2
ELF     0x7fe1d000-7fe32000     Deferred        libnsl.so.1
ELF     0x7fe32000-7fe3b000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e60000-b7e62000     Deferred        libnvidia-tls.so.1
ELF     0xb7e68000-b7e6b000     Deferred        libdl.so.2
ELF     0xb7e6b000-b7f9a000     Deferred        libc.so.6
ELF     0xb7f9a000-b7fac000     Deferred        libpthread.so.0
ELF     0xb7fac000-b7faf000     Deferred        libxau.so.6
ELF     0xb7fbb000-b7fd5000     Deferred        libwine.so.1
ELF     0xb7fd8000-b7fee000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\e-Sword\e-Sword.exe
        0000000f    1
        0000000e    1
        0000000d    1
        0000000c    1
        0000000b    1
        0000000a    1
        00000009    0 <==
gary@funhouse:~$
```

---

### Post by shane2peru on 2007-01-12
> **musings said:**
> Shane,

Here's the terminal output from after e-Sword has started until I enable Strong's Tool Tips and then hover over one of Strong's number:

I'm using Dapper.

Regards, Gary


Gary,

  Wow, that is a little over my head.  I guess I was thinking a little too simple.  I have never seen half those errors.  What version of wine are you using.  In the terminal you can type ```
wine --version
``` and it will tell you.  Also do you have any special Graphics type things installed?  or are you just using plain dapper, I mean you don't have Beryl installed or anything like that?  I'm thinking that your wine may be outdated??  

Shane

---

### Post by shane2peru on 2007-01-12
Also for those that are looking for the how to, it is now posted [here.]("http://www.ubuntuforums.org/showthread.php?t=332566&highlight=e-sword")  I also noted that in post Number 8, but in case it was missed.  I will do trouble shooting there.  

(Gary since we already started here, we can just finish out your thread.)

Shane

---

### Post by musings on 2007-01-13
> **shane2peru said:**
> Gary,

  Wow, that is a little over my head.  I guess I was thinking a little too simple.  I have never seen half those errors.  What version of wine are you using.  In the terminal you can type ```
wine --version
``` and it will tell you.  Also do you have any special Graphics type things installed?  or are you just using plain dapper, I mean you don't have Beryl installed or anything like that?  I'm thinking that your wine may be outdated??  

Shane

Hi Shane,

I'm using wine 0.9.9. I have the standard repositories enabled including universe & multiverse. Regarding graphics, nothing special installed that I'm aware of.

Regards, Gary

---

### Post by shane2peru on 2007-01-13
> **musings said:**
> Hi Shane,

I'm using wine 0.9.9. I have the standard repositories enabled including universe & multiverse. Regarding graphics, nothing special installed that I'm aware of.

Regards, Gary

I'm using wine 0.9.29  Are you sure there wasn't a two in there?  If that is so, that rules out all of my suggestions.  If you really interested in getting it fixed you can try posting [here.]("http://groups.google.com/group/comp.emulators.ms-windows.wine?hl=en")  They have been helpful to me.  It is a Google group that helps with wine problems.  I have posted there before.  Sorry I couldn't be of more help. I will have to think and see what I can come up with, if anything.

Shane

---

### Post by musings on 2007-01-13
> **shane2peru said:**
> I'm using wine 0.9.29  Are you sure there wasn't a two in there?  If that is so, that rules out all of my suggestions.  If you really interested in getting it fixed you can try posting [here.]("http://groups.google.com/group/comp.emulators.ms-windows.wine?hl=en")  They have been helpful to me.  It is a Google group that helps with wine problems.  I have posted there before.  Sorry I couldn't be of more help. I will have to think and see what I can come up with, if anything.

Shane

No worries Shane. Thanks for your help getting me to this point. I'll happily run & use e-Sword on Ubuntu.

Regards, Gary

---

### Post by WorkingOnWise on 2007-01-23
Hi all,

I love e-sword! Thanks to everyone who helped me get it working 100% Even the maps!

I also love the windows version of the Sword Project best, but I can live with gnomesword as long as I have my e-sword!

This is for those who don't have windows installed, and need msls31.dll.
I built web sites, and so I need IE6 and 7 to test my work. In the IE7 folder, if you drill down in the windows folder, you will find a host of windows dll's that IE7 needs....including msls31.dll. I was glad I don't need to boot into my wifes laptop (WinXP and Ubuntu CE dual...Windows is only there cuz she's afraid to let it go. She only uses it to watch shows on cbs.com innertube) to get windows files.

Thought I'd throw that out there.
google ies4linux to get the tarball you need to install IE 5.01, 5.5, 6, and or 7. I'm running the last 3...a feat you cant do in xp at all. Anyhow... make sure you get the ver 2.5 beta. It's got a slick gui and the option to install IE7 in behind the "advanced" button. Very slick!

Peace All
Keith

---

### Post by david_kt on 2007-04-08
> **shane2peru said:**
>  I still can't install new Bibles, but that is another story.



I can install everything, just follow my "how to":

[http://ubuntuforums.org/showthread.php?p=2419356#post2419356](http://ubuntuforums.org/showthread.php?p=2419356#post2419356)

DK

---

### Post by shane2peru on 2007-04-08
> **david_kt said:**
> I can install everything, just follow my "how to":

[http://ubuntuforums.org/showthread.php?p=2419356#post2419356](http://ubuntuforums.org/showthread.php?p=2419356#post2419356)

DK

DK,



Nice little how to.  I also have a how to install e-Sword posted.  I guess you can't have too many out there.   [It is here.]("http://ubuntuforums.org/showthread.php?t=332566&highlight=e-Sword")  It is a program in high demand.

Wine has come a long way, and gotten much better.  

Shane

---

### Post by david_kt on 2007-04-08
> **shane2peru said:**
>  I guess you can't have too many out there.   [It is here.]("http://ubuntuforums.org/showthread.php?t=332566&highlight=e-Sword")  It is a program in high demand.
Shane

I have written it before I read your post. But after I compared, it is similar. But you need to add more overrides (oleaut32.dll) in order to run it perfectly (well, almost perfect as I still see some error i.e. fixme:win:LockWindowUpdate, but I don't see any effect on the performance though). Without oleaut32 overrides, it still could run but I saw in terminal it through out a lot of error.

Other thing is that to install module, you need E-sword installed on windows box and copy over to linux. Using my how to, windows box is abolutely not required.

I am still trying to solve the fixme:win:LockWindowUpdate error, but still has no clue yet. After I could solve it, I will update my how to. I also will change the url address to direct link for easy download of required dll.

Regards,
DK

---

### Post by shane2peru on 2007-04-08
Yeah, my how to is a little older, and the version of wine I don't think was as good.  Plus as you stated to install modules on mine, you had to copy them into your e-Sword folder to get them installed.  I haven't given yours a try yet, as I prefer to set back and enjoy the work of others.  I just get the deb and install it.  However if you get things working perfectly, let me know and I will update my how to, and certainly give you the credit for the work.  Once the installer was put together in the deb format, I kind of lost interest, figuring that most will just run the deb, not wanting to dirty their hands with the working of a command line.  It still interests me, but it is kind of like re-inventing the wheel.  Thanks for the info though, I appreciate it.  And if you can get it working perfectly then we need to let Jereme know so that he can get it setup the same way in the deb.  Not to imply it isn't working, but every tweek does help.  

Shane

---

### Post by david_kt on 2007-04-08
> **shane2peru said:**
>  And if you can get it working perfectly then we need to let Jereme know so that he can get it setup the same way in the deb.  Not to imply it isn't working, but every tweek does help.  

Shane

Actually I can say the setup I suggested works perfectly now. The "fixme:win:LockWindowUpdate" error is harmless. Some programmers even does not know how to use this function, or what is this function for in windows. As such, it is not implemented yet in wine. Anyway, I still wanted to give a try if I have time, to play with user32.dll and user32.lib, which is related to LockWindowsUpdate function. But without solving this issue, E-sword should be working perfectly though. Actually I write that "how to" so that many people will try it and feed back to me if they face problems, as I myself do not use all functions. But I dont expect it will give you major issue. And it will not mess up your file system as everything is installed under your /home/user/.wine folder.

DK

---

