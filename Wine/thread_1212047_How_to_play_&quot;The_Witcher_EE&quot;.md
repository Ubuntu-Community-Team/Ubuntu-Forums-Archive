---
title: "How to play &quot;The Witcher EE&quot; ?"
date: 2009-07-13
forum: Wine
---

### Post by MaximB on 2009-07-13
Hello !

I don't generally use Wine so I don't know all the tricks.
I've installed "The Witcher EE" but it won't play...
(I get the errors once I get home).

Is there a step-by-step guide on how to install "The Withcer EE" ?

Using Ubuntu 9.04 64-bit.

---

### Post by MaximB on 2009-07-13
Update :

When I try to run the game as my user I get :

```
maximb@MaximB-HQ:~/Games/the witcher/The Witcher Enhanced Edition/System$ wine witcher.exe                                             
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x114000 0                                                                                    
wine: Unhandled page fault on write access to 0x00663000 at address 0x7bc46aa1 (thread 0027), starting debugger...                     
Unhandled exception: page fault on write access to 0x00663000 in 32-bit code (0x7bc46aa1).                                             
Register dump:                                                                                                                         
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b                                                                                       
 EIP:7bc46aa1 ESP:0064e690 EBP:0064e6d8 EFLAGS:00010246(  R- --  I  Z- -P- )                                                           
 EAX:00000ffe EBX:7bc94ff4 ECX:00000000 EDX:00662000                                                                                   
 ESI:006701da EDI:00250000                                                                                                             
Stack dump:                                                                                                                            
0x0064e690:  0066ff70 0064e764 0064e6b8 7b8a008e                                                                                       
0x0064e6a0:  ffffffff 0064e6c4 0064e6c8 00000040                                                                                       
0x0064e6b0:  00640025 0066ff70 0064e6d8 7b8a00fa                                                                                       
0x0064e6c0:  ffffffff 00662000 00001000 7ee8fff4                                                                                       
0x0064e6d0:  0066ff70 0064e764 0064e778 7ee8d9b1                                                                                       
0x0064e6e0:  00662000 00000132 0066ff78 00250000                                                                                       
Backtrace:                                                                                                                             
=>0 0x7bc46aa1 LdrProcessRelocationBlock+0xc1() in ntdll (0x0064e6d8)                                                                  
  1 0x7ee8d9b1 in winedevice (+0xd9b1) (0x0064e778)                                                                                    
  2 0x7ee8dd07 in winedevice (+0xdd07) (0x0064e9f8)                                                                                    
  3 0x7ee8e326 in winedevice (+0xe326) (0x0064ea48)                                                                                    
  4 0x7ee38e0c in advapi32 (+0x28e0c) (0x0064ea98)                                                                                     
  5 0x7bc6c338 call_thread_func+0xc() in ntdll (0x0064eaa8)                                                                            
  6 0x7bc6c540 call_thread_entry_point+0x70() in ntdll (0x0064eb78)                                                                    
  7 0x7bc7481b in ntdll (+0x6481b) (0x0064f3b8)                                                                                        
  8 0xf7da84ff start_thread+0xbf() in libpthread.so.0 (0x0064f4b8)                                                                     
  9 0xf7d24b9e __clone+0x5e() in libc.so.6 (0x00000000)                                                                                
0x7bc46aa1 LdrProcessRelocationBlock+0xc1 in ntdll: addl        %edi,0x0(%edx,%eax,1)                                                  
Modules:                                                                                                                               
Module  Address                 Debug info      Name (26 modules)                                                                      
PE        650000-  672000       Deferred        sshdrv65.sys                                                                           
ELF     7b800000-7b954000       Deferred        kernel32<elf>                                                                          
  \-PE  7b820000-7b954000       \               kernel32                                                                               
ELF     7bc00000-7bcb1000       Export          ntdll<elf>                                                                             
  \-PE  7bc10000-7bcb1000       \               ntdll                                                                                  
ELF     7bf00000-7bf04000       Deferred        <wine-loader>                                                                          
ELF     7ece5000-7ed54000       Deferred        msvcrt<elf>                                                                            
  \-PE  7ed00000-7ed54000       \               msvcrt                                                                                 
ELF     7ed54000-7edc1000       Deferred        rpcrt4<elf>                                                                            
  \-PE  7ed60000-7edc1000       \               rpcrt4                                                                                 
ELF     7edc1000-7edfc000       Deferred        ntoskrnl<elf>                                                                          
  \-PE  7edd0000-7edfc000       \               ntoskrnl                                                                               
ELF     7edfc000-7ee52000       Export          advapi32<elf>                                                                          
  \-PE  7ee10000-7ee52000       \               advapi32                                                                               
ELF     7ee52000-7ee5e000       Deferred        libnss_files.so.2                                                                      
ELF     7ee5e000-7ee69000       Deferred        libnss_nis.so.2                                                                        
ELF     7ee69000-7ee72000       Deferred        libnss_compat.so.2                                                                     
ELF     7ee7c000-7ee91000       Export          winedevice<elf>                                                                        
  \-PE  7ee80000-7ee91000       \               winedevice                                                                             
ELF     7efbb000-7efe1000       Deferred        libm.so.6                                                                              
ELF     7efe7000-7f000000       Deferred        libnsl.so.1                                                                            
ELF     f7c3a000-f7c3e000       Deferred        libdl.so.2                                                                             
ELF     f7c3e000-f7da1000       Export          libc.so.6                                                                              
ELF     f7da2000-f7dbb000       Export          libpthread.so.0                                                                        
ELF     f7dda000-f7f16000       Deferred        libwine.so.1                                                                           
ELF     f7f18000-f7f39000       Deferred        ld-linux.so.2                                                                          
Threads:                                                                                                                               
process  tid      prio (all id:s are in hex)                                                                                           
00000008                                                                                                                               
        00000009    0                                                                                                                  
0000000a                                                                                                                               
        0000000b    0                                                                                                                  
0000000c                                                                                                                               
        0000000d    0                                                                                                                  
0000000e                                                                                                                               
        00000026    0                                                                                                                  
        00000020    0                                                                                                                  
        0000001b    0                                                                                                                  
        00000016    0                                                                                                                  
        00000015    0                                                                                                                  
        00000014    0                                                                                                                  
        00000010    0                                                                                                                  
        0000000f    0                                                                                                                  
00000011
        00000017    0
        00000013    0
        00000012    0
00000018
        0000001c    0
        0000001a    0
        00000019    0
0000001d
        00000022    0
        00000021    0
        0000001f    0
        0000001e    0
00000023 (D) C:\windows\system32\winedevice.exe
        00000027    0 <==
        00000025    0
        00000024    0
Backtrace:
=>0 0x7bc46aa1 LdrProcessRelocationBlock+0xc1() in ntdll (0x0064e6d8)
  1 0x7ee8d9b1 in winedevice (+0xd9b1) (0x0064e778)
  2 0x7ee8dd07 in winedevice (+0xdd07) (0x0064e9f8)
  3 0x7ee8e326 in winedevice (+0xe326) (0x0064ea48)
  4 0x7ee38e0c in advapi32 (+0x28e0c) (0x0064ea98)
  5 0x7bc6c338 call_thread_func+0xc() in ntdll (0x0064eaa8)
  6 0x7bc6c540 call_thread_entry_point+0x70() in ntdll (0x0064eb78)
  7 0x7bc7481b in ntdll (+0x6481b) (0x0064f3b8)
  8 0xf7da84ff start_thread+0xbf() in libpthread.so.0 (0x0064f4b8)
  9 0xf7d24b9e __clone+0x5e() in libc.so.6 (0x00000000)
fixme:mixer:ALSA_MixerInit No master control found on Camera, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:ntoskrnl:IoAllocateMdl stub: 0x1141f0, 5, 0, 0, (nil)
fixme:reg:GetNativeSystemInfo (0x33f750) using GetSystemInfo()
fixme:ntoskrnl:IoAllocateMdl stub: 0x1141f0, 5, 0, 0, (nil)
fixme:ntoskrnl:IoAllocateMdl stub: 0x1141f0, 5, 0, 0, (nil)
fixme:ntoskrnl:IoAllocateMdl stub: 0x114618, 5, 0, 0, (nil)
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x113ff8 0
fixme:ntoskrnl:IoAllocateMdl stub: 0x1141e8, 5, 0, 0, (nil)

```

