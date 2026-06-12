---
title: "program wont run problem with nethasp protection"
date: 2008-12-18
forum: Wine
---

### Post by izar on 2008-12-18
i have installed a clean copy of ubuntu 8.10 64bit
i installed a program called the Bar Ilan Responsa Project which uses a license from a local network server, using wine.
this program works perfectly for my friend who has ubuntu 8.10 32bit.
alas, when i try running the program i always get the message: "no answer from NetHasp license manager (15)"
(this is the error you get in windows if you try running the program when you are not connected to the network)
(the first times i installed the program the installation didn't go well and a few dll files weren't installed. i found out that this happened because i was trying to install from a location on my old windows (ntfs) partition. this was fixed when i copied the original installation folder to my ext3 partition, and installed from there)

i thought the cause might be the 64bit OS, so i removed it and installed kubuntu 8.10 32bit instead.
when that didn't work, i installed gnome and tried installing and running the program from there. didn't help.

i tried doing this both in wine 1.0.1 and 1.1.9 (which both work for my friend)
i also installed various packages such as:
winbind, smbfs, ntlm, cabextract (for ies4linux), samba...
i also tried switching windows versions in winecfg.
we copied the entire .wine folder form my friends computer to mien, and tried running the program from there.

as you can assume, non of this helped.

we tried comparing the output we get in terminal when running the program.
this is my friends output (which works):
```

  :~/.wine/drive_c/Program Files/ResponsaCD14$ env LANG=he_IL.utf8 WINEPREFIX="/home/a/.wine" wine "C:\PROG~FBU\RESP~MT1\RESPONSA.EXE" 
  wine: Unhandled privileged instruction at address 0x451e1a (thread 0014), starting debugger... 
  Unhandled exception: privileged instruction in 32-bit code (0x00451e1a). 
  Register dump: 
    CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b 
    EIP:00451e1a ESP:7ec1c6d8 EBP:00451e1a EFLAGS:00010206(   - 00      - RIP1) 
    EAX:00000000 EBX:7eea3ff4 ECX:7ec1c964 EDX:00000000 
    ESI:004500c8 EDI:004f2420 
  Stack dump: 
  0x7ec1c6d8:  004de662 7ec1c6e8 00000246 004500c8 
  0x7ec1c6e8:  7ec1c988 7eea1f37 7eea4500 7ec1c964 
  0x7ec1c6f8:  00114080 00000000 00113f38 7ec1c974 
  0x7ec1c708:  00040002 00000000 00000000 7eea4500 
  0x7ec1c718:  00340014 7b8b7ff4 00010000 7ec1c96c 
  0x7ec1c728:  7ec1c964 7eea2a2a 7ec1c978 7ec1c974 
  Backtrace: 
  =>1 0x00451e1a in hardlock.sys (+0x1e1a) (0x00451e1a) 
  0x00451e1a: movl   %cr4,%esi 
  Modules: 
  Module   Address         Debug info   Name (29 modules) 
  PE     450000-  4f7400   Export          hardlock.sys 
  ELF   7b800000-7b940000   Deferred        kernel32<elf> 
    \-PE   7b820000-7b940000   \               kernel32 
  ELF   7bc00000-7bcac000   Deferred        ntdll<elf> 
    \-PE   7bc10000-7bcac000   \               ntdll 
  ELF   7bf00000-7bf04000   Deferred        <wine-loader> 
  ELF   7eaf7000-7eb0d000   Deferred        hal<elf> 
    \-PE   7eb00000-7eb0d000   \               hal 
  ELF   7ec1e000-7ec32000   Deferred        libresolv.so.2 
  ELF   7ec47000-7ec67000   Deferred        iphlpapi<elf> 
    \-PE   7ec50000-7ec67000   \               iphlpapi 
  ELF   7ec67000-7ecce000   Deferred        rpcrt4<elf> 
    \-PE   7ec70000-7ecce000   \               rpcrt4 
  ELF   7eddf000-7ee19000   Deferred        ntoskrnl<elf> 
    \-PE   7edf0000-7ee19000   \               ntoskrnl 
  ELF   7ee19000-7ee6e000   Deferred        advapi32<elf> 
    \-PE   7ee30000-7ee6e000   \               advapi32 
  ELF   7ee6e000-7ee87000   Deferred        libnsl.so.1 
  ELF   7ee87000-7ee90000   Deferred        libnss_compat.so.2 
  ELF   7ee90000-7eea5000   Deferred        winedevice<elf> 
    \-PE   7eea0000-7eea5000   \               winedevice 
  ELF   7efc5000-7efeb000   Deferred        libm.so.6 
  ELF   7eff4000-7f000000   Deferred        libnss_files.so.2 
  ELF   b7c12000-b7c1d000   Deferred        libnss_nis.so.2 
  ELF   b7c1e000-b7c22000   Deferred        libdl.so.2 
  ELF   b7c22000-b7d80000   Deferred        libc.so.6 
  ELF   b7d81000-b7d9a000   Deferred        libpthread.so.0 
  ELF   b7daf000-b7ee6000   Deferred        libwine.so.1 
  ELF   b7ee8000-b7f05000   Deferred        ld-linux.so.2 
  Threads: 
  process  tid      prio (all id:s are in hex) 
  00000008 
      00000009    0 
  0000000a 
      0000000b    0 
  0000000c 
      00000013    0 
      00000012    0 
      0000000e    0 
      0000000d    0 
  0000000f (D) c:\windows\system32\winedevice.exe 
      00000014    0 <== 
      00000011    0 
      00000010    0 
  Backtrace: 
  =>1 0x00451e1a in hardlock.sys (+0x1e1a) (0x00451e1a) 
  fixme:wtsapi:WTSQuerySessionInformationA Stub (nil) 0xffffffff 4 0x32fbd8 0x32fbcc 
  fixme:keyboard:X11DRV_LoadKeyboardLayout L"0000040d", 0101: stub! 
  fixme:keyboard:X11DRV_ActivateKeyboardLayout (nil), 0100: stub! 
  fixme:bidi:mirror stub: mirroring of characters not yet implemented 
  fixme:ntdll:NtLockFile I/O completion on lock not implemented yet 
  fixme:font:WineEngRemoveFontResourceEx :stub 
  fixme:font:WineEngRemoveFontResourceEx :stub 
  fixme:font:WineEngRemoveFontResourceEx :stub 
  fixme:font:WineEngRemoveFontResourceEx :stub 
  fixme:font:WineEngRemoveFontResourceEx :stub 
  fixme:font:WineEngRemoveFontResourceEx :stub 
  fixme:font:WineEngRemoveFontResourceEx :stub 
```


