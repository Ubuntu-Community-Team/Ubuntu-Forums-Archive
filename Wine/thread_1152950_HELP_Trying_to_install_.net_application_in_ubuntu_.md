---
title: "HELP Trying to install .net application in ubuntu under wine"
date: 2009-05-08
forum: Wine
---

### Post by gts1983 on 2009-05-08
i have followed some different post on how to install mono in place of .net but the closest i can get it this happens.

gts1983@Gmobile:~/Desktop$ wine myprogram.exe                                                                                               
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported                                                                       
fixme:advapi:CheckTokenMembership (0x13c 0x149df0 0x32dfa8) stub!                                                                              

Unhandled Exception: System.TypeInitializationException: The type initializer for 'System.Globalization.TextInfo' threw an exception.
   at System.Globalization.TextInfo.GetNativeTextInfo(Int32 cultureID)                                                               
   at System.Globalization.TextInfo.get_InvariantNativeTextInfo()                                                                    
   at System.String.Compare(String strA, Int32 indexA, String strB, Int32 indexB, Int32 length, StringComparison comparisonType)     
   at System.Security.Util.URLString.PreProcessForExtendedPathRemoval(String url, Boolean isFileUrl)                                 
   at System.AppDomainSetup.NormalizePath(String path, Boolean useAppBase)                                                           
   at System.AppDomainSetup.SetupDefaultApplicationBase(String imageLocation)                                                        
   at System.AppDomain.SetupFusionStore(AppDomainSetup info)                                                                         
   at System.AppDomain.SetupDomain(Boolean allowRedirects, String path, String configFile)                                           
wine: Unhandled exception 0xe0434f4d at address 0x7b845450 (thread 0009), starting debugger...                                       
Unhandled exception: 0xe0434f4d in 32-bit code (0x7b8454c3).                                                                         
Register dump:                                                                                                                       
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b                                                                                     
 EIP:7b8454c3 ESP:0032ef54 EBP:0032efb8 EFLAGS:00200246(   - 00      - IZP1)                                                         
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:0032eff0                                                                                 
 ESI:0032eff0 EDI:e0434f4d                                                                                                           
Stack dump:                                                                                                                          
0x0032ef54:  0032eff0 00000004 0000003c e0434f4d                                                                                     
0x0032ef64:  00000001 00000000 7b845450 00000001                                                                                     
0x0032ef74:  80131534 e0434f4d 0032eff0 00392010                                                                                     
0x0032ef84:  02000036 0032ef9c 79e814da 0032efa8                                                                                     
0x0032ef94:  02000036 00000001 0032f018 79e87ff4                                                                                     
0x0032efa4:  0000012c 003f161c 7b84545a 00130140                                                                                     
Backtrace:                                                                                                                           
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0032efb8)                                                                                   
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f018)                                                                                  
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f0dc)                                                                                  
  4 0x0331365b (0x0032f10c)                                                                                                          
  5 0x03313521 (0x0032f138)                                                                                                          
  6 0x0331194d (0x00000000)                                                                                                          
0x7b8454c3: subl        $4,%esp                                                                                                      
Modules:                                                                                                                             
Module  Address                 Debug info      Name (66 modules)                                                                    
PE        400000-  9f0000       Deferred        trinitytools                                                                         
PE      5e380000-5e409000       Deferred        diasymreader                                                                         
PE      78130000-781cb000       Deferred        msvcr80                                                                              
PE      79000000-79045000       Deferred        mscoree                                                                              
PE      79060000-790b3000       Deferred        mscorjit                                                                             
PE      790c0000-794de000       Deferred        mscorlib                                                                             
PE      79e70000-7a3d1000       Export          mscorwks                                                                             
ELF     7b800000-7b93d000       Export          kernel32<elf>                                                                        
  \-PE  7b820000-7b93d000       \               kernel32                                                                             
ELF     7bc00000-7bca7000       Deferred        ntdll<elf>                                                                           
  \-PE  7bc10000-7bca7000       \               ntdll                                                                                
ELF     7bf00000-7bf04000       Deferred        <wine-loader>                                                                        
ELF     7e475000-7e48a000       Deferred        lz32<elf>                                                                            
  \-PE  7e480000-7e48a000       \               lz32                                                                                 
ELF     7e48a000-7e4a5000       Deferred        version<elf>                                                                         
  \-PE  7e490000-7e4a5000       \               version                                                                              
ELF     7e4cd000-7e4e1000       Deferred        libresolv.so.2                                                                       
ELF     7e4e1000-7e500000       Deferred        iphlpapi<elf>                                                                        
  \-PE  7e4f0000-7e500000       \               iphlpapi                                                                             
ELF     7e500000-7e563000       Deferred        rpcrt4<elf>                                                                          
  \-PE  7e510000-7e563000       \               rpcrt4                                                                               
