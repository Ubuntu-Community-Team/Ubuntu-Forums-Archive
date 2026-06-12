---
title: "Spotify crashes when pressing play"
date: 2009-03-29
forum: Wine
---

### Post by wezzy on 2009-03-29
I've been trying to get Spotify to work under Wine and it should be a very easy story. I did it on my netbook in about 5 min. Now I've tried for many hours...

Basically what happen is that Spotify starts up alright with no problems, I hear the start sound and I can look for music and change settings, but as soon as I click play, nothing happens and I'm stucked with a program that is all freezed up.

I'm running Wine 1.0.1 on a Kubuntu 8.10 64-bit. In win xp mode and tried with oss and alsa.

I'm not good enough to get anything about this, but when I press play this is what the terminal shows me:
> Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x004b1f7c).             
Register dump:                                                                                         
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b                                                       
 EIP:004b1f7c ESP:7c4d9398 EBP:00ece1e0 EFLAGS:00210206(   - 00      - RIP1)                           
 EAX:00000000 EBX:00000000 ECX:00ecc3fc EDX:007a00bd                                                   
 ESI:00000080 EDI:7d7a2dbd                                                                             
Stack dump:                                                                                            
0x7c4d9398:  00ecd2c0 00ecd2c0 0077683e 00ecc3fc                                                       
0x7c4d93a8:  004be247 00ecc3fc 00000010 00ec917c                                                       
0x7c4d93b8:  00ecf130 00ec9160 00eb2620 00000000                                                       
0x7c4d93c8:  00ec89e0 0047b1ce 00000009 004a92b8                                                       
0x7c4d93d8:  00ece1e0 00000000 0047b330 00ecf158                                                       
0x7c4d93e8:  00ec9190 00ecc3fc 00ec917c 00ec9160                                                       
Backtrace:                                                                                             
=>1 0x004b1f7c in spotify (+0xb1f7c) (0x00ece1e0)                                                      
  2 0x00000000 (0x00146318)                                                                            
  3 0x00ece1e0 (0x00000000)                                                                            
0x004b1f7c: movl        %edi,0x0(%eax)                                                                 
Modules:                                                                                               
Module  Address                 Debug info      Name (93 modules)                                      
PE        400000-  7ae000       Export          spotify                                                
ELF     7b800000-7b93c000       Deferred        kernel32<elf>                                          
  \-PE  7b820000-7b93c000       \               kernel32                                               
ELF     7bb56000-7bba2000       Deferred        dbghelp<elf>                                           
  \-PE  7bb60000-7bba2000       \               dbghelp                                                
ELF     7bc00000-7bca7000       Deferred        ntdll<elf>                                             
  \-PE  7bc10000-7bca7000       \               ntdll                                                  
ELF     7bcd0000-7bd1c000       Deferred        dsound<elf>                                            
  \-PE  7bce0000-7bd1c000       \               dsound                                                 
ELF     7bd1c000-7bd5b000       Deferred        urlmon<elf>                                            
  \-PE  7bd20000-7bd5b000       \               urlmon                                                 
ELF     7bd5b000-7bd97000       Deferred        shdocvw<elf>                                           
  \-PE  7bd60000-7bd97000       \               shdocvw                                                
ELF     7bf00000-7bf04000       Deferred        <wine-loader>                                          
ELF     7bf06000-7bf0c000       Deferred        libnss_dns.so.2                                        
ELF     7bf0c000-7bf22000       Deferred        psapi<elf>                                             
  \-PE  7bf10000-7bf22000       \               psapi                                                  
ELF     7bf22000-7bf25000       Deferred        libnss_mdns4_minimal.so.2                              
ELF     7c26b000-7c27f000       Deferred        msimg32<elf>                                           
  \-PE  7c270000-7c27f000       \               msimg32                                                
ELF     7c6fd000-7c766000       Deferred        crypt32<elf>                                           
  \-PE  7c710000-7c766000       \               crypt32                                                
