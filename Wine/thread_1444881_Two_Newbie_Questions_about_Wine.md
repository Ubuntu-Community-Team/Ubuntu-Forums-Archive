---
title: "Two Newbie Questions about Wine"
date: 2010-04-01
forum: Wine
---

### Post by grandsatrap on 2010-04-01
1. I am having trouble starting programs in Wine. I read that you can also do this from the command line. I have put a small Windows utility called convert.exe in various folders and I am trying to find out why I can't run it.

Locations of convert:
```
griffin@octopus:~$ pwd
/home/griffin
griffin@octopus:~$ find . -iname convert\.exe
./Convert.exe
./.wine/drive_c/Convert.exe
./.wine/drive_c/Program Files/Convert.exe
./.wine/Convert.exe
./Desktop/Convert.exe

```

Results of typing in "wine convert.exe"
```
wine convert.exe
Warning: could not find DOS drive for current working directory '/home/griffin', starting in the Windows directory.
wine: could not load L"C:\\windows\\system32\\convert.exe": Module not found

```
This happens when convert.exe is in (i) my home folder, (ii) my Desktop folder and (iii) my .wine folder.
"wine convert.exe" only works in "drive_c" and in "Program Files"

What does the error message mean? Does it mean that I have to put all of my programs in c:\windows\system32 ? That sounds crazy and I'm not going to do that. 
Can in only run Windows programs if they are in drive_C ?

2. I read somewhere that when I run an Windows program, the program name is **automatically added to the Wine menu** (under the Applications top level menu). This would be very convenient, but it has never happened to me. How do I get this working?

[I'm using Wine 1.0.1, Ubuntu 9.04]

---

### Post by donkyhotay on 2010-04-02
In order to run a windows program in wine with the CLI you need to run wine first and then have wine run that program. Assuming that the program convert.exe is located in your home folder and that is your current working directory then you would simply go
```

wine ./convert.exe

```
Which tells the computer "run wine, have wine use the convert.exe file located in my current working directory. If you just go
```

./convert.exe

```
then that tells the system you are attempting to run convert.exe itself directly as if it was a native linux program. Now if convert.exe isn't located in your home folder (most people usually put this in their .wine folder) then you would need to specify the folder the program is in. Windows programs that 'install' will usually automatically create entries in your menu however running a binary that doesn't need to install won't do that. If you're planning on using the CLI to run this program then you should do a little research on how to use basic BASH commands. Even if you're not going to do that it would be a good idea to know how to do that. Running wine through the CLI is essential for troublehooting when it doesn't work right.

---

### Post by grandsatrap on 2010-04-02
> **donkyhotay said:**
> In order to run a windows program in wine with the CLI you need to run wine first and then have wine run that program. Assuming that the program convert.exe is located in your home folder and that is your current working directory then you would simply go
```

wine ./convert.exe

```
Which tells the computer "run wine, have wine use the convert.exe file located in my current working directory. 

Hey, you're right! 
```
wine ./convert.exe
``` gives a different error from ```
wine convert.exe
```
My error is now ```
Warning: could not find DOS drive for current working directory '/home/friggit', starting in the Windows directory.
```
This happens in my home directory, in my desktop directory, and in my .wine directory.

I think that what Wine (and you) are telling me, is that the only way that I can run programs with Wine is if they are in ~/.wine/drive_c . Is that right? 
(I am moderately good at the command-line, I just don't know much about Ubuntu GUI - I've been running an Ubuntu server for a while).

Thanks for explaining the adding to menus thing too!

---

### Post by donkyhotay on 2010-04-02
The 'dot' at the beginning of ./convert.exe specifies the directory you are in right now (usually you're home directory). If you don't put it there then wine isn't 100% certain where to look and starts trolling through your "C:" drive (~/.wine/drive_c/) which is where wine tells windows programs your "C:" drive is located. If it isn't in there wine will have issues finding it. However by specifying ./convert.exe you tell wine exactly where the file is located so there isn't any issues. Now this can be changed, check winecfg to find out where your "C:" drive is reported. It sounds like ./convert.exe can't find the C: drive (which may not be set up in winecfg yet) and it's required. In general you can run windwos programs from anywhere within your filestructure, not just the drive_c folder. I often run installers for windows programs from my home directory without any issue.

---

### Post by grandsatrap on 2010-04-03
Even though this is clean install of Ubuntu 9.04, something wasn't working in Wine. The only other responses to errors like this: "Warning: could not find DOS drive for current working directory '/home/griffin', starting in the Windows directory." were to delete .wine (or move it to .wine.bak) and run winecfg.

After doing this, I can now run Wine programs from anywhere. Very weird. It seems that the initial Wine install is a bit non-functional (at least in my case). 

Thanks for your help -- I'm off to use wine. 

* I think I'll be using MS Word 2000 for a while, Open Office is different enough that it is really slow for me to do things in.

---

