---
title: "Why can't I install executable files from a CD in 10.4??"
date: 2010-08-02
forum: Wine
---

### Post by icebeat on 2010-08-02
I know that by right clicking the executable file and clicking properties, I can choose the permissions tab and check the "allow executing file as a program" box to give permission to install software...BUT when I do that, it says:
Sorry, could not change the permissions of "Setup.exe": Error setting permissions: Read-only file system

How can I overcome this problem?  Any suggestions would be awesome.

---

### Post by icebeat on 2010-08-02
[FONT=Arial][SIZE=5][SIZE=4]I know that by right  clicking the executable file and clicking properties, I can choose the  permissions tab and check the "allow executing file as a program" box to  give permission to install software...BUT when I do that, it says:
Sorry, could not change the permissions of "Setup.exe": Error setting  permissions: Read-only file system
      
    [/SIZE][SIZE=4]How can I overcome this problem?  Any  suggestions would be awesome.[/SIZE][/SIZE][/FONT]

---

### Post by Kakers on 2010-08-02
The CD will be read only, copy the file(s) to your machine/desktop and  try from there.

If you have to keep it in a disc like format you could copy the cd to an .iso on your machine, then mount that and try from there
[http://ubuntuforums.org/showthread.php?t=6509](http://ubuntuforums.org/showthread.php?t=6509)

---

### Post by Icarus315 on 2010-08-02
You cannot run Windows programs under Ubuntu 10.04 unless you use a program called WINE (WINE Is Not an Emulator).  Google "Ubuntu WINE Tutorial" to get started with that.  In the meantime there is a full library of Ubuntu software available.  Go to your Applications menu and choose "Ubuntu Software Centre."  Within that there are literally thousands of programs.  Install some and they will then appear under the various Applications sub-menus.

If WINE is too complex at first look, there is also a program called: Crossover which comes in [Games]("http://www.codeweavers.com/products/cxgames/") and [Applications]("http://www.codeweavers.com/products/cxlinux/") flavors.  Both are a paid app and games at least has a one week trial to test it.

---

### Post by NoBugs! on 2010-08-02
You should be able to run it without setting executable, using command line:
"sh nameoffile", or for .exe files, "wine nameoffile.exe"

---

### Post by Zimmer on 2010-08-02
Time for some reading..

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

[https://help.ubuntu.com/community/Applications](https://help.ubuntu.com/community/Applications)

---

### Post by lisati on 2010-08-02
Duplicate threads merged and moved to "Wine". (And please use the default font for the forum unless you are highlighting something)

---