ELF     7e563000-7e609000       Deferred        ole32<elf>                                                                           
  \-PE  7e570000-7e609000       \               ole32                                                                                
ELF     7e82b000-7e897000       Deferred        msvcrt<elf>                                                                          
  \-PE  7e840000-7e897000       \               msvcrt                                                                               
ELF     7e897000-7e8a0000       Deferred        libxcursor.so.1                                                                      
ELF     7e8a0000-7e8a5000       Deferred        libxfixes.so.3                                                                       
ELF     7e8a5000-7e8a9000       Deferred        libxcomposite.so.1                                                                   
ELF     7e8a9000-7e8b0000       Deferred        libxrandr.so.2                                                                       
ELF     7e8b0000-7e8ba000       Deferred        libxrender.so.1                                                                      
ELF     7e8ba000-7e8bd000       Deferred        libxinerama.so.1                                                                     
ELF     7e8bd000-7e8de000       Deferred        imm32<elf>                                                                           
  \-PE  7e8c0000-7e8de000       \               imm32                                                                                
ELF     7e8de000-7e8e3000       Deferred        libxdmcp.so.6                                                                        
ELF     7e8e3000-7e8fc000       Deferred        libxcb.so.1                                                                          
ELF     7e8fc000-7e8ff000       Deferred        libxcb-xlib.so.0                                                                     
ELF     7e8ff000-7e902000       Deferred        libxau.so.6                                                                          
ELF     7e902000-7e9f1000       Deferred        libx11.so.6                                                                          
ELF     7e9f1000-7ea00000       Deferred        libxext.so.6                                                                         
ELF     7ea00000-7ea06000       Deferred        libxxf86vm.so.1                                                                      
ELF     7ea06000-7ea1e000       Deferred        libice.so.6                                                                          
ELF     7ea1e000-7ea27000       Deferred        libsm.so.6                                                                           
ELF     7ea37000-7ead2000       Deferred        winex11<elf>                                                                         
  \-PE  7ea50000-7ead2000       \               winex11                                                                              
ELF     7eaec000-7eb13000       Deferred        libexpat.so.1                                                                        
ELF     7eb13000-7eb40000       Deferred        libfontconfig.so.1                                                                   
ELF     7eb50000-7eb66000       Deferred        libz.so.1                                                                            
ELF     7eb66000-7ebdc000       Deferred        libfreetype.so.6                                                                     
ELF     7ebec000-7ec8b000       Deferred        gdi32<elf>                                                                           
  \-PE  7ec00000-7ec8b000       \               gdi32                                                                                
ELF     7ec8b000-7edd7000       Deferred        user32<elf>                                                                          
  \-PE  7ecb0000-7edd7000       \               user32                                                                               
ELF     7edd7000-7ee32000       Deferred        shlwapi<elf>                                                                         
  \-PE  7ede0000-7ee32000       \               shlwapi                                                                              
ELF     7ee32000-7ee85000       Deferred        advapi32<elf>                                                                        
  \-PE  7ee40000-7ee85000       \               advapi32                                                                             
ELF     7efa5000-7efb1000       Deferred        libnss_files.so.2                                                                    
ELF     7efb1000-7efca000       Deferred        libnsl.so.1                                                                          
ELF     7efca000-7eff0000       Deferred        libm.so.6                                                                            
ELF     7eff5000-7f000000       Deferred        libnss_nis.so.2                                                                      
ELF     b7db2000-b7dbb000       Deferred        libnss_compat.so.2                                                                   
ELF     b7dbc000-b7dc0000       Deferred        libdl.so.2                                                                           
ELF     b7dc0000-b7f1e000       Deferred        libc.so.6                                                                            
ELF     b7f1f000-b7f38000       Deferred        libpthread.so.0                                                                      
ELF     b7f48000-b807f000       Deferred        libwine.so.1                                                                         
ELF     b8081000-b809e000       Deferred        ld-linux.so.2                                                                        
Threads:                                                                                                                             
process  tid      prio (all id:s are in hex)                                                                                         
00000008 (D) Z:\home\gts1983\Desktop\myprogram.exe                                                                                
        00000018    2                                                                                                                
        00000017    0                                                                                                                
        00000009    0 <==                                                                                                            
0000000c                                                                                                                             
        00000014    0                                                                                                                
        00000013    0                                                                                                                
        00000012    0                                                                                                                
        0000000e    0                                                                                                                
        0000000d    0                                                                                                                
0000000f
        00000016    0
        00000015    0
        00000011    0
        00000010    0
00000019
        0000001a    0
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0032efb8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f018)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f0dc)
  4 0x0331365b (0x0032f10c)
  5 0x03313521 (0x0032f138)
  6 0x0331194d (0x00000000)
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x32ea9c,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.42 - Fatal Execution Engine Error (79F97075) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

---

### Post by asdfoo on 2009-05-08
which Wine version? how did you install .net?

---

