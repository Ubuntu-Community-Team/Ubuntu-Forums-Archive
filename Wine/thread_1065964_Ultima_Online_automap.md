---
title: "Ultima Online automap"
date: 2009-02-10
forum: Wine
---

### Post by tneva82 on 2009-02-10
Not a program I can't live without but would be nice to get it working. However it seems to crash soon after starting it up.

Is there much of a hope of getting it working? If not then fair enough, I know UO world well enough that I should be able to get where I want without it but sure would make life easier.

Here's output of Wine when I try to run it. I bolded the part where it went haywire. After that there's long register dumb. Not sure if it's any use so I don't spam forum with that one.

Is there any method that doesn't involve rewriting parts of Wine?-)

err: process:__wine_kernel_init boot event wait timed out                   
fixme: shdocvw: PersistStreamInit_InitNew (0x1414c0)                         
fixme: shdocvw: OleObject_Advise (0x1414c0)->(0x5b0258, 0x5b02a4)            
fixme: shdocvw: ViewObject_SetAdvise (0x1414c0)->(1 00000000 0x5b0258)       
fixme: shdocvw: ViewObject_Draw (0x1414c0)->(1 -1 (nil) (nil) (nil) 0x314 0x5b02bc 0x5b02bc (nil) 00000000)                                                       
fixme: shdocvw:navigate_url Unsupported args (Flags 0x1002b848 : 10; TargetFrameName 0x1002b848 : 10)                                                                
fixme: urlmon:URLMonikerImpl_BindToObject use running object table               
fixme: mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer                                                                             
fixme: system: SetProcessDPIAware stub!                                           
fixme: dwmapi: DwmIsCompositionEnabled 0x32ddc4                                   
0154208: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found                             
0154208: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\softokn3.dll") - Symbol NSGetModule not found                                    
0[154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nspr4.dll") - Symbol NSGetModule not found                                       
0[154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found                                     
fixme:iphlpapi:NotifyAddrChange (Handle 0x7ce12898, overlapped 0x7ce128a0): stub
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\js3250.dll") - Symbol NSGetModule not found                                      
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\xpcom.dll") - Symbol NSGetModule not found                                       
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found                                    
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\xul.dll") - Symbol NSGetModule not found                                         
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found                                     
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plds4.dll") - Symbol NSGetModule not found                                       
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\ssl3.dll") - Symbol NSGetModule not found                                        
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\plc4.dll") - Symbol NSGetModule not found                                        
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nss3.dll") - Symbol NSGetModule not found                                        
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\freebl3.dll") - Symbol NSGetModule not found                                     
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\smime3.dll") - Symbol NSGetModule not found                                      
0154208]: nsNativeModuleLoader:: LoadModule("C:\windows\gecko\0.9.0\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found                                     
fixme: shdocvw:ClOleCommandTarget_QueryStatus (0x141560)->((null) 1 0x32e35c (nil))                                                                              
fixme: shdocvw:ClOleCommandTarget_Exec (0x141560)->((null) 25 2 0x32e370 (nil))  
fixme: shdocvw:ClOleCommandTarget_Exec (0x141560)->((null) 26 2 0x32e370 (nil))  
fixme: shdocvw: ClientSite_GetContainer (0x141560)->(0x32e3ac)                    
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e480 (nil))                                                  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e510)                                                  
fixme: resource: GetGuiResources (0xffffffff,0): stub                             
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 29 2 0x32e564 (nil))  
fixme: shdocvw: DocHostUIHandler_GetDropTarget (0x141560)                         
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32e47c)                                                  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32e47c)                                                  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 26 2 0x32e544 (nil))  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 29 2 0x32e554 (nil))  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))                                                    
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))                                                   
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 35 0 (nil) (nil))     
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 28 2 0x32e47c (nil))  
fixme: shdocvw: ClientSite_GetContainer (0x141560)->(0x32e540)                    
fixme: shdocvw: InPlaceFrame_SetStatusText (0x141560)->(0xb7e3bff1)               
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 25 2 0x32e474 (nil))  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 26 2 0x32e474 (nil))  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 21 2 (nil) (nil))     
fixme: mshtml: HTMLDocument3_get_parentDocument (0x143438)->(0x22b4360)           
fixme: shdocvw: navigate_url Unsupported args (Flags 0x1002b848:10; TargetFrameName 0x1002b848:10)                                                                
fixme: mshtml: HlinkTarget_SetBrowseContext (0x1433f0)->((nil))                   
fixme: urlmon: URLMonikerImpl_BindToObject use running object table               
fixme: shdocvw: BindStatusCallback_OnProgress status code 11                      
fixme: shdocvw: BindStatusCallback_OnProgress status code 14                      
fixme: shdocvw: ClOleCommandTarget_QueryStatus (0x141560)->((null) 1 0x32e2b4 (nil))                                                                              
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 25 2 0x32e2c8 (nil))  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->((null) 26 2 0x32e2c8 (nil))  
fixme: shdocvw: ClientSite_GetContainer (0x141560)->(0x32e304)                    
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e3d8 (nil))                                                  
fixme: shdocvw: ClOleCommandTarget_Exec (0x141560)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e468)                                                  
[B]wine: Unhandled privileged instruction at address 0x1c1e16 (thread 0046), starting debugger...                                                                  
Unhandled exception: privileged instruction in 32-bit code (0x001c1e16).     [/B]

---

