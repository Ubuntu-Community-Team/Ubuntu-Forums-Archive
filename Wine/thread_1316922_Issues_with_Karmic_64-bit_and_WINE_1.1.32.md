---
title: "Issues with Karmic 64-bit and WINE 1.1.32"
date: 2009-11-06
forum: Wine
---

### Post by Jguy on 2009-11-06
So I got my desktop up and working. It runs Karmic excellently. No issues with video, sound, wireless or any other drivers.

What I am having issues with is getting anything running with WINE. I was able to install Steam last night (coming to find out that installing anything to another assigned drive in wine caused the program to crash both with installation and trying to run anything. (the drive is filesystem ext2) (There would be another problem, I have to figure out how to get wine to read it's .wine from another mount location, namely media/apps, instead of my home folder. If I install everything to my home directory, that mount point will quickly run out of space))

So, I was able to install Steam by installing it to the drive_c folder in my home/jguy/.wine directory, but when I went to start Half-Life as a test to make sure I installed everything correctly, I was met with the home screen for Half Life, with only the 'Options' and 'Quit' selections displayed. The game then instantly froze. I had to then Alt+F2 my way to a terminal in the background and 'xkill' the Half Life window. What's worse yet is the fact that upon Half Life freezing, I lost all sound capabilities, I ended up having to restart Ubuntu to get it to work. (I have the ALSA driver selected in winecfg)

I then tried Ragnarok Online. This game worked flawlessly on my laptop (albeit not having the full ability to update the client) running Ubuntu 9.04 32-bit and wine 1.1.32. Ragnarok installed, my pserver client installed, and I was able to get in game, but on my login screen (and screens thereafter), the fps was like, 2.0. The fps was fine upon first loading the game, but a few seconds after the client starting, the fps dropped to around 2.0fps. The propritary driver for my ATi Radeon HD 4890 were in use by Ubuntu and reportedly running fine. What's worse again is after closing Ragnarok the first time, my sound disappeared again!

So, my problems:

* Half Life crashes when trying to run it.
* Ragnarok has a VERY low fps. so does Counter Strike
* Sound Ubuntu wide crashes after exiting a game from wine.
* I need wine to read it's .wine directory in /media/apps, not /home/jguy.

thanks for any help you can provide.

---

### Post by beastrace91 on 2009-11-06
I also run my Wine from a different directory to do so is easy just run the following in terminal: ```
mv ~/.wine /media/apps/Wine
ln -s /media/apps/Wine ~/.wine
```

The above two commands move your .wine directory and then create a symbolic link between the new location and your home directory.

Regarding your stability issues these most likely linked to your choice in graphics card. ATI drivers for Linux are a joke at best. Someone in another thread put it best "You have a better chance of finding the holy grail than getting most 3D Wine games to work on an ATI card". This statement is not far from the truth. While they run many native applications at an alright speed they are just too poor to handle most Wined applications. The few that work at all tend to run poorly.

Regards,
~Jeff

---

### Post by Jguy on 2009-11-06
Hm, thanks for the input. That might explain why my laptop (using an nVidia 8200 M, I think) works flawlessly but the desktop does not. 

I have some extra cash laying around, but am liquid cooled. Getting the card out and a new card in means a rebuild ;_; (I might be able to switch to onboard graphics for the time being, as it is an SLI/Nvidia board)

thanks.

---

### Post by nikro on 2009-11-09
I have an Radeon HD 4770 and have exactly the same problem. If you find a solution, please post it here - I will if I find it.

Btw: I have Ubuntu 32-bit and tried all wine versions (1.01 and 1.2 of the repos and the newest release from winehq.org)

---

### Post by nikro on 2009-11-09
Here is a detailed log of starting Steam and Counter-Strike 1.6

I will cut the output in pieces.

**Starting Steam:**
```
sven@sven-desktop:~/.wine/drive_c/Programme/Steam$ wine Steam.exe 
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: Fetching server list from CSDS. . .
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
CellID: CSDS returned 179 servers.
CellID: Connecting to 203.77.185.187:27031. . .
CellID: Connect to 203.77.185.187:27031 took 333 MS
CellID: Nothing beat our old best time of 30 MS
fixme:wbemprox:wbem_locator_ConnectServer 0x2a24188, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x3b8d3f8)
fixme:wbemprox:DllCanUnloadNow 
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x2a271b0)->(1 00000002 0x159e6a8)
fixme:shdocvw:PersistStreamInit_InitNew (0x2a271b0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x2a271b0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x2a271b0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x2a282e0)->(1 00000002 0x159e748)
fixme:shdocvw:PersistStreamInit_InitNew (0x2a282e0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x2a282e0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x2a282e0)->(ffffffff)
fixme:win:RegisterDeviceNotificationA (hwnd=0x100a6, filter=0x32de10,flags=0x00000004),
	returns a fake device notification handle!
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:urlmon:InternetBindInfo_GetBindString not supported string type 12
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Sat, 08-Nov-2014 17:49:53 GMT; path=/")
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32c84c
fixme:iphlpapi:NotifyAddrChange (Handle 0x91ce8e8, overlapped 0x91ce8f0): stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
0[2a8b558]: IMM32: InitKeyboardLayout, aKeyboardLayout=04070407, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x2a27250)->((null) 1 0x32ce14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 25 2 0x32ce28 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 26 2 0x32ce28 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000170
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x2a27250)->(0x32ce64)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32cef0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32cf18)
fixme:wininet:InternetLockRequestFile STUB
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 29 2 0x32d8e8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x2a27250)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d7f8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2d20798)->(0x32d2f0 0x32d2dc 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d7f8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2d21670)->(0x32d2f0 0x32d2dc 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d7f8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2d22530)->(0x32d2f0 0x32d2dc 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d7f8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2d233d0)->(0x32d2f0 0x32d2dc 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d7f8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2d2be78)->(0x32d2f0 0x32d2dc 0)
fixme:shdocvw:ClientSite_GetContainer (0x2a27250)->(0x32d8ec)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x2a27250)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 25 2 0x32d820 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 26 2 0x32d820 (nil))
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 28 2 0x32d9c8 (nil))
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d7f8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2d21670)->(0x32d2f0 0x32d2dc 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
0[2a8b558]: file http://store.steampowered.com/, line 63: ReferenceError: Ajax is not defined
0[2a8b558]: file http://store.steampowered.com/, line 242: ReferenceError: swfobject is not defined
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b4c0c8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x961e8b0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x961ff90)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b4e7d0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9656c58)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9657ca0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9659750)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x965b590)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x965d2b8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x965ef90)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9660a60)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9662a78)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96644d8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9665f90)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9667da8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9669cd0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x966b3e8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x966d030)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96706c8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96728f8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9674528)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9676208)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9677cb0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9679b68)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x967bb00)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x967d388)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9680a78)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9682ac0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9684490)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96859c0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x968c590)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x968d138)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x968dd78)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x968e920)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x968f100)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x9690ea0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x969f880)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96a1468)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96a2ef8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96a4978)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96acf48)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96aeb40)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96b0728)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96b3bf8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96b5488)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96b70f8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x967eda8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96bab70)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96bd950)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96c81b8)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96c90c0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96cb7b0)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c9e0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x96cd788)->(0x32c4d8 0x32c4c4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32c9e8)
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32c9e8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 26 2 0x32cab0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 29 2 0x32cac0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x2a27250)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x2a27250)->(L"Done")
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x2a271b0)->(0x32c85c)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x2a271b0)->(0x32c85c)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x2a271b0)->(0x32b9d4)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x2a271b0)->(0x32b9d4)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x2a271b0)->(0x32b9d4)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x2a271b0)->(0x32ac40)
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:mshtml:DispatchEx_GetDispID Unsupported grfdex 8
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
```

**Starting Counter-Strike - Prompting "Prepare to launch Counter-Strike"**
```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32cee0,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0x2d27940)->(1 00000002 0x159dd38)
fixme:shdocvw:PersistStreamInit_InitNew (0x2d27940)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x2d27940)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x2d27940)->(ffffffff)

```

**Counter-Strike started - Showing Main Menu**
```
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x2d27940)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x2d27940)
fixme:shdocvw:OleObject_Close (0x2d27940)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2a8,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:mshtml:hidden_proc (0x100c4 49239 0 1)
fixme:shdocvw:ViewObject_SetAdvise (0x1c3b48)->(1 00000002 0x5281950)
fixme:shdocvw:PersistStreamInit_InitNew (0x1c3b48)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1c3b48)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1c3b48)->(ffffffff)
err:ntdll:RtlpWaitForCriticalSection section 0xc173f4 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9f764 "loader.c: loader_section" wait timed out in thread 005d, blocked by 0056, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9f764 "loader.c: loader_section" wait timed out in thread 005e, blocked by 0056, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xc173f4 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
```

The game freezes after ~1sec

**Debugging Output after Ctrl+C**
```
^Cwine: Unhandled page fault on write access to 0x00000000 at address 0x3b3743d (thread 005e), starting debugger...
sven@sven-desktop:~/.wine/drive_c/Programme/Steam$ Thread ID=0057 renamed using MS VC6 extension (name=="CThread")
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x03b3743d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:03b3743d ESP:0979e6ec EBP:03c9b1c8 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:0000001d ECX:00000000 EDX:0125c0d0
 ESI:00000000 EDI:0000001d
Stack dump:
0x0979e6ec:  03b07775 05279ca0 0979e708 00000200
0x0979e6fc:  03c9b1c8 0423cc68 0979e901 7e1beff4
0x0979e70c:  00000814 0979e7f0 7e1a37a8 0979e744
0x0979e71c:  00000000 0979e738 00000040 00000000
0x0979e72c:  00000000 00000000 00000001 0979eaa4
0x0979e73c:  7e1a3a20 000001f8 7e1beff4 00000814
Backtrace:
=>0 0x03b3743d (0x03c9b1c8)
  1 0x00000000 (0x00000000)
0x03b3743d: addb	%al,0x0(%eax)
Modules:
Module	Address			Debug info	Name (142 modules)
PE	 1240000- 1260000	Deferred        filesystem_steam
PE	 1400000- 3517000	Deferred        hl
PE	 3730000- 3745000	Deferred        steam_api
PE	 3750000- 3765000	Deferred        particleman
PE	 81e0000- 8339000	Deferred        client
PE	 8770000- 8854000	Deferred        gameui
PE	 8a70000- 8ab0000	Deferred        vgui2
PE	 97a0000- 97af000	Deferred        voice_miles
PE	 98c0000- 98de000	Deferred        demoplayer
PE	 99f0000- 9a38000	Deferred        core
PE	 a110000- a19d000	Deferred        serverbrowser
PE	 a550000- a5aa000	Deferred        vstdlib
PE	 a5b0000- a609000	Deferred        tier0
PE	10000000-1003c000	Deferred        gameoverlayrenderer
PE	21100000-2115e000	Deferred        mss32
PE	30000000-302c5000	Deferred        steam
PE	38000000-38379000	Deferred        steamclient
PE	3f000000-3f0a6000	Deferred        tier0_s
PE	3f600000-3f671000	Deferred        vstdlib_s
PE	60000000-60021000	Deferred        cserhelper
ELF	79fe1000-7b800000	Deferred        fglrx_dri.so
ELF	7b800000-7b972000	Deferred        kernel32<elf>
  \-PE	7b820000-7b972000	\               kernel32
ELF	7bc00000-7bcb3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d0df000-7d0f5000	Deferred        winejoystick<elf>
  \-PE	7d0e0000-7d0f5000	\               winejoystick
ELF	7d0f5000-7d10e000	Deferred        mcicda<elf>
  \-PE	7d100000-7d10e000	\               mcicda
ELF	7d10e000-7d15b000	Deferred        dsound<elf>
  \-PE	7d120000-7d15b000	\               dsound
ELF	7d15b000-7d19c000	Deferred        shdocvw<elf>
  \-PE	7d160000-7d19c000	\               shdocvw
ELF	7d210000-7d2ab000	Deferred        opengl32<elf>
  \-PE	7d230000-7d2ab000	\               opengl32
ELF	7d3a6000-7d3d2000	Deferred        libatiadlxx.so
ELF	7daf1000-7dafa000	Deferred        librt.so.1
ELF	7dafa000-7db18000	Deferred        libgcc_s.so.1
ELF	7db18000-7dba9000	Deferred        libgl.so.1
ELF	7dba9000-7dcd9000	Deferred        wined3d<elf>
  \-PE	7dbb0000-7dcd9000	\               wined3d
ELF	7dcd9000-7dce0000	Deferred        libnss_dns.so.2
ELF	7dce0000-7dce4000	Deferred        libnss_mdns4_minimal.so.2
ELF	7dce4000-7dce9000	Deferred        libgpg-error.so.0
ELF	7dce9000-7dd65000	Deferred        libgcrypt.so.11
ELF	7dd65000-7dd77000	Deferred        libtasn1.so.3
ELF	7dd77000-7de1f000	Deferred        libgnutls.so.26
ELF	7de2e000-7de55000	Deferred        netapi32<elf>
  \-PE	7de30000-7de55000	\               netapi32
ELF	7de55000-7de81000	Deferred        secur32<elf>
  \-PE	7de60000-7de81000	\               secur32
ELF	7de81000-7deb2000	Deferred        wintrust<elf>
  \-PE	7de90000-7deb2000	\               wintrust
ELF	7deb2000-7deca000	Deferred        imagehlp<elf>
  \-PE	7dec0000-7deca000	\               imagehlp
ELF	7deca000-7df55000	Deferred        crypt32<elf>
  \-PE	7ded0000-7df55000	\               crypt32
ELF	7df9c000-7dfb1000	Deferred        midimap<elf>
  \-PE	7dfa0000-7dfb1000	\               midimap
ELF	7dfb1000-7dfd7000	Deferred        msacm32<elf>
  \-PE	7dfc0000-7dfd7000	\               msacm32
ELF	7dfd7000-7dff0000	Deferred        msacm32<elf>
  \-PE	7dfe0000-7dff0000	\               msacm32
ELF	7dff0000-7e02e000	Deferred        wineoss<elf>
  \-PE	7e000000-7e02e000	\               wineoss
ELF	7e02e000-7e113000	Deferred        oleaut32<elf>
  \-PE	7e050000-7e113000	\               oleaut32
ELF	7e113000-7e136000	Deferred        mpr<elf>
  \-PE	7e120000-7e136000	\               mpr
ELF	7e136000-7e18d000	Deferred        wininet<elf>
  \-PE	7e140000-7e18d000	\               wininet
ELF	7e18d000-7e214000	Deferred        winmm<elf>
  \-PE	7e1a0000-7e214000	\               winmm
ELF	7e2a4000-7e2ba000	Deferred        psapi<elf>
  \-PE	7e2b0000-7e2ba000	\               psapi
ELF	7e2ba000-7e309000	Deferred        dbghelp<elf>
  \-PE	7e2c0000-7e309000	\               dbghelp
ELF	7e32d000-7e39b000	Deferred        rpcrt4<elf>
  \-PE	7e340000-7e39b000	\               rpcrt4
ELF	7e39b000-7e497000	Deferred        ole32<elf>
  \-PE	7e3b0000-7e497000	\               ole32
ELF	7e4c1000-7e4f4000	Deferred        uxtheme<elf>
  \-PE	7e4d0000-7e4f4000	\               uxtheme
ELF	7e4f4000-7e5be000	Deferred        comctl32<elf>
  \-PE	7e500000-7e5be000	\               comctl32
ELF	7e5be000-7e74e000	Deferred        shell32<elf>
  \-PE	7e5d0000-7e74e000	\               shell32
ELF	7e74e000-7e7ab000	Deferred        shlwapi<elf>
  \-PE	7e760000-7e7ab000	\               shlwapi
ELF	7e7ab000-7e7bf000	Deferred        lz32<elf>
  \-PE	7e7b0000-7e7bf000	\               lz32
ELF	7e7bf000-7e7d9000	Deferred        version<elf>
  \-PE	7e7c0000-7e7d9000	\               version
ELF	7e7d9000-7e7e4000	Deferred        libxcursor.so.1
ELF	7e7e4000-7e7ea000	Deferred        libxfixes.so.3
ELF	7e7ea000-7e7ee000	Deferred        libxcomposite.so.1
ELF	7e7ee000-7e7f7000	Deferred        libxrandr.so.2
ELF	7e7f7000-7e801000	Deferred        libxrender.so.1
ELF	7e801000-7e807000	Deferred        libxxf86vm.so.1
ELF	7e807000-7e80a000	Deferred        libxinerama.so.1
ELF	7e80a000-7e82b000	Deferred        imm32<elf>
  \-PE	7e810000-7e82b000	\               imm32
ELF	7e82b000-7e830000	Deferred        libxdmcp.so.6
ELF	7e830000-7e84e000	Deferred        libxcb.so.1
ELF	7e84e000-7e852000	Deferred        libxau.so.6
ELF	7e852000-7e857000	Deferred        libuuid.so.1
ELF	7e857000-7e986000	Deferred        libx11.so.6
ELF	7e986000-7e996000	Deferred        libxext.so.6
ELF	7e996000-7e9b1000	Deferred        libice.so.6
ELF	7e9b1000-7e9ba000	Deferred        libsm.so.6
ELF	7e9c9000-7ea68000	Deferred        winex11<elf>
  \-PE	7e9e0000-7ea68000	\               winex11
ELF	7ea9b000-7eac2000	Deferred        libexpat.so.1
ELF	7eac2000-7eaef000	Deferred        libfontconfig.so.1
ELF	7eafe000-7eb14000	Deferred        libz.so.1
ELF	7eb14000-7eb93000	Deferred        libfreetype.so.6
ELF	7eb93000-7eba8000	Deferred        system.drv16.so
PE	7eba0000-7eba8000	Deferred        system.drv16
ELF	7eba8000-7ec48000	Deferred        gdi32<elf>
  \-PE	7ebc0000-7ec48000	\               gdi32
ELF	7ec48000-7ed94000	Deferred        user32<elf>
  \-PE	7ec60000-7ed94000	\               user32
ELF	7ed94000-7edec000	Deferred        advapi32<elf>
  \-PE	7eda0000-7edec000	\               advapi32
ELF	7edec000-7ee00000	Deferred        libresolv.so.2
ELF	7ee00000-7ee20000	Deferred        iphlpapi<elf>
  \-PE	7ee10000-7ee20000	\               iphlpapi
ELF	7ee20000-7ee4a000	Deferred        ws2_32<elf>
  \-PE	7ee30000-7ee4a000	\               ws2_32
ELF	7ee4a000-7ee65000	Deferred        wsock32<elf>
  \-PE	7ee50000-7ee65000	\               wsock32
ELF	7ee65000-7ee71000	Deferred        libnss_files.so.2
ELF	7ee71000-7ee88000	Deferred        libnsl.so.1
ELF	7ee88000-7ee90000	Deferred        libnss_compat.so.2
ELF	7efcb000-7eff1000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b749d000-b74a1000	Deferred        libdl.so.2
ELF	b74a1000-b75e5000	Deferred        libc.so.6
ELF	b75e6000-b75ff000	Deferred        libpthread.so.0
ELF	b760e000-b774a000	Deferred        libwine.so.1
ELF	b774c000-b7769000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 
	00000019    0
00000055 (D) C:\Programme\Steam\steamapps\sven@cyres-clan.de\counter-strike\hl.exe
	0000005f    0
	0000005e    0 <==
	0000005c   15
	0000005b   15
	00000057    0
	00000056    0
Backtrace:
=>0 0x03b3743d (0x03c9b1c8)
  1 0x00000000 (0x00000000)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```


I googled the errors, but found nothing that could help me. Any Ideas?

---

### Post by terrax on 2009-11-09
This must be an ubuntu issue. I just moved from Archlinux to Ubuntu, because Archlinux upgraded the xserver to 1.7 -> No fglrx support.

Though I didn't have any issues running wine with fglrx. You are very very wrong thinking its because of a crappy fglrx. Actually its because wine is developed over nvidia hardware, and uses specific nvidia opengl functions. This will all be fixed when opengl 3.2 for fglrx is released. But again. No issues with fglrx on wine in a 64 bit environment.

---

### Post by ram32 on 2009-11-24
I have the same problem as nikro using wine 1.1.33 on Ubuntu 9.10 with ATI Radeon HD4570 (fglrx drivers).
I can run CS in D3D mode (ugly), but can't do it in OpenGL mode! The error message is the same as nikro said.

---

### Post by yester64 on 2009-11-25
you guys were able to install games?
I can't even install a game with that version and now i am reading that none actually work.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554&iTestingId=45103](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554&iTestingId=45103)

---

