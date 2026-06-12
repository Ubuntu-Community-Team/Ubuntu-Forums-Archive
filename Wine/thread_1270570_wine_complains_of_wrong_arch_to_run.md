---
title: "wine complains of wrong arch to run"
date: 2009-09-19
forum: Wine
---

### Post by Belgoroth on 2009-09-19
Hello there!

Today I installed wine, but every time I attempt to run anything it spews out this

belgoroth@belgoroth-desktop:/media/casper/Games/Alice$ wine alice.exe 
err:menubuilder:WinMain unknown option -a                             
err:menubuilder:WinMain unknown option -r                             
wine: Unhandled page fault on execute access to 0x004e9af3 at address 0x4e9af3 (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x004e9af3 in 32-bit code (0x004e9af3).                      
Register dump:                                                                                                    
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b                                                                  
 EIP:004e9af3 ESP:0173ff0c EBP:0173ffe8 EFLAGS:00010246(   - 00      -RIZP1)                                      
 EAX:00000000 EBX:7b8b6ff4 ECX:42dd02a4 EDX:00000000                                                              
 ESI:004e9af3 EDI:7ffdf000                                                                                        
Stack dump:                                                                                                       
0x0173ff0c:  7b879028 7ffdf000 00000000 00000000                                                                  
0x0173ff1c:  00000000 00000000 00000000 00000000                                                                  
0x0173ff2c:  ffffffff 7b8790b0 7b845ef0 7b8b6ff4                                                                  
0x0173ff3c:  ffbefbe2 00000018 0173ffe8 2deeac51                                                                  
0x0173ff4c:  c50f26a4 00000000 00000000 00000000                                                                  
0x0173ff5c:  00000000 00000000 00000000 00000000                                                                  
Backtrace:                                                                                                        
=>1 0x004e9af3 EntryPoint() in alice (0x0173ffe8)                                                                 
  2 0xf7e9ed77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)                                           
0x004e9af3 EntryPoint in alice: pushl   %ebp                                                                      
Modules:                                                                                                          
Module  Address                 Debug info      Name (69 modules)                                                 
PE        400000-  f3e000       Export          alice                                                             
ELF     7b800000-7b93c000       Deferred        kernel32<elf>                                                     
  \-PE  7b820000-7b93c000       \               kernel32                                                          
ELF     7bc00000-7bca7000       Deferred        ntdll<elf>                                                        
  \-PE  7bc10000-7bca7000       \               ntdll                                                             
ELF     7bf00000-7bf04000       Deferred        <wine-loader>                                                     
ELF     7ddc8000-7dddd000       Deferred        midimap<elf>                                                      
  \-PE  7ddd0000-7dddd000       \               midimap                                                           
ELF     7dddd000-7de05000       Deferred        msacm32<elf>                                                      
  \-PE  7dde0000-7de05000       \               msacm32                                                           
ELF     7e606000-7e60c000       Deferred        libattr.so.1                                                      
ELF     7e60c000-7e66b000       Deferred        libpulse.so.0                                                     
ELF     7e66b000-7e733000       Deferred        libasound.so.2                                                    
ELF     7e73c000-7e755000       Deferred        msacm32<elf>                                                      
  \-PE  7e740000-7e755000       \               msacm32                                                           
ELF     7e755000-7e78c000       Deferred        winealsa<elf>                                                     
  \-PE  7e760000-7e78c000       \               winealsa                                                          