And then a pop up with "insufficient privileges ! you must run this program asa an administrator dor the first time"

Ok, Now I try to run this game with "sudo" :

```
maximb@MaximB-HQ:~/Games/the witcher/The Witcher Enhanced Edition/System$ sudo wine witcher.exe
[sudo] password for maximb:
wine: /home/maximb/.wine is not owned by you

```
I've checked and wine is owned by my user (maximb) and it's on the home folder...

Ok, next step is to try to run this program with "root" :

```
root@MaximB-HQ:/home/maximb/Games/the witcher/The Witcher Enhanced Edition/System# wine witcher.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\maximb\\Games\\the witcher\\The Witcher Enhanced Edition\\System\\witcher.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\maximb\\Games\\the witcher\\The Witcher Enhanced Edition\\System\\witcher.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\maximb\\Games\\the witcher\\The Witcher Enhanced Edition\\System\\CommonLibs.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\maximb\\Games\\the witcher\\The Witcher Enhanced Edition\\System\\CommonLibs.dll") not found
err:module:import_dll Library CommonLibs.dll (which is needed by L"Z:\\home\\maximb\\Games\\the witcher\\The Witcher Enhanced Edition\\System\\witcher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\maximb\\Games\\the witcher\\The Witcher Enhanced Edition\\System\\witcher.exe" failed, status c0000135

```

