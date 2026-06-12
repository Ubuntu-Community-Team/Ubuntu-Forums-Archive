---
title: "problem updating a program installed in WINE"
date: 2010-05-31
forum: Wine
---

### Post by 3pinner on 2010-05-31
I have the latest version running on ubuntu 10.04.
I just installed a Windows based mapping program in WINE,  (National Geographic TOPO! 4.0) downloaded an update for that program onto my Ubuntu desktop.
I marked the .exe program as executable, then tried to open it with WINE. It sends back an error message that it cannot find the installed version of TOPO 4.0 that I just installed.
Any tricks to helping an .exe file  to find the program it is supposed to update?"

Thanks!
Solving this will completely break any connection I still might have with Windows. I keep it around just to generate topo maps for some of my insane back country bp and ski trips :)

---

### Post by cogadh on 2010-05-31
Try putting the update EXE into Wine's fake C: drive, open a terminal, change directories to where the update EXE is, then run it using the terminal commands. If it works, great, if it doesn't, the terminal will have Wine's error output, which might explain what is happening.

---

### Post by 3pinner on 2010-06-01
Thank you for the reply, but it did not work.
I moved it into the fake C drive, used both the GUI and terminal to try and run the program, and kept getting the following error message:

Failed to update because of the following errors:

Update failed because an existing installation of TOPO! version 4 could not be located. Please install this application from a version 4 TOPO! Installer CD-ROM before attempting this update.

So the installer will run, and try to find the install of TOPO 4.0 and can't find it. I tried moving the updater into the Programs folder, then into the TOPO folder then into various folders inside that with no success.
It would be nice if the installer would allow you to type in the path to the program. 
I even tried opening the TOPO 4.0 program to see if the updater would find it but nothing.
Any other suggestions??
Thanks!

---

### Post by dearingj on 2010-06-01
Are you trying to update to version 4.5? According to [this]("http://support.topo.com/articles/8") page, you need to download and install the 4.2.8 update before the 4.5 update will work.

---

### Post by roubman on 2010-06-01
I wouldn't use wine if i were you...
it isn't really made for the programs needed in windows, i tried it too and it didn't do so well...
I suggest you try something else OR...
Dual boot your computer...
(means have one partition windows ... other linux
:) ;-)

---

### Post by cogadh on 2010-06-01
Um, what are you talking about? The *only* thing Wine is made for is running Windows programs and while you may not have had much success with it, the rest of us have. That doesn't mean 3pinner will have the same kind of success, but to just give up on it without even trying is plain wrong.

---

### Post by 3pinner on 2010-06-02
Actually I have had good success running Windows apps with WINE, but it is a progressive thing. 
TOPO would not work at all in WINE a couple of years ago, but the latest version that came with Lucid Lynx runs it well. I just don't assume that it will run all Windows programs, but so far its been great after a bit of tweaking for the software I really need.
I did run dual boot for some time - with Windows 2000, but in the last year I cannot remember when I actually used Win2K except for TOPO. So this will move me over to Ubuntu 100%.

dearingj - Thank you for that, I missed it, and will download and try it first. I will report back about how it worked.

Thanks for the comments and help.

---

### Post by 3pinner on 2010-06-02
Thank you dearingj!
That was the solution.
I downloaded the .exe file, copied it to the fake C drive 
(/home/myusername/.wine/drive_c) opened the file properties, checked the box to make it executable, right clicked the .exe file and opened with WINE. It took a while at first, I thought the installer had crashed - and that is one of the things I have learned about using WINE, sometimes it takes a while but it will eventually figure it out and run.
The first update finally installed, the other update installed in a couple of seconds.
So now I can start planning a couple of trips in West Virginia that I've had my eye on.
And no Windows! :guitar:

---

