---
title: "Trying to get Everquest to work in Ubuntu"
date: 2009-06-16
forum: Wine
---

### Post by replambe on 2009-06-16
Hello, I don't know if I'm doing this right, but I've been trying to get Everquest to run in Wine for a while now, and so far nothing has worked. I am using the latest version of Wine and also using Jaunty. I am new to Linux. I have tried many different threads on various sites, including this one. Here is what the terminal says when I run LaunchPad.exe:

  	 	 	 	 	 	  Bootstrapper version = release-728753 
 Started with args = LaunchPad.exe 
 Running Bootstrapper... 
 Performing basic setup and system checks... 
 Info: Running on system=Windows XP, wordsize=32 
 Set working dir=C:/Program Files/Sony/Station/Station Launcher 
 Checking for self-installation... 
 No newer self-update in tmp 
 Checking for self-patch... 
 Getting mod time for url=http://lpconfig.patch.station.sony.com:7000/patch/lp2/lpconfig/live/launcher/self/LaunchPad.exe 
 checking status-> storedLastChecksum=6762496, storedRemoteLastMod=1234924521, remoteLastMod=1234924521, myChecksum=6762496 
 No self-patching needed 
 Translating running context... 
 Setting context to self-image default (LaunchPad2) 
 Station Launcher was not running at the time of acquiring its mutex 
 Getting next image... 
 WAITING_FOR_REQUEST 
 lp2-live: Cache check implies no update is required. 
 Stop requested, but i'm not running  
 Updater exit status: 2 
 Executing next image... 
 Start Process exec=C:\Program Files\Sony\Station\Station Launcher\LaunchPad2\StationLauncher.exe, args=, workingDir=C:\Program Files\Sony\Station\Station Launcher\LaunchPad2 
 Bootstrapper run completed 
 [email]replambe@ralph:~/.wine[/email]/drive_c/Program Files/Sony/Station/Station Launcher$ fixme:advapi:CheckTokenMembership (0xe8 0x33fbcc 0x33fb9c) stub! 
 fixme:sync:CreateTimerQueue stub 
 fixme:sync:CreateTimerQueueTimer stub 
 fixme:sync:CreateTimerQueueTimer stub 
 fixme:sync:CreateTimerQueueTimer stub 
 fixme:sync:CreateTimerQueueTimer stub 
 fixme:sync:CreateTimerQueueTimer stub 
 fixme:win:FlashWindowEx 0x33dea0 
 fixme:win:FlashWindowEx 0x33e220 
 fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE) 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE) 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
 fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented 
  
 

My computer is fully capable of running EQ, Wine, and Linux. Any help would be greatly appreciated. If you need more info let me know, thank you.

---

### Post by kanamor on 2009-06-22
Hello, u can play Everquest following this guide

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2939](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2939)

I have playing now to Everquest with ubuntu jaunty and the last beta version of wine 

[IMG]http://i130.photobucket.com/albums/p242/kanamor/Pantallazo-5-1.png[/IMG]

im in BB server, /tell kanamor

---