No luck with that.

How do I play "The Witcher EE" ?

---

### Post by MaximB on 2009-07-14
Any good suggestions ?

---

### Post by doctordruidphd on 2009-07-23
Trying to get the Witcher to run on wine is a nightmare -- I almost think the King of the Wild Hunt himself designed it! But it can be done, though I have not succeeded it getting it perfect. And I'm not sure I can remember all of the hoops I had to jump through to get it to run.

Also, I will tell you up front that I cannot get it to run on any version of wine higher than 1.1.24; I get the same errors you are getting, and no help from the wine forum on it. If you are not using wine for anything else, then remove it from you system, delete your ~/.wine directory, and start over. I found that I cannot revert back -- once 1.1.25 or .26 have been installed, it wrecks the .wine directory, and reinstalling 1.1.24 won't fix it. I had backups of my .wine directory from before I "upgraded", so when I went back to 1.1.24, I just copied them back and they worked.

That all being said, the information on the wine appdb is helpful, but not perfect:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13866](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13866)

One thing, I needed to change the rendering to "gdi" and not "opengl", otherwise I get black screens when many of the special effects kick in (potions, drunk, etc).

The launcher doesn't work, but you probably already discovered that. You will either need a cracked version of the witcher.exe file, because the copy protection does not work with wine, or you will need to upgrade to the 1.5 patch, which has no copy protection. I could not get the patch to work with wine; I had to install on a windows computer, apply the patch, then copy everything over. 

That's all I can remember off the top of my head; witcher and oblivion were the worst installation nightmares I have ever had. If they gave experience points for getting these to work, I could kill a dragon with a mere glance...

Good luck with it. Yeah, it's worth it, the game is really cool.

PS Another thing I should mention - when the game starts, I often get video anomalies, such as characters with only faces and weapons showing. Usually I can fix that, by going into the "option" menu and changing the video resolution settings back and forth. Like I said, not perfect, but it works.

---

### Post by thezood on 2009-07-24
I just want to add that you really' don't want to run any Wine programs as root, since all configuration files or any files created by the game will be owned by root and it can be a nightmare to sort out. Also, it's a huge security risk.

---

### Post by lestatto on 2009-07-25
Well, can't say for sure, but Witcher need really good no-dvd crack, as it's protected. Try with a few of them, at least one should fit :)
Cheers

---

