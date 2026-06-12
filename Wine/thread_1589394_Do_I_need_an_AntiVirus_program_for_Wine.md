---
title: "Do I need an AntiVirus program for Wine?"
date: 2010-10-06
forum: Wine
---

### Post by TUA85550 on 2010-10-06
I understand that a Windows virus is harmless on a Linux Operating system (as the virus won’t know what to do since Linux is coded differently).  I also heard it is possible to get viruses from Wine.  If that is the case, do I need to install an Anti Virus program if I am going to be using Wine?

Is there a high risk involved if I am going to be running Wine (since your system is no longer immune to Windows viruses)?  Also, if you do get a windows virus, will the virus only infect the Wine directory or could it cause havoc on your entire Linux operation system?

Is this correct?  If I don’t have Wine installed and come across a web site that has a virus, I am safe.  However, if I have Wine installed and come across a web site that has a virus, I am no longer safe.  Even if I browse the web site in FireFox (the non-wine version / the linux version), I can still become infected.

I just need some clarification with regards to Wine and Viruses and the risks involved.

---

### Post by 6cody5 on 2010-10-07
No, you don't need an antivirus program for wine because you are running on Linux. Wine is a Windows Emulator on your linux partition so linux doesn't natively recognize .exe files or Windows Script files etc. So they just won't run. Your computer will be safe unless the program that is running in Wine downloads a linux virus. WINDOWS VIRUSES ARE ONLY BUILT TO NAVIGATE THROUGH THE WINDOWS DIRECTORY!
Hope that helped!
Cody:popcorn:

---

### Post by Justin_Bailey on 2010-10-07
> **6cody5 said:**
> No, you don't need an antivirus program for wine because you are running on Linux. Wine is a Windows Emulator on your linux partition so linux doesn't natively recognize .exe files or Windows Script files etc. So they just won't run. Your computer will be safe unless the program that is running in Wine downloads a linux virus. WINDOWS VIRUSES ARE ONLY BUILT TO NAVIGATE THROUGH THE WINDOWS DIRECTORY!
Hope that helped!
Cody:popcorn:

There is so much wrong with this reply that I don't even know where to start.
The author of this thread may want to search the forum on this topic as I've seen it covered properly before.

---

### Post by sikander3786 on 2010-10-07
Simple answer "No".

For details, Google "virus wine ubuntu". It has been discussed many times before.

---

### Post by 3Miro on 2010-10-07
Antivirus programs don't run under wine. There are Linux antivirus programs that lok for windows viruses, so if you have a lot of windows files and you are not sure about them, then you may consider that. If you only have games from original CDs and you only install official patches under wine, you should be safe.

A windows virus could affect Linux through wine, however, the odds are small. There are leyers of defenses on top of wine that will prevent almost any virtus from harming anything beyond the .wine or /home/your_username folder.

---

### Post by lisati on 2010-10-07
As always, your best defense **begins** with being smart about what you allow on your system and what you open.

---

