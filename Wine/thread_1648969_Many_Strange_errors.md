---
title: "Many Strange errors"
date: 2010-12-19
forum: Wine
---

### Post by Terrum on 2010-12-19
Okay so there's many things I'm trying to do succeed:
I want to play WoW and Steam on Ubuntu. I have followed many forums and tutorials. I have the latest ATI drivers and catalyst control center installed from the .run file on the ati's official website.

I have WoW and Steam already installed on an external drive which is plugged into my PC all the time.

Now everything I try open always comes up with a weird "X Error of failed request" error. Even when I write glxinfo | grep rendering

Error for WoW.exe:
> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  202
  Current serial number in output stream:  202

Error for glxinfo | grep rendering:
> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18

Steam actually loads fine, then after a while of it saying "Connecting Steam account: ***" (*** is my username) it closes then the terminal says:
> CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: CSDS returned 168 servers.
CellID: Connecting to 203.77.185.182:27031. . .
CellID: Connect to 203.77.185.182:27031 took 297 MS
CellID: Nothing beat our old best time of 27 MS
fixme:mixer:ALSA_MixerInit No master control found on Generic USB Audio Device   , disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x1f1de8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x42abeb8)
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  9602
  Current serial number in output stream:  9602

Last but not least, When I try open PlayOnLinux, It says an alert "You don't seem to have 3D acceleration! We advise you install and enable it." with a "Do not alert me anymore" checkbox. I have the drivers installed though so I'm confused.

Yes I have Wine installed + PlayonLinux. Am running latest version of Ubuntu Desktop (installed with Wubi) newly installed today. Am using 2 monitors with multi-display desktop provided by the catalyst control center. Any help is appreciated!

EDIT: I figure it's the graphics. Because everything graphical runs slowly (Like scrolling, or moving windows) has a huge fps drop rate when moving/scrolling. I still need big urgent help! :D Thanks.

---

### Post by Terrum on 2010-12-20
Bump? This is still quite urgent :S

---

### Post by SoFl W on 2010-12-20
Playing a game is urgent? 

Sure, Wizard of Wor was a great game in its time, but hardly urgent.

---

### Post by cwwilson721 on 2010-12-20
Have you tried installing the drivers for ATi from System > Administration >Additional Drivers? I'd do that first, because your 'driver install' didn't work, no matter what you think.

---

### Post by Terrum on 2010-12-21
> **SoFl W said:**
> Playing a game is urgent? 

Sure, Wizard of Wor was a great game in its time, but hardly urgent.
Gaming is always urgent to addicts ;) But really I just wanted a swift reply. Wasn't THAT urgent.
> **cwwilson721 said:**
> Have you tried installing the drivers for ATi from System > Administration >Additional Drivers? I'd do that first, because your 'driver install' didn't work, no matter what you think.
No matter what I think? I never said it installed successfully in the first place lol. That's why I asked here. I even said I don't think it installed the ATI drivers properly.

But I'll try that method of "Additional Drivers". Many Thanks.

---

### Post by dino99 on 2010-12-21
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

of course, use the latest wine and make tweaks with winetricks if needed

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