this is my output (which dosn't work):
  ```

  avi@avi-laptop:~$ env LANG="he_IL.UTF-8" WINEPREFIX="/home/avi/.wine" wine "C:\PROG~FBU\RESP~MT1\RESPONSA.EXE"                                                  
  Warning: could not find DOS drive for current working directory '/home/avi', starting in the Windows directory.                                                  
  wine: Unhandled privileged instruction at address 0x451e1a (thread 0014), starting debugger...                                                                  
  Unhandled exception: privileged instruction in 32-bit code (0x00451e1a).        
  Register dump:                                                                  
    CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b                                
    EIP:00451e1a ESP:7ec2d908 EBP:00451e1a EFLAGS:00010202(   - 00      - -RI1)    
    EAX:00000000 EBX:7ee74ff4 ECX:7ec2d9b4 EDX:00000000                            
    ESI:00450000 EDI:004f2420                                                      
  Stack dump:                                                                      
  0x7ec2d908:  004de662 7ec2d918 00000246 00450000                                
  0x7ec2d918:  7ec2d9d8 7ee72f79 7ee75480 7ec2d9b4                                
  0x7ec2d928:  001110c0 00000000 00111060 7ec2d9c4                                
  0x7ec2d938:  fc11c0a7 00110f28 00110014 00120000                                
  0x7ec2d948:  7bc42cfd 7bc8aff4 7ee75480 7ec2d9bc                                
  0x7ec2d958:  7ec2d9b4 7ec2d998 7ee7382a 7ec2d9c8                                
  Backtrace:                                                                      
  =>1 0x00451e1a in hardlock.sys (+0x1e1a) (0x00451e1a)                            
  0x00451e1a: movl        %cr4,%esi                                                
  Modules:                                                                        
  Module  Address                 Debug info      Name (31 modules)                
  PE        450000-  4f7400       Export          hardlock.sys                    
  ELF     7b800000-7b93d000       Deferred        kernel32<elf>                    
    \-PE  7b820000-7b93d000       \               kernel32                        
  ELF     7bc00000-7bca7000       Deferred        ntdll<elf>                      
    \-PE  7bc10000-7bca7000       \               ntdll                            
  ELF     7bf00000-7bf04000       Deferred        <wine-loader>                    
  ELF     7ea9c000-7eab2000       Deferred        hal<elf>                        
    \-PE  7eaa0000-7eab2000       \               hal                              
  ELF     7eab2000-7eb1e000       Deferred        msvcrt<elf>                      
    \-PE  7eac0000-7eb1e000       \               msvcrt                          
  ELF     7ec2f000-7ec43000       Deferred        libresolv.so.2                  
  ELF     7ec43000-7ec62000       Deferred        iphlpapi<elf>                    
    \-PE  7ec50000-7ec62000       \               iphlpapi                        
  ELF     7ec62000-7ecc5000       Deferred        rpcrt4<elf>                      
    \-PE  7ec70000-7ecc5000       \               rpcrt4                          
  ELF     7edd6000-7ee0e000       Deferred        ntoskrnl<elf>                    
    \-PE  7ede0000-7ee0e000       \               ntoskrnl                        
  ELF     7ee0e000-7ee61000       Deferred        advapi32<elf>                    
    \-PE  7ee20000-7ee61000       \               advapi32                        
  ELF     7ee61000-7ee76000       Deferred        winedevice<elf> 
    \-PE  7ee70000-7ee76000       \               winedevice 
  ELF     7ee76000-7ee8f000       Deferred        libnsl.so.1 
  ELF     7ee8f000-7ee98000       Deferred        libnss_compat.so.2 
  ELF     7efc9000-7efef000       Deferred        libm.so.6 
  ELF     7eff4000-7f000000       Deferred        libnss_files.so.2 
  ELF     b7ca1000-b7cac000       Deferred        libnss_nis.so.2 
  ELF     b7cad000-b7cb1000       Deferred        libdl.so.2 
  ELF     b7cb1000-b7e0f000       Deferred        libc.so.6 
  ELF     b7e10000-b7e29000       Deferred        libpthread.so.0 
  ELF     b7e3a000-b7f71000       Deferred        libwine.so.1 
  ELF     b7f73000-b7f90000       Deferred        ld-linux.so.2 
  Threads: 
  process  tid      prio (all id:s are in hex) 
  00000008 
	  00000009    0 
  0000000a 
	  0000000b    0 
  0000000c 
	  00000013    0 
	  00000012    0 
	  0000000e    0 
	  0000000d    0 
  0000000f (D) C:\windows\system32\winedevice.exe 
	  00000014    0 <== 
	  00000011    0 
	  00000010    0 
  Backtrace: 
  =>1 0x00451e1a in hardlock.sys (+0x1e1a) (0x00451e1a) 
  fixme:wtsapi:WTSQuerySessionInformationA Stub (nil) 0xffffffff 4 0x32fbd8 0x32fbcc 
  
```
(for some reason i get a simular messege when ever i run any program through wine, shuch as winecfg)

as you can see the to lines which have to do with "msvcrt". i tried replacing the msvcrt.dll file with one from windows xp and tried the same with one from vista. i also tried install playing with the override option in winecfg

finally me and my friend made a debug file with the command:
```
:~/.wine/drive_c/Program Files/ResponsaCD14$ WINEDEBUG=+relay,+seh,+tid env LANG=he_IL.utf8 WINEPREFIX="/home/avi/.wine" wine "C:\PROG~FBU\RESP~MT1\RESPONSA.EXE" &> ~/documents/debug.txt
```
(note that i am using wine 1.0.1 and my friend is currently using wine 1.1.9, so this might cause some difference. as noted oboe i tried also wine 1.1.9 and it still didn't work so this isn't the problem. if you wish i can create another debug file using wine 1.1.9 latter)
i named the files works (for my friend) and dosntwork (for mien) and attached them.
(we had to cut "works" because it was too big (32 mb) so we left about the number of lines in "dosntwork" and deleted the lines from there on) 

we can't find any reason why the progarm works for my friend and not for me. can you please help?

---

### Post by izar on 2008-12-20
hey it toke me more than an hour to write all of this information. you cant simply ignore me

---

### Post by hikaricore on 2008-12-20
> **izar said:**
> hey it toke me more than an hour to write all of this information. you cant simply ignore me


The Ubuntu Forums is a volunteer community of Ubuntu users just like you.  People will respond when and if they can assist you.
Telling people they're not allowed to ignore you is just silly because they can do whatever they please.

In the future please allow 24-48 hours before bumping posts.

Best of luck,

--Aaron

---

### Post by izar on 2008-12-25
> Telling people they're not allowed to ignore you is just silly because they can do whatever they please.
i was just being a bit cynical, i never thought i have any sort of power to command the readers to reply. though i _did_ wait nearly 48 hours before bumping.

this post has been up for almost a week, and yet i haven't gotten any sort of the slightest answer._***please***_ give me some help? ](*,)
[SIZE="1"](i am beginning to wonder if the fact that i posted all of the information at once was a mistake rather than help for you to understand the problem better)[/SIZE]

---

### Post by izar on 2009-01-05
ok i give up 
also i give up linux because i need responsa running on my computer and i cant do without it. 
:(

---

### Post by arubin on 2009-01-20
Izar,

I have tried installing Bar Ilan Responsa under wine on another distribution (Slackware) and it would not run. Some problem with loading dlls.

My solution (which should work in Ubuntu) was to use a virtual Windows installation running on Vmware.

I should note that this was the CD vesion of Bar Ilan

---

### Post by izar on 2009-01-22
thanks, i should try that at some point
though i was hoping to avoid using windows

---

### Post by izar on 2009-03-12
if anyone ever serches here for using responsa in linux then you should know that:
it works!
for more info look here:
[http://www.whatsup.org.il/index.php?name=PNphpBB2&file=viewtopic&t=31072&start=30&postdays=0&postorder=asc&highlight=]("http://www.whatsup.org.il/index.php?name=PNphpBB2&file=viewtopic&t=31072&start=30&postdays=0&postorder=asc&highlight=")
or PM me

---