ELF     7c766000-7c789000       Deferred        mpr<elf>                                               
  \-PE  7c770000-7c789000       \               mpr                                                    
ELF     7c789000-7c7d9000       Deferred        wininet<elf>                                           
  \-PE  7c790000-7c7d9000       \               wininet                                                
ELF     7c7d9000-7c806000       Deferred        ws2_32<elf>                                            
  \-PE  7c7e0000-7c806000       \               ws2_32                                                 
ELF     7c806000-7c8ac000       Deferred        oleaut32<elf>                                          
  \-PE  7c820000-7c8ac000       \               oleaut32                                               
ELF     7c8d0000-7c8e4000       Deferred        libresolv.so.2                                         
ELF     7c8eb000-7c8fa000       Deferred        libgcc_s.so.1                                          
ELF     7c8fa000-7c919000       Deferred        iphlpapi<elf>                                          
  \-PE  7c900000-7c919000       \               iphlpapi                                               
ELF     7c919000-7c97c000       Deferred        rpcrt4<elf>                                            
  \-PE  7c930000-7c97c000       \               rpcrt4                                                 
ELF     7c97c000-7ca22000       Deferred        ole32<elf>                                             
  \-PE  7c990000-7ca22000       \               ole32                                                  
ELF     7cb4a000-7cc0f000       Deferred        comctl32<elf>                                          
  \-PE  7cb50000-7cc0f000       \               comctl32                                               
ELF     7cc0f000-7cc6a000       Deferred        shlwapi<elf>                                           
  \-PE  7cc20000-7cc6a000       \               shlwapi                                                
ELF     7cc6a000-7cd7e000       Deferred        shell32<elf>                                           
  \-PE  7cc80000-7cd7e000       \               shell32                                                
ELF     7d797000-7d7ca000       Deferred        uxtheme<elf>                                           
  \-PE  7d7a0000-7d7ca000       \               uxtheme                                                
ELF     7e7c9000-7e7de000       Deferred        midimap<elf>                                           
  \-PE  7e7d0000-7e7de000       \               midimap                                                
ELF     7e7de000-7e806000       Deferred        msacm32<elf>                                           
  \-PE  7e7e0000-7e806000       \               msacm32                                                
ELF     7e806000-7e81f000       Deferred        msacm32<elf>                                           
  \-PE  7e810000-7e81f000       \               msacm32                                                
ELF     7e81f000-7e85c000       Deferred        wineoss<elf>                                           
  \-PE  7e830000-7e85c000       \               wineoss                                                
ELF     7e85c000-7e8f0000       Deferred        winmm<elf>                                             
  \-PE  7e870000-7e8f0000       \               winmm                                                  
ELF     7e8f0000-7e8f9000       Deferred        libxcursor.so.1                                        
ELF     7e8f9000-7e8fe000       Deferred        libxfixes.so.3                                         
ELF     7e8fe000-7e902000       Deferred        libxcomposite.so.1                                     
ELF     7e902000-7e909000       Deferred        libxrandr.so.2                                         
ELF     7e909000-7e913000       Deferred        libxrender.so.1                                        
ELF     7e913000-7e916000       Deferred        libxinerama.so.1                                       
ELF     7e916000-7e937000       Deferred        imm32<elf>                                             
  \-PE  7e920000-7e937000       \               imm32                                                  
ELF     7e937000-7e93c000       Deferred        libxdmcp.so.6                                          
ELF     7e93c000-7e955000       Deferred        libxcb.so.1                                            
ELF     7e955000-7e958000       Deferred        libxcb-xlib.so.0                                       
ELF     7e958000-7ea47000       Deferred        libx11.so.6                                            
ELF     7ea47000-7ea56000       Deferred        libxext.so.6                                           
ELF     7ea56000-7ea5c000       Deferred        libxxf86vm.so.1                                        
ELF     7ea72000-7eb0d000       Deferred        winex11<elf>                                           
  \-PE  7ea80000-7eb0d000       \               winex11                                                
