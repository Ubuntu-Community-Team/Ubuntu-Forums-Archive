---
title: "Dragon Age dlc nightmare"
date: 2010-10-05
forum: Wine
---

### Post by harvodan on 2010-10-05
Hello,

Got a really frustrating problem with Dragon Age Origins under wine 1.3.4 with Ubuntu maverick 64 bit. The game functions fairly well with the exception of downloadable content, at least for me. The wine appdb entries for this game as of late have been claiming that dlc can be used and authenticated successfully, in some cases while running the game in offline mode. 

Anyway, I can't get my dlc to authorize no matter what I do. Whether I'm logged in or out it still shows up as unauthorized. the account is fine because I've tried it under windows, and at one point I could at least use my dlc by forcing the game not to try to authorize my content, but now I have no luck at all with it.

Terminal output for running the daupdatersvc service, which runs in the background and checks your dlc.

sirbubbles@sirbubbles-desktop:~$ wine net start daupdatersvc 
The Dragon Age: Origins - Content Updater service is starting. 
fixme:sync:CreateMemoryResourceNotification (0) stub 
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceProcess" 
fixme:shell:URL_ParseUrl failed to parse L"System" 
fixme:shell:URL_ParseUrl failed to parse L"DAUpdater.Engine" 
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration" 
fixme:shell:URL_ParseUrl failed to parse L"System.Xml" 
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented TransmitFile 
fixme:shell:URL_ParseUrl failed to parse L"System.resources" 
fixme:shell:URL_ParseUrl failed to parse L"System.resources" 
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceProcess.resources" 
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceProcess.resources" 
The Dragon Age: Origins - Content Updater service was started successfully.

In addition the dragon age log file makes repeated mention of the following. 
DA Download Manager (DADM)	Connected to DADM Control Server!
DA Download Manager (DADM)	Failed to configure DADM!

This is using the steam version of Dragon Age.

EDIT - seems this bit with the dragon age log files was due to a mainline kernel I had installed, after reverting to stock kernel this changes to the following:
DA Download Manager (DADM)	Could not connect to DADM Control Server!

---

