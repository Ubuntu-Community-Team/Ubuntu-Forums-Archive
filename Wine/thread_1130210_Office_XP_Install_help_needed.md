---
title: "Office XP Install help needed"
date: 2009-04-19
forum: Wine
---

### Post by PT.Linn.A on 2009-04-19
I an own up to my limitations ... most of them anyway.  ;) So, I am waving the white flag and asking for help.

I would like to install Office XP on my Ubuntu 8.10 system.

Tried all of the other self-help sites, and I have failed on my own.

Can anyone provide a little assistance with installing Office XP to me?

---

### Post by ddrichardson on 2009-04-19
I only really need Word but had no problems with it in Heron, installed wine then ran the Office set up and logged out (to get the menu to refresh).```
sudo apt-get install wine
wine /path/to/office/SETUP.EXE
```
Access segfaults but I don't need it at home.

---

### Post by PT.Linn.A on 2009-04-19
Tried the suggested code. Below is the result:

phoenix@pla:/$ wine /media/cdrom0/setup.exe
fixme:advapi:CheckTokenMembership ((nil) 0x12e7b0 0x32eaac) stub!
fixme:imm:ImmDisableIME (-1): stub
err:module:attach_process_dlls "RPCRT4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\msiexec.exe" failed, status c0000005
phoenix@pla:/$ 


Suggestions?

---

### Post by ddrichardson on 2009-04-19
Worked for me, sorry can't be more help.

---

### Post by NightMKoder on 2009-04-19
> **PT.Linn.A said:**
> Tried the suggested code. Below is the result:

phoenix@pla:/$ wine /media/cdrom0/setup.exe
fixme:advapi:CheckTokenMembership ((nil) 0x12e7b0 0x32eaac) stub!
fixme:imm:ImmDisableIME (-1): stub
err:module:attach_process_dlls "RPCRT4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\msiexec.exe" failed, status c0000005
phoenix@pla:/$ 


Suggestions?

Wine version? And also, I'm guessing you used some sort of winetricks/native dlls to install something else. Upgrade wine and start with a fresh prefix. (I suggest installing office in a separate prefix - use `export WINEPREFIX=~/.wine_office` in the terminal you do everything in)

---

### Post by PT.Linn.A on 2009-04-19
> **NightMKoder said:**
> Wine version? And also, I'm guessing you used some sort of winetricks/native dlls to install something else. Upgrade wine and start with a fresh prefix. (I suggest installing office in a separate prefix - use `export WINEPREFIX=~/.wine_office` in the terminal you do everything in)

phoenix@pla:~$ wine --version
wine-1.1.19
phoenix@pla:~$ 

Yes, I installed Winetricks as part of a previous tutorial in this process. Didn't seem to help any. Is Winetricks holding up the process??

I am unfamiliar with how to use export WINPREFIX.

Sorry for being a pain, and unfamiliar. But, I do appreciate the assistance.

---

### Post by NightMKoder on 2009-04-19
Yea - technically the less winetricks/fixes you use the better. Wine doesn't expect some things that windows uses.

To install in a separate prefix (sort of like a separate windows install - the two versions of wine will be completely separate), just do:

```

$ export WINEPREFIX=~/.wine_office
$ wine Setup.exe
....

```

This way your office stays in its own little space (some people call this bottling).

Back to the original problem - Office 2003 suffers from the same regression as Office 2007 - you need to use a version of wine < 1.1.17.
This tutorial: [http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840) is for Office 2007, but it shows you how to install the version of wine you need (1.1.16).

Don't forget to check AppDB [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214) , the HOWTO's there are usually the most reliable.

---

