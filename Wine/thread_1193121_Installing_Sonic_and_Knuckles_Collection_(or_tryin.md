---
title: "Installing Sonic and Knuckles Collection (or trying to)"
date: 2009-06-21
forum: Wine
---

### Post by anthony62490 on 2009-06-21
One of my all-time favorite games is Sonic the Hedgehog 3. Trying everything I can think of, but I'm not having much luck.

One thing I don't remember seeing under Windows was the four files that look like installation files, so I just tried all of them one-by-one.

Here's the output:
```
**Install:**
anthony@anthony-desktop:/media/cdrom0$ wine INSTALL.EXE 
**Nothing seems to happen.**
```

```
**Launch:**
anthony@anthony-desktop:/media/cdrom0$ wine Launch.exe 
fixme:ole:OLEPictureImpl_SaveAsFile (0x132a68)->(0x132e10, 0, (nil)), hacked stub.
err:heap:GlobalFree (0x1002): Page fault occurred ! Caused by bug ?
anthony@anthony-desktop:/media/cdrom0$ fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
fixme:shell:DllCanUnloadNow stub

[B]This one installs Acrobat Reader 3.0 the first time it is run. 
The second time, it opens up the instructions file...[/B]

wine Launch.exe 
fixme:ole:OLEPictureImpl_SaveAsFile (0x132a68)->(0x132e10, 0, (nil)), hacked stub.
err:heap:GlobalFree (0x1002): Page fault occurred ! Caused by bug ?
```

```
[B]Setup:
This one looks and acts like it is going to install, but after I click the install button, 
the folder is about empty. Only one autorun file and one called Register.exe[/B]
anthony@anthony-desktop:/media/cdrom0$ wine Setup.exe 
fixme:mciavi:MCIAVI_mciPut PUT_WINDOW (1,1)-(500,394)
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

```

```
**Start:**
anthony@anthony-desktop:/media/cdrom0$ wine Start.exe 
**Again, nothing at all happens.**
```

WINE is set to run under Windows 2000 and I have not added any DLLs just yet.

Any ideas for me to try, or does it look hopeless?

EDIT: Using WINE 1.0.1

---

### Post by FrozenFox on 2009-06-21
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5339](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5339)

This suggests it was working on the stable wine version 1.1.0 at least decently once the game is patched. What version of wine are you on? wine --version . 

That said, you could accomplish the same thing as this better using a native linux Genesis emulator (I think there's a new and much better version of Gens around, and old versions of Dgen and Generator), but I won't go into detail, on the assumption these forums wouldn't like it. Is there any particular reason you're preferring this pc version?

---

### Post by anthony62490 on 2009-06-21
No reason in particular, it's just the same version that I have always used. But a Genesis Emulator would probably do the job much better (though I try to keep my ROM downloads to a minimum...).

That being said, I am pretty new to Linux (only six months or so), so I am trying to get a feel for it. Learning to use WINE effectively is near the top of my to-do list. I'll try it out with version 1.1.0. and see if it works.

---

### Post by NightMKoder on 2009-06-21
You should install the latest wine and try that (they keep improving): [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) .

---

### Post by anthony62490 on 2009-06-21
I installed 1.1.24, but no luck. For now I've got an emulator up and running, but I will continue checking for new versions of WINE.

Thank you for your help.

---

