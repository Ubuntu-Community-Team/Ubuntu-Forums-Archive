---
title: "Steam won't work with wireless LAN"
date: 2010-06-18
forum: Wine
---

### Post by Toxicbits on 2010-06-18
Hi,

I just installed Steam via PlayOnLinux using Wine 1.1.42 and didn't have the Update problem. It works fine, except for the case that I'm using Wlan. I have a > Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) and surfing or using Skype works without any problems. When I try to start Steam while using my Wifi connection it sais Steam - Updating (Updating Steam...), then a window opens stating that my account would connect and finally asks whether it should restart in offline mode.

When I do so this message appears:
   > Steam - Error 

Cold not connect to Steam network. This could be due to a problem with your Internet connection, or with the Steam network. Please visit [www.steampowered.com]("http://www.steampowered.com") for more info.I don't have a Graphics card, I use this system only to test stuff.


Console output:


```
env WINEPREFIX="/home/username/.PlayOnLinux/wineprefix/Steam" wine "C:\Program Files\Steam\Steam.exe" 
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
err:ole:RevokeDragDrop invalid hwnd 0x100a0
err:ole:RevokeDragDrop invalid hwnd 0x100b0
err:ole:RevokeDragDrop invalid hwnd 0x100b6
err:ole:RevokeDragDrop invalid hwnd 0x100b4
Shutting down. . .
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```Any suggestions would be appreciated

---

### Post by asdfoo on 2010-06-18
Update to wine-1.2-rc4.
The version you are using is quite old.

---

### Post by Toxicbits on 2010-06-18
Thanks a lot. I didn't think about that I'll try it later.:p

---

