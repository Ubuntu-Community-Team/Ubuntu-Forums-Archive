---
title: "Fallout 3 Cannot Run"
date: 2010-01-27
forum: Wine
---

### Post by Hman242 on 2010-01-27
I'm sure you have been pounded with threads like this, but I can't get Fallout 3 to run. When I run it, it says [this]("http://img8.imageshack.us/img8/5976/screenshotmzn.png"). Obviously it says Fallout3.exe instead of what it currently says. Once I run it and close it, if I try to run it again it says that's there is already an instance of of it running. WineHQ says I need to have gfwlivesetupmin to be able to run Fallout 3, but when I try to run it, it says what it says in the link above. I have no idea what to do. Could anyone help me?

---

### Post by brian70809 on 2010-01-27
From WineHQ:

[SIZE=2]by [NSLW]("http://appdb.winehq.org/contact.php?iRecipientId=117047") on (December 10th 2009)           [/SIZE]   Patch 1.7 requires Games for Windows - Live 3.0 client. To install it follow these steps:                              

   1) Download **msasn1.dll** from e.g. [here]("http://www.dllbank.com/zip/m/msasn1.dll.zip")     
2) Override **msasn1.dll** in Wine Configuration. [How to Override DLL]("http://www.winehq.org/docs/wineusr-guide/config-wine-main")     
3) Download **gfwlivesetupmin.exe** from e.g. [here]("http://download.microsoft.com/download/5/5/8/55846E20-4A46-4EF8-B272-7F988BC9090A/gfwlivesetupmin.exe")     
4) Install **gfwlivesetupmin.exe** but without .NET Framework                              
5) Only set **xlive** to native in Wine Configuration.                              
6) Download and install 1.7 patch for Fallout 3

---

### Post by Hman242 on 2010-01-27
I have the .dll and the patch. gfwlivesetupmin.exe won't run.

---

### Post by gsmanners on 2010-01-27
In my experience, you're better off without GfWL. If you're willing to disable it, you should try this:

[http://www.fallout3nexus.com/downloads/file.php?id=1086](http://www.fallout3nexus.com/downloads/file.php?id=1086)

---

### Post by Hman242 on 2010-01-28
Is there a certain place I need to put it or can I just run it? I put in in with F3 and ran it, it said it worked. I'm still can't get the game running.

---

### Post by gsmanners on 2010-01-29
If you disable GfWL then it's not an xlive problem. It has to be some other problem.

About the install: Did it go okay? Did you run the launcher at least once? Do you have any mods? Is your system capable of playing Fallout 3?

---

### Post by Hman242 on 2010-01-29
I ran the installer. I uninstalled and reinstalled it before posting the thread. My system can run the game bare minimum, and the graphics are set to low. I don't know what the problem could be.

---

### Post by Hman242 on 2010-02-01
Ok, I think I've got it to a point that will be able for you guys to actually try to help because it's not so vague. When I run it now, it comes up with "failed to initialize renderer". However, that only appears when I click the windowed button. When it isn't clicked, nothing even comes up when I press play. Any idea what the problem is?

---

### Post by brian70809 on 2010-02-01
Go into Terminal and type:

glxgears

if you don't see a set of gears spinning on your screen, then your OpenGL drivers are not working and you need to install them.

Download the latest drivers for your video card.

---

### Post by Hman242 on 2010-02-01
Gears appear when I type that. Should I still update my drivers anyway?
EDIT: Seems like Ubuntu or Debian isn't listed under the Linux distros that are supported. The distro that are on the list are Fedora 10, Fedora Core 7, Wind River Linux, and Red Hat Linux. What should I do? [This]("http://edc.intel.com/Software/Downloads/IEGD/#overview") is my chip.

---

### Post by gsmanners on 2010-02-02
Ubuntu is well-supported. What isn't supported is your video.

see [http://www.bethsoft.com/bgsforums/index.php?showtopic=892715&view=findpost&p=13705368](http://www.bethsoft.com/bgsforums/index.php?showtopic=892715&view=findpost&p=13705368)
see also [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)

---

### Post by Hman242 on 2010-02-02
After posting my last post I ran it in WINE and it said that it worked. I still can't run Fallout 3.

---

### Post by gsmanners on 2010-02-03
> **Hman242 said:**
> After posting my last post I ran it in WINE and it said that it worked. I still can't run Fallout 3.

You accidentally the whole thing?

---

### Post by Hman242 on 2010-02-03
What?

---

### Post by gsmanners on 2010-02-03
You wrote "it worked" and "still can't run". Well, which one is it?

---

### Post by Hman242 on 2010-02-03
Installing the drive in WINE seemed to work, but I still can't run Fallout 3. If my graphics card isn't listed in the list above, does that mean I can't run it?

---

### Post by gsmanners on 2010-02-04
I'll quote the thread:

> Minimum System Requirements:

Windows XP/Vista
1GB System RAM (XP)/ 2GB System RAM (Vista)
2.4 Ghz Intel Pentium 4 or equivalent processor
Direct X 9.0c compliant video card with 256MB RAM (NVIDIA 6800 or better/ATI X850 or better) 

I don't see anything in the above requirement about low-power, embedded Intel video hardware. In other words, it will not work. The fact is, the game *barely* works with NVIDIA 7600, which is a far better piece of hardware for video.

---

