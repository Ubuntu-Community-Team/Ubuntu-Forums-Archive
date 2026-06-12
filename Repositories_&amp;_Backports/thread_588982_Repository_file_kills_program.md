---
title: "Repository file kills program? ?  ?"
date: 2007-10-23
forum: Repositories &amp; Backports
---

### Post by Richard Carlson on 2007-10-23
I've got a program called 'Sky Charts' installed on the newest version of Ubuntu 7.10. Sky charts has worked on several Linux distro's that I've used and I believe this one also, at least an earlier version).   The program consists of basically 2 *.deb files and some additional catalog files.  The program installed flawlessly without any program fault messages or errors.   The problem I have is that it won't start. I either click on the program 'icon' or use the command line to get things rolling and nothing happens. I've reinstalled the program several times an have had the very same results. It won't start up.   I believe one of the Ubuntu repository files (i.e. Library files. . .maybe the culprit). These files are all remastered replicates of the debian ones except for some slight  variation I'm sure. Problem is I don't know which one.    The program can be found at :    [http://www.ap-i.net/skychart/index.php](http://www.ap-i.net/skychart/index.php)  I have the latest verion 3.1.2-1 installed.   It is an excellent program and by far surpasses Kstars, Celestia, and stellarium as an Astronomy software package (especially if you've got the additional catalog files and 20,000 photo's installed. which don't take long whatsoever to do.   If anyone is familiar with the Ubuntu/Debian file respository system or else think they know what the culprit is please let me know. Any help would be appreciated. Thanks   Rich

---

### Post by cpmdays on 2007-10-25
I installed Skychart from the repository on Oct. 19th and it worked well at that time but I had not used it since then. Today I reinstalled Gutsy (because it couldn't find my camera - BTW the reinstall did not help) so I had to reinstall Skychart. Skychart will not open now. I have tried older Skychart versions and even an .exe file with wine, none of which work. Maybe a Gutsy update in the past few days has messed it up? I wish I knew because Skychart is a great program.

---

### Post by TaTaE on 2007-10-28
run skychart in terminal and copy-paste the output here pls, so anyone can see the errors.

---

### Post by Richard Carlson on 2007-10-28
My initial installation into Gutsy 7.10 did no work at all period. The program installed properly via the debian installer  that installed the package. (The software package was *.deb files totally.) They were no Terminal or Konsole error messages after I tried to start it from terminal. The desktop icon when it was installed didn't do a thing when it was clicked on by the mouse. So I can't say what if any errors occurred or which while in the repositories have messed up the program. I did a reinstall and removal a couple times with the same results. This was with the latest version of the program which has always worked for me in a couple other Linux Distros. . . .    Rich

---

### Post by cpmdays on 2007-10-28
Terminal Run:
joe@joe: ~$ skychart
joe@joe: ~$

System monitor shows skychart sleeping for a few seconds and then disappearing off of the process list.

My experiments are as follows  ( note: same skychart version, 3. beta, used for all experiments - deb [http://kent.dl.sourceforge.net/sourceforge/](http://kent.dl.sourceforge.net/sourceforge/) skychart/ )

Booted Dapper live cd and installed skychart via synaptic manager. It worked fine with the live cd. 

Booted Gutsy with live cd but could not install skychart because "unable to download libgdk-pixbuf2 and libgtk1.2". Also, the skychart I had successfully installed (via my normal Gutsy operating system - not the live cd) would not run with the Gutsy live cd.

Booted Dapper live cd. Installed skychart as above. And, still using the Dapper live cd, I ran my Gutsy skychart bin file (copied to a flash drive first) and it also ran fine. BTW the Dapper skychart bin file does not run under Gutsy.

Other info:

The download of skychart also includes libgdk-pixbuf2, libglib1.2, libgtk1.2, libgtk1.2-common. Dependencies of skychart (via dpkg --info) are listed as libc6, libgcc1, libgtk1.2, libgdk-pixbuf2, libX11-6 | xlibs.

That's all I have for now. Tried copying files from Dapper to Gutsy but messed up and had to do a terminal recovery session to fix it. Will work on this when I can. Till then I am using KStars.

Thanks for any and all help!

---

### Post by cpmdays on 2007-10-28
Oh, I forgot to mention that I did get the Gutsy live cd to install starchart but I had to check more repositories (which I did not have to do in the Dapper live cd). The Gutsy live cd installation of skychart failed to run just as the normal skychart install failed to run.

---

### Post by cpmdays on 2007-10-29
I just found out that my Open Office under Gutsy crashes and so I am leaving Gutsy for the old reliable Dapper. Hopefully someone else can figure out why skychart crashes with Gutsy. Good Luck!

---

### Post by navneeth on 2007-11-03
So I'm not the only person with these problems!

Skychart aka Cartes du Ciel (quite simply the best free planetrium program)  won't start. I had it installed in Feisty, but in Gutsy, it wouldn't start. I have had no replies to my message the Sky Chart Yahoo group. 

Stellarium wouldn't start, either. When I type stellarium in the terminal, I get this error message.
```
stellarium: error while loading shared libraries: libQtOpenGL.so.4: cannot open shared object file: No such file or directory

```

I simply have no idea what to do. 

And OO.o...well, that doesn't work either. I've managed to open the Word Processor and Spreadsheet programs, but Presentation will not open.

---

### Post by Richard Carlson on 2007-11-04
Well, I hope someone figures this out. Sky Charts i.e. 
Cartes dul Ciel is an excellent program. Probably the best Linux astronomy software program out there. For now I've dumped Ubuntu and am back to using PCLinuxOS which runs very well with my equipment and I've got all of the latest software including i.e (Sky Charts, Stellarium 9.0, Celestia 1.4.1, latest Googleearth and Picasa running. )It has so far been very satisfactory. Until someone else gets the upper hand I think I'll be staying with them for a while. I've used about 12 different distro's and am continually looking around to see who has and is using the cutting edge software available. Good luck to all of you with Ubuntu. (Ubuntu is an excellent OS by all means. . . ) I hope they can continue to show improvement and progress . The Gnome desktop is quite pleasing to use and view. 

Rich

---

### Post by cpmdays on 2007-11-05
I switched to Dapper on my work computer but still have Gutsy on my laptop so I decided to play with skychart a little more. I booted in recovery mode and ran skychart in the terminal. Skychart did not run but the terminal gave me a message: AppArmor could not find something needed for skychart (sorry I do not remember what that something was). So..... I rebooted in normal mode. Completely removed AppArmor via synaptic manager then.... skychart worked !
I don't know why AppArmor kept skychart from working but removing it  
was a workaround for me.

---

