---
title: "exe problem with wine and windows"
date: 2010-06-24
forum: Wine
---

### Post by mighty mouse on 2010-06-24
Hi All
 
Please help me with the latest problem i ma facing :
 
My laptop is dual booted with ubuntu 9.10 and windows 7.in Ubuntu i cant run any exe application with WINE.When i click on an exe application and run with wine...nothing happens.I then booted into my windows partition and all my exe's are unrecognizable.Cant even run regedit.My antivirus protection is also not recognized. 
 
I hope i have placed my problem at the right place and any help would be appreciated.
Please Help !!

---

### Post by sanderd17 on 2010-06-24
Well, Wine is not so good. It has a lot of missing libraries. Could you check if the files are executable first? (in the file properties under ubuntu)

Do you ask now to execute the apps under wine or under windoze? If it's under wine, you don't need an anti-virus.

(Now a bit off topic but not bad to read if you're new to Linux)

I know, when I arrived at Linux, I wanted to execute my normal programs (winamp and some others) but that didn't work and I felt angry. It took some time but I forced myself to learn the Ubuntu/Linux way of doing things (installing software via the repos/software center, using command line if you want to do something quick ...). Now, I can use Ubuntu without a problem. I don't have any non-native Linux program and if I really need one, I can always make a virtual machine (about 15 to 30 minutes work).


I you come from windoze, I might be good to read the [Linux is NOT windows]("http://linux.oneandoneis2.org/LNW.htm") text. It's a text about the idea behind Linux, you won't learn to work with it, you'll just be able to understand why the devellopers made it so.

If you want to work with Linux, I would recommand a beginners tutorial on the commandline and file structure: [http://gd.tuwien.ac.at/linuxcommand.org/]("http://gd.tuwien.ac.at/linuxcommand.org/"). It's a small tutorial but it tells you all you need.

---

### Post by ronnielsen1 on 2010-06-24
> My laptop is dual booted with ubuntu 9.10 and windows 7.in Ubuntu i cant  run any exe application with WINE.When i click on an exe application  and run with wine...nothing happens.I then booted into my windows  partition and all my exe's are unrecognizable.Cant even run regedit.My  antivirus protection is also not recognized. 

Like the other poster said, right click on the exe and make sure it's clicked executable in properties. Google windowssoftware winehq (example ms office 2007 winehq) and this will lead you to [http://www.google.com/search?client=ubuntu&channel=fs&q=ms+office+2007+winehq&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ms+office+2007+winehq&ie=utf-8&oe=utf-8) and the best link out of that will get you to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992) that tells you if there's any special steps you need to do to get it running. You can also open a terminal and type in wine /locationofexefile/file.exe to check for errors. If I had an exe file that I wanted to run that was located on my desktop I would either right click > open with wine or type in /home/username/Desktop/software.exe

There's not much of a need to run antivirus in Linux (I don't) but if you do, use a linux version

---

### Post by mighty mouse on 2010-06-24
thanks guys for the replies!!

I am not relatively new in Linux....but yes still a beginner.

My antivirus was in windows not linux.i was just wondering what happened to all my exe's in windows.and is it because of it , its not working in linux.

---

### Post by Mark Phelps on 2010-06-24
> **mighty mouse said:**
> My antivirus was in windows not linux.i was just wondering what happened to all my exe's in windows.and is it because of it , its not working in linux.
Since Windows uses completely different filesystem model, the only way that you could render your .exe's unexecutable is by removing the .exe file extension.  IF you did not do that, you didn't do anything in Linux to disable your MS Windows programs.

Sounds more like you have some malware infection in MS Windows.

Couple of freeware products that do really good jobs of disinfectinf MS Windows are Malwarebytes anti-malware and SuperAntiSpyware.  Sine the second of these uses a randomly-generated filename, it is quite easy to download and run on an infected machine.

---

### Post by mooreted on 2010-06-24
For times when you might run a Windows application from Wine, I find it helpful to execute it from the command line to see if I get any errors. For instance I have WoW installed and I can run it from the CLI thusly:

wine ".wine/drive_c/Program Files/World of Warcraft/Wow.exe"

If it doesn't run, I can see errors in the terminal that help me fix it.

Generally I avoid Windows programs. For philosophical reasons, I gave up Windows long ago.

---

### Post by TommyfoarRoshie on 2010-06-24
> **mooreted said:**
> For times when you might run a Windows application from Wine, I find it helpful to execute it from the command line to see if I get any errors. For instance I have WoW installed and I can run it from the CLI thusly:

wine ".wine/drive_c/Program Files/World of Warcraft/Wow.exe"

If it doesn't run, I can see errors in the terminal that help me fix it.

Generally I avoid Windows programs. For philosophical reasons, I gave up Windows long ago.

Hai im looking to run wow from the other side of my hard drive so do i do it like that?

---

### Post by philinux on 2010-06-24
Moved to Wine forum.

---

### Post by mooreted on 2010-06-24
> **TommyfoarRoshie said:**
> Hai im looking to run wow from the other side of my hard drive so do i do it like that?

If you have WoW installed on your Windows partition, you can copy your WoW directory to your Wine Program Files directory and run it from there. 

You can't just run Windows executables by opening them from your Windows partition, you usually have to install them like you would in Windows.

Here is a handy guide for getting WoW to run.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