ELF     7e78c000-7e795000       Deferred        libxcursor.so.1                                                   
ELF     7e795000-7e79a000       Deferred        libxfixes.so.3                                                    
ELF     7e79a000-7e79e000       Deferred        libxcomposite.so.1                                                
ELF     7e79e000-7e7a6000       Deferred        libxrandr.so.2                                                    
ELF     7e7a6000-7e7b0000       Deferred        libxrender.so.1                                                   
ELF     7e7b0000-7e7b3000       Deferred        libxinerama.so.1                                                  
ELF     7e7b7000-7e7be000       Deferred        libgdbm.so.3                                                      
ELF     7e7be000-7e7c3000       Deferred        libcap.so.2                                                       
ELF     7e7c3000-7e7ca000       Deferred        libasound_module_pcm_pulse.so                                     
ELF     7e7ca000-7e7d3000       Deferred        librt.so.1                                                        
ELF     7e7d5000-7e7da000       Deferred        libxdmcp.so.6                                                     
ELF     7e7da000-7e7f4000       Deferred        libxcb.so.1                                                       
ELF     7e7f4000-7e7f8000       Deferred        libxau.so.6                                                       
ELF     7e7f8000-7e7fd000       Deferred        libuuid.so.1                                                      
ELF     7e7fd000-7e8ec000       Deferred        libx11.so.6                                                       
ELF     7e8ec000-7e8fc000       Deferred        libxext.so.6                                                      
ELF     7e8fc000-7e914000       Deferred        libice.so.6                                                       
ELF     7e914000-7e91d000       Deferred        libsm.so.6                                                        
ELF     7e91e000-7e93f000       Deferred        imm32<elf>                                                        
  \-PE  7e920000-7e93f000       \               imm32                                                             
ELF     7e93f000-7e9da000       Deferred        winex11<elf>                                                      
  \-PE  7e950000-7e9da000       \               winex11                                                           
ELF     7ea26000-7ea4d000       Deferred        libexpat.so.1                                                     
ELF     7ea4d000-7ea7a000       Deferred        libfontconfig.so.1                                                
ELF     7ea7a000-7ea90000       Deferred        libz.so.1                                                         
ELF     7ea90000-7eb07000       Deferred        libfreetype.so.6                                                  
ELF     7eb07000-7eb1d000       Deferred        libresolv.so.2                                                    
ELF     7eb1e000-7eb24000       Deferred        libxxf86vm.so.1                                                   
ELF     7eb3f000-7eb5e000       Deferred        iphlpapi<elf>                                                     
  \-PE  7eb50000-7eb5e000       \               iphlpapi                                                          
ELF     7eb5e000-7eb8b000       Deferred        ws2_32<elf>                                                       
  \-PE  7eb70000-7eb8b000       \               ws2_32                                                            
ELF     7eb8b000-7ec2b000       Deferred        gdi32<elf>                                                        
  \-PE  7eba0000-7ec2b000       \               gdi32                                                             
ELF     7ec2b000-7ed77000       Deferred        user32<elf>                                                       
  \-PE  7ec50000-7ed77000       \               user32                                                            
ELF     7ed77000-7ee0b000       Deferred        winmm<elf>                                                        
  \-PE  7ed80000-7ee0b000       \               winmm                                                             
ELF     7ee0b000-7ee5e000       Deferred        advapi32<elf>                                                     
  \-PE  7ee20000-7ee5e000       \               advapi32                                                          
ELF     7ef88000-7ef94000       Deferred        libnss_files.so.2                                                 
ELF     7ef94000-7ef9f000       Deferred        libnss_nis.so.2                                                   
ELF     7ef9f000-7efb8000       Deferred        libnsl.so.1                                                       
ELF     7efb8000-7efde000       Deferred        libm.so.6                                                         
ELF     7efe5000-7f000000       Deferred        wsock32<elf>                                                      
  \-PE  7eff0000-7f000000       \               wsock32                                                           
ELF     f7cf4000-f7cf8000       Deferred        libdl.so.2                                                        
ELF     f7cf8000-f7e5b000       Deferred        libc.so.6                                                         
ELF     f7e5c000-f7e75000       Deferred        libpthread.so.0                                                   
ELF     f7e77000-f7e80000       Deferred        libnss_compat.so.2                                                
ELF     f7e97000-f7fce000       Export          libwine.so.1                                                      
ELF     f7fd0000-f7ff1000       Deferred        ld-linux.so.2                                                     
Threads:                                                                                                          
process  tid      prio (all id:s are in hex)                                                                      
00000008 (D) Z:\media\casper\Games\Alice\alice.exe                                                                
        00000009    0 <==                                                                                         
