---
title: "Steam crashes after launch (Memory dump problem)"
date: 2009-02-24
forum: Wine
---

### Post by barronmb on 2009-02-24
I installed steam per the instructions at [winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554")... and have tried a few other methods. However, after I launch and login, I get the main window for a second and then it crashes and dumps out to a mdmp file.  I tried the sysctl file edit trick but that did no good.  I searched here and all over the web. Other people are having this problem but I haven't been able to find a solution yet. 

Here's the output:

> fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: Fetching server list from CSDS. . .
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: CSDS returned 154 servers.
CellID: Connecting to 208.111.140.6:27031. . .
CellID: Connect to 208.111.140.6:27031 took 100 MS
CellID: Nothing beat our old best time of 15 MS
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0x946fcc "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)
fixme:shdocvw:ViewObject_SetAdvise (0x186b08)->(1 00000002 0x136de40)
fixme:shdocvw:PersistStreamInit_InitNew (0x186b08)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x186b08)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x186b08)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x187108)->(1 00000002 0x136e068)
fixme:shdocvw:PersistStreamInit_InitNew (0x187108)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x187108)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x187108)->(ffffffff)
fixme:win:RegisterDeviceNotificationA (hwnd=0x10086, filter=0x32e088,flags=0x00000004),
	returns a fake device notification handle!
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7befe9f8, overlapped 0x7befe9dc): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x576ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x186ba4)->((null) 1 0x32bc10 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x186ba4)->((null) 25 2 0x32bc24 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x186ba4)->((null) 26 2 0x32bc24 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000170
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x186ba4)->(0x32bc60)
fixme:shdocvw:ClOleCommandTarget_Exec (0x186ba4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32bd34 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1a36e0)->(L"" L"" 0 0x32bd6c)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:shdocvw:ClOleCommandTarget_Exec (0x186ba4)->((null) 29 2 0x32d9f8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x186ba4)
fixme:shdocvw:ClientSite_GetContainer (0x186ba4)->(0x32d9ac)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x186ba4)->(0xf7eb0db5)
fixme:shdocvw:ClOleCommandTarget_Exec (0x186ba4)->((null) 25 2 0x32d8e0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x186ba4)->((null) 26 2 0x32d8e0 (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x580a6b8)->(L"no")
err:mshtml:HTMLElement_insertAdjacentHTML CreateTextNode failed: 80070057
fixme:mshtml:HTMLDocument_get_title (0x1a4038)->(0x32d02c)
fixme:mshtml:HTMLDocument_put_ondragstart (0x1a4038)
fixme:mshtml:HTMLBodyElement_put_scroll (0x580a6b8)->(L"no")
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x186b08)->(0x32c808)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x186b08)->(0x32c808)
fixme:mshtml:HTMLBodyElement_put_scroll (0x580a6b8)->(L"no")
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x186b08)->(0x32cc5c)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x186b08)->(0x32e000)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x186b08)->(0x32e000)
fixme:shdocvw:ClOleCommandTarget_Exec (0x186ba4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x186ba4)->((null) 28 2 0x32d9e8 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
**fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set**


System info:
Wine version is current stable 1.0.1
Ubuntu 8.10 amd64
AMD 64 x2 3000
4gb RAM
nVidia gx260

As a side question: How do manage to install steam games from my regular browser. I click the "I already have steam installed" button and I get an error b/c the steam protocol isn't associated. (I ask b/c apparently it can no longer be done through the "store" section of steam window due to flash and browsing issues).

Any detailed help is much appreciated.
Thanks.

---

### Post by NightMKoder on 2009-02-24
Seems you don't have gecko installed. Check to see that 'wine iexplore [http://winehq.org](http://winehq.org)' starts fine. If not, then you need to do the winetricks gecko install:
> 
cd ~
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh ./winetricks gecko


---

### Post by barronmb on 2009-02-25
> **NightMKoder said:**
> Seems you don't have gecko installed. Check to see that 'wine iexplore [http://winehq.org](http://winehq.org)' starts fine. If not, then you need to do the winetricks gecko install:

Yes, I already did that.  That was part of the winehq HowTo.  iexplore launches and winehq shows in it just fine.  Never did ask for me to install anything though.. I believe gecko was already installed.

---

### Post by NightMKoder on 2009-02-25
You probably have an old version of gecko installed then.

Try the following:

```

sudo apt-get remove wine-gecko

cd ~/.wine/drive_c/windows
mv gecko gecko_old
wine iexplore http://winehq.org

```

This will prompt you to install gecko. See if that helps.

---

### Post by barronmb on 2009-02-26
Night,

  Gave that a whirl but it didn't stop the crashing.  Any more thoughts?

---

### Post by NightMKoder on 2009-02-26
So one last relevant suggestion (from appdb):
> 
Steam takes too long to start: (crash 1)

While starting steam actually crashing and writes a small memory dump (*.mdmp files).
To fix this add the following lines to "/etc/sysctl.conf"

# Send and receive buffer sizes to make steam happy
net.core.rmem_max = 131072
net.core.wmem_max = 131072

and run

sysctl -p


Now if the above doesn't work, it may be that you installed something on wine that messes with the gecko engine. Try removing dll overrides from the wine config and if that doesn't work, rename your .wine to something else and try installing steam again.

---

### Post by barronmb on 2009-02-26
The sysctl.conf edit was the first thing that I tried, as mentioned earlier.  It didn't do anything for me.

I'll take a look through the DLLs when I get home.  I haven't added any (except the one for sound in Ventrilo).

---

### Post by barronmb on 2009-02-26
Ok. I checked and have no DLL overrides in place.

I also tried renaming my .wine folder and fresh installing steam.  It installed fine (like always) and I got the Gecko popup asking to install.  I installed it.  Steam began to load and crashed out, exactly as it did before... Not sure what I am missing here.

---

### Post by NightMKoder on 2009-02-26
Man this is a tough one. Alright then - two things to try:

1. Basically reinstall gecko from ubuntu's repositories:
```

cd ~/.wine/drive_c/windows
rm -r gecko
sudo apt-get install wine-gecko

```

2. Install latest beta wine (its not that beta): [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) . Then make sure that you install gecko through wine itself (wine iexplore).

If you could, post a log of steam with the beta wine if it doesn't work.

---

### Post by volcanosc on 2009-07-05
Hi guys
There is a fatal error with current version of wine-gecko which causes almost any application using it crashes 
I've found a possible solution here:
Please do NOT install Gecko
Install ie6 with winetricks instead.

---

