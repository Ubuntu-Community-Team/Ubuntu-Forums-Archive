---
title: "WINE needs a DLL...how?"
date: 2005-12-10
forum: Wine
---

### Post by Griff on 2005-12-10
I'm trying to install xfire via WINE.  When trying to install I get a message saying WINE needs the following DLL: c:\windows\system32\MSVCRT.DLL

How do you get these DLL files and how would you put them into WINE?

---

### Post by cdsboy on 2005-12-10
that would be a windows dll. either steal it from a windows machine or try to find it on the internet.

---

### Post by Harleen on 2005-12-11
Get the needed DLL and put it in the system directory of your fake windows installation, usually it's ~/.wine/drive_c/windows/system32.
If you use the wine version from the official winehq-repository, you can use the winetools to to that for you. It's the menu point "Visual C++ run-time"

---

### Post by DiscoKiller on 2005-12-11
i have a broken windows install on my hd i havent cleaned out yet, i`ll have a look for the file for you
i have nothing better to do :D

---

### Post by roberine on 2005-12-11
You can download the DLL here:
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcrt](http://www.dll-files.com/dllindex/dll-files.shtml?msvcrt) :)

---

### Post by Griff on 2005-12-11
F'in awesome guys.  I am dangerously close here to getting this up.  I'm getting a message saying that I need to pick where the mozilla bin directory is, but I can't seem to find it.  Is there a default location for this or can I just create it?

edit: tried creating with no luck

---

### Post by Gray. on 2005-12-11
Did you download the mozcontrol.tgz and extract it to ~/.wine/drive_c/Program\ Files?
It should create a folder called mozcontrol in Program Files then you run wine regsvr32 mozctlx.dll

get mozcontrol.tgz [here]("http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz")

---

### Post by Griff on 2005-12-11
[QUOTE=Gray.]Did you download the mozcontrol.tgz and extract it to ~/.wine/drive_c/Program\ Files?
It should create a folder called mozcontrol in Program Files then you run wine regsvr32 mozctlx.dll[/QUOTE]

Did that all that and got the following:

stephen@ubuntu:~$ wine regsvr32 mozctlx.dll
Failed to load DLL mozctlx.dll

---

### Post by MozartlovesUbun2 on 2007-11-24
ok so is there a place where i can just get all these dll or what ever is missing and just put them into wine so i have no problem installing and running what ever window apps i need?

ok well i guess i can take it from the windows installation

**but what do i need?**

---

### Post by hikaricore on 2007-11-25
Thread is two years old.  I suggest making a new one...

---

### Post by trixsta1 on 2007-11-25
<a href="http://www.AWSurveys.com/HomeMain.cfm?RefID=trixsta"><img src="http://www.AWSurveys.com/Pictures/AWS_ad3_150by150.jpg" width="150" height="150"></a>

---