0000000e                                                                                                          
        00000018    0                                                                                             
        00000015    0
        00000014    0
        00000010    0
        0000000f    0
00000011
        00000017    0
        00000016    0
        00000013    0
        00000012    0
Backtrace:
=>1 0x004e9af3 EntryPoint() in alice (0x0173ffe8)
  2 0xf7e9ed77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

I'm guessing I'm missing some more libraries but after installing all i can find synaptic i still seem to have a problem is it because wine does not do 64bit?

---

### Post by beastrace91 on 2009-09-20
Wine works perfectly fine on 64bit if you have the compatibility libraries installed. ```
sudo apt-get install ia32-libs
```

Also does every program you try to load via Wine dump with this exact same error message?

~Jeff

---

### Post by Belgoroth on 2009-09-20
Hi

The libs don't seem to work, get the same error on warcraft 3, diablo 2 and quake 4 :(
even after a fresh install.
Busy trying to compile from source see if it makes a difference

---

### Post by beastrace91 on 2009-09-21
Did you install your Graphics drivers while the 32bit libs where installed? If not then try reinstalling them - they need these libs to install their own 32bit compatibility libraries I am decently sure.

~Jeff

---

### Post by YokoZar on 2009-09-21
How did you install Wine?  Just installing the package should pull in all the libraries it uses.

---

### Post by Belgoroth on 2009-09-21
I installed from the repo through synaptic but since almost every program i install needs new libraries i updated my kubuntu and only tried it then. It seems to do it with any exe except direct x ironically. I did  back up my apt folder and format just now and re did my setup and i get the same error tried the deb from wine hq too. Does anyone know of any conflicting software i might have installed?

---

### Post by beastrace91 on 2009-09-21
> **beastrace91 said:**
> Did you install your Graphics drivers while the 32bit libs where installed? If not then try reinstalling them - they need these libs to install their own 32bit compatibility libraries I am decently sure.

I still think this might be your issue. What gfx card do you have? What driver version - and how did you install said driver?

Also do any non-direct x 3D apps run on your system via Wine?

~Jeff

---

### Post by Belgoroth on 2009-09-21
I am running a 8800 gts nvidia and its the first thing i installed on my system its on the ubuntu dvd then i install kubuntu and libs updated then i only installed wine ill retry it again when i get back from work. edit think the only other opengl i tried maya and quake

---

### Post by beastrace91 on 2009-09-21
> **beastrace91 said:**
> What driver version - and how did you install said driver?

Also what Wine version? And did you run Quake and/or Maya through Wine or nativly?

~Jeff

---

### Post by Belgoroth on 2009-09-21
Hi 
nvidia driver 180 via the hardware driver restricted pop up on my first boot wine version 1.01 and the one from winehq is 1.1.29 i think. As for quake and maya its already installed on my other drive when i had windows i have the disks too they are native linux?

---

### Post by beastrace91 on 2009-09-21
Quake 3 has a native Nix installer I know - not sure about Maya or other versions of Quake.

~Jeff

---

### Post by Belgoroth on 2009-09-23
Hi sorry for delay ok i installed fresh kubuntu and then nvidia drivers then ia32 then wine 1.01 winrar installs and works but almost everything gives me the same error. I then upgraded to 1.129 to no avail

---

### Post by YokoZar on 2009-10-01
> **Belgoroth said:**
> I installed from the repo through synaptic but since almost every program i install needs new libraries i updated my kubuntu and only tried it then. It seems to do it with any exe except direct x ironically. I did  back up my apt folder and format just now and re did my setup and i get the same error tried the deb from wine hq too. Does anyone know of any conflicting software i might have installed?

are you sure you're using the right version of the repository?  If you upgraded the whole operating system but are using the Wine packages for the previous version you may run into problems.

---