ELF     7eb41000-7eb68000       Deferred        libexpat.so.1                                          
ELF     7eb68000-7eb95000       Deferred        libfontconfig.so.1                                     
ELF     7eb95000-7ebab000       Deferred        libz.so.1                                              
ELF     7ebab000-7ec21000       Deferred        libfreetype.so.6                                       
ELF     7ec21000-7ec74000       Deferred        advapi32<elf>                                          
  \-PE  7ec30000-7ec74000       \               advapi32                                               
ELF     7ec74000-7ed14000       Deferred        gdi32<elf>                                             
  \-PE  7ec80000-7ed14000       \               gdi32                                                  
ELF     7ed14000-7ee60000       Deferred        user32<elf>                                            
  \-PE  7ed30000-7ee60000       \               user32                                                 
ELF     7ee60000-7ee6c000       Deferred        libnss_files.so.2                                      
ELF     7ee6c000-7ee85000       Deferred        libnsl.so.1                                            
ELF     7ee85000-7ee8e000       Deferred        libnss_compat.so.2                                     
ELF     7ee8f000-7ee92000       Deferred        libxau.so.6                                            
ELF     7efc4000-7efea000       Deferred        libm.so.6                                              
ELF     7eff3000-7effe000       Deferred        libnss_nis.so.2                                        
ELF     f7ce3000-f7ce7000       Deferred        libdl.so.2                                             
ELF     f7ce7000-f7e45000       Deferred        libc.so.6                                              
ELF     f7e46000-f7e5f000       Deferred        libpthread.so.0                                        
ELF     f7e75000-f7fac000       Deferred        libwine.so.1                                           
ELF     f7fae000-f7fce000       Deferred        ld-linux.so.2                                          
Threads:                                                                                               
process  tid      prio (all id:s are in hex)                                                           
0000000c                                                                                               
        00000012    0                                                                                  
        0000000e    0                                                                                  
        0000000d    0                                                                                  
0000000f                                                                                               
        00000014    0                                                                                  
        00000011    0                                                                                  
        00000010    0                                                                                  
00000016                                                                                               
        00000017    0                                                                                  
0000001d (D) C:\Program Files\Spotify\spotify.exe                                                      
        0000003f   15                                                                                  
        00000039    0 <==                                                                              
        00000038    0                                                                                  
        00000037    0                                                                                  
        00000036    2                                                                                  
        00000035    2                                                                                  
        00000034    2                                                                                  
        00000033    2                                                                                  
        00000032    2                                                                                  
        00000031    2                                                                                  
        00000030    2                                                                                  
        0000002f    2                                                                                  
        0000002e    2                                                                                  
        0000002d    2                                                                                  
        0000002c    2                                                                                  
        0000002b    2                                                                                  
        0000002a    2                                                                                  
        00000029    2                                                                                  
        00000028    2                                                                                  
        00000027    2                                                                                  
        00000026    0                                                                                  
        00000025    0                                                                                  
        00000024    0                                                                                  
        00000023    0                                                                                  
        00000022    0                                                                                  
        00000021    0                                                                                  
        00000020    0                                                                                  
        0000001f    0                                                                                  
        0000001e    0                                                                                  
Backtrace:                                                                                             
=>1 0x004b1f7c in spotify (+0xb1f7c) (0x00ece1e0)                                                      
  2 0x00000000 (0x00146318)                                                                            
  3 0x00ece1e0 (0x00000000)                                                                            
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags                                                                                                 
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags                                                                                                 
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags                                                                                                 
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags                                                                                                 
err:ntdll:RtlpWaitForCriticalSection section 0x562a4c "?" wait timed out in thread 001e, blocked by 0039, retrying (60 sec)

If someone can help I'm very thankful, I don't wanna go back to Windows

---

### Post by wezzy on 2009-03-30
Well, it helped with a complete uninstallation of Wine and Spotify (removing the .wine folder too) and then install everything from scratch again.

That means that this have to be considered solved I guess...

---

