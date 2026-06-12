---
title: "Full tilt poker and wine"
date: 2010-02-12
forum: Wine
---

### Post by budaslap on 2010-02-12
Hi, I am running karmic, and have wine version 1.0.1, and I am trying to get Full Tilt poker to work. I searched, and couldn't find anyone having my same problem.

The install seems to have gone OK, but when I try and run FT, nothing happens, I have tried every compatibility option. Strangely when I use wine to run the uninstaller, that works fine, just not the actual program.

Anyone have any suggestions?

Thanks

---

### Post by budaslap on 2010-02-12
> dave@dave-desktop:~$ wine C:\\fulltiltpoker
err:module:import_dll Library libexpat.dll (which is needed by L"C:\\fulltiltpoker.exe") not found
err:module:import_dll Library QtWebKit4.dll (which is needed by L"C:\\fulltiltpoker.exe") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\fulltiltpoker.exe") not found
err:module:import_dll Library QtXml4.dll (which is needed by L"C:\\fulltiltpoker.exe") not found
err:module:import_dll Library QtGui4.dll (which is needed by L"C:\\fulltiltpoker.exe") not found
err:module:import_dll Library QtNetwork4.dll (which is needed by L"C:\\fulltiltpoker.exe") not found
err:module:import_dll Library QtCore4.dll (which is needed by L"C:\\fulltiltpoker.exe") not found
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc4572d


Here is the output from Wine, seems I'm missing some DLLs, still no clue what to do next.

---

### Post by MrNatewood on 2010-02-12
Looks like you are missing the QT libary that is supposed to install along with Full Tilt.

Something went wrong during the install process. I suppose you have tried re-installing.

I'd suggest upgrading wine to latest version:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
And re-installing.

---

### Post by budaslap on 2010-02-12
Yeah I tried reinstalling, I'll update wine(thought I had newest version) and see if that helps.

---

### Post by budaslap on 2010-02-14
Well, I wound up completely uninstalling wine, then starting again from scratch. Seems to have solved the problem, I'm pretty sure the problem was that I installed FT on the old version of wine, so the DLL's didn't properly install.

Thanks for the help MrNatewood

---

### Post by kolo-01 on 2010-02-15
You need to run Wine 1.2 version to get full tilt to work

go to software sources in system > admin, other software tab and put this ppa in the bar

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)

then go to synaptic package manager reload the repositories, and you should then find wine 1.2 available for download, once you have, set the wine version to windows 98

full tilt works ok on my machine but sometimes it is quite unstable, maybe it will be fixed when wine is officially updated as i think this is a beta version

---

### Post by MrNatewood on 2010-02-15
> **kolo-01 said:**
> 
full tilt works ok on my machine but sometimes it is quite unstable, maybe it will be fixed when wine is officially updated as i think this is a beta version

To make full tilt more stable, try going into wine config and changing the audio driver from ALSA to EsoundD.

---

### Post by kolo-01 on 2010-02-22
> **MrNatewood said:**
> To make full tilt more stable, try going into wine config and changing the audio driver from ALSA to EsoundD.

spot on mr.natewood

---

