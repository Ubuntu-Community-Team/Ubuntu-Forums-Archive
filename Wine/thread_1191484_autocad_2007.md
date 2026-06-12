---
title: "autocad 2007"
date: 2009-06-19
forum: Wine
---

### Post by Mia1990 on 2009-06-19
ok i am trying to install autocad 2007using wine but i keep getting this error on autocad
and when i open the log i get this can someone help me with this please i also run rosetta
stone with no problem using wine 1.1.23 and i would like to keep that running as good as
it does but i need autocad for class

2009/6/19:00:50:55    mia    mia-laptop    === Installation started on mia-laptop by mia === 
2009/6/19:00:51:10    mia    mia-laptop    Install    MSI Runtime 3.1    Skipped    Windows Installer upgrade is not required. System Version = 3.1.4000.2435 
2009/6/19:00:52:17    mia    mia-laptop    Install    .NET Framework Runtime 2.0    Failed    Installation aborted, Result=1603 
2009/6/19:00:52:17    mia    mia-laptop    === Installation ended ===

---

### Post by Mia1990 on 2009-06-19
ok i installed wine tricks and did the .net 2 and i got this error now it said the .net framwork wass installed but the error say it isn't here is the error please help

2009/6/19:02:15:57    mia    mia-laptop    === Installation started on mia-laptop by mia === 
2009/6/19:02:16:06    mia    mia-laptop    Install    MSI Runtime 3.1    Skipped    Windows Installer upgrade is not required. System Version = 3.1.4000.2435 
2009/6/19:02:16:06    mia    mia-laptop    Install    .NET Framework Runtime 2.0    Skipped    .NET Framework Runtime upgrade is not required. System Version = 2.0.50727.0 
2009/6/19:02:16:06    mia    mia-laptop    Install    .NET Framework Runtime 2.0 Language Pack    Skipped    Installation not required 
2009/6/19:02:16:18    mia    mia-laptop    Install    DirectX 9.0 Runtime    Failed    Failure is ignored, Result=-9 
2009/6/19:02:16:23    mia    mia-laptop    Install    MDAC 2.7    Succeeded      Command = "D:\Bin\acadFeui\support\mdac_typ.exe" /q:a /c:"setup.exe /qnt" 
2009/6/19:02:16:40    mia    mia-laptop    Install    Autodesk DWF Viewer    Succeeded      Command = "D:\Bin\acadFeui\support\aev\DWFViewerSetup.exe" /u2 /q2 /b0 
2009/6/19:02:16:42    mia    mia-laptop    Install    Flash    Succeeded      Command = "D:\Bin\acadFeui\support\flash\Install Flash Player 8 AX.exe" /q 
2009/6/19:02:16:57    mia    mia-laptop    Install    AutoCAD 2007    Failed    Installation aborted, Result=1603 
2009/6/19:02:16:57    mia    mia-laptop    === Installation ended ===

---

### Post by m4tic on 2009-06-19
dual boot with windows on this one, i also got problems with installing solid works.

---

### Post by Mia1990 on 2009-06-19
i can get the dwf viewer to install but i dont think it see that i have the .net framework and direct x installed.i only use two piece's of software and Rosetta stone works great in wine there has to be a way to get autocad to work in wine too.

---

### Post by m4tic on 2009-06-19
i think auto cad and solid works are large programs and use a lot of resources and you have to remember that wine is really a small emulator, i think for wine to be able to run CAD programs it will take half the time it took to create win NT:popcorn:

---

### Post by Mia1990 on 2009-06-19
maybe a autocad clone like [bricsys ]("http://www.bricsys.com/en_INTL/")it will read and write autocad's newest format and is very light weight do you think that would work better?

---

### Post by Mia1990 on 2009-06-19
I was just on bricsys site and they have a version for linux but its for[COLOR=Black] redhat and fedora
could i install one of them?
[/COLOR]

---

### Post by Chronon on 2009-06-19
That's good to know!  Still a bit pricey for me, though.

---

### Post by Mia1990 on 2009-06-19
they have a version for linux but its for[COLOR=Black] redhat and fedora
could i install one of them?anyway thank you so much for
your help

xoxo

Mia
[/COLOR]

---

### Post by m4tic on 2009-06-19
I dont know about those

---

### Post by dmizer on 2009-06-19
If you ever have difficulty installing something in Wine, always stop in at the wineHQ to see what other people have done: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=86](http://appdb.winehq.org/objectManager.php?sClass=application&iId=86)

Unfortunately, autocad 2007 doesn't appear to work at all. If possible, you might get away with using 2006 instead?

---

### Post by Mia1990 on 2009-06-20
ok i have downloaded a trial of autocad 2010 that is what my school prefer's.I have it installed all is fine with it and there is no crashing but there is one problem i have 512 mb of ram on my video card and 3 gb of ram in the computer running wine 1.1.23 and autocad is still slow real slow how could i speed it up or is there a way

thank you

---

### Post by dmizer on 2009-06-20
> **Mia1990 said:**
> ok i have downloaded a trial of autocad 2010 that is what my school prefer's.I have it installed all is fine with it and there is no crashing but there is one problem i have 512 mb of ram on my video card and 3 gb of ram in the computer running wine 1.1.23 and autocad is still slow real slow how could i speed it up or is there a way

thank you

If you're using advanced desktop effects (compiz), you should probably disable them while running CAD. Beyond that, not sure.

---

### Post by Mia1990 on 2009-06-20
Thank you so much i'll try that and post back

xoxo

---

### Post by Mia1990 on 2009-06-22
ok a no go on that i have read running it in the terminal may show were the problem is so could anyone tell me how to do that i am new to wine i used linux a few years ago but never wine.Thank you for Any help i sure need it

---

### Post by dmizer on 2009-06-23
Open up a terminal and enter a command similar to the following:
```
wine /path/to/autocad.exe
```

---

### Post by NightMKoder on 2009-06-24
slowness most likely related to DIB engine. (wine bug 421). Nothing you can do until alexandre deems it a priority (its not really)

---

### Post by executorvs on 2009-06-24
you can try installing the RPMs for bricsys using alien.

---

### Post by Mia1990 on 2009-06-25
bricsys has a linux version but it says for red hat and fedora is there a way to install them on ubuntu?I read that there is a program that lets you convert from one one distribution to another but i can't remenber what it was can it be done?

---

### Post by executorvs on 2009-06-25
RPM are the format most commonly used in fedora. Alien is a program which allows you to convert these packages for use on your system. beyond that I don't have much information to offer you. if you find some more clarification please share.

to get you started.
[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)
[http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html](http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html)

[http://ubuntu-snippets.blogspot.com/2009/02/install-rpm-packages-on-ubuntu.html](http://ubuntu-snippets.blogspot.com/2009/02/install-rpm-packages-on-ubuntu.html) (most recent)

---

### Post by fernandonnz on 2012-02-25
Hi.
Try with Autocad 2004. I've installed and it works ok.
With 2007 version I've the same error message.
Bye.

---

### Post by howefield on 2012-02-25
Closed.

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

