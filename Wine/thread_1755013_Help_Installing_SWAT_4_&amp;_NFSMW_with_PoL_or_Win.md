---
title: "Help Installing SWAT 4 &amp; NFSMW with PoL or Wine"
date: 2011-05-10
forum: Wine
---

### Post by TurtleKing on 2011-05-10
Swat 4 (couldn't even get the 1st one to install): Get to the part where it ask for the 2nd CD, but when I put the 2nd CD in the tray, the pop-up asking for "retry" or "cancel" will not go away (yes I clicked on "retry", "cancel", and "red x button") and thus prevent me from continuing the installation (man I was so close :P). This was using PlayonLinux (PoL), since wine doesn't exactly make it easier for me to install. The reason being, the autorun option located in the CD does not execute and will not let me change it's permission, so PoL is my half-working option here.

Need for Speed Most Wanted:
Same problem as SWAT. I have the 4 disc, however once I get the 1st one working, the 2nd one says it cannot mount since it is read-only, and PoL gets stuck waiting for it.

Any help please? I don't have much to offer, but a virtual chocolate chip cookie:
[http://maxflies.net/files/2011/03/lighter-chocolate-chip-cookies.jpg](http://maxflies.net/files/2011/03/lighter-chocolate-chip-cookies.jpg)

---

### Post by bobwyajnr on 2011-05-10
> **TurtleKing said:**
> Any help please? I don't have much to offer, but a virtual chocolate chip cookie:
[http://maxflies.net/files/2011/03/lighter-chocolate-chip-cookies.jpg](http://maxflies.net/files/2011/03/lighter-chocolate-chip-cookies.jpg)

Gnnnummm, nummmm, nnuuummmm. \\:D/

All the answers you seek (and more) are at:
[WINE HQ FAQ]("http://wiki.winehq.org/FAQ")

Bob

---

### Post by TurtleKing on 2011-05-11
No luck following their instructions. Inside the 1st CD there are 6 .exe files:
AutoRUn.exe, DIAG.EXE, eauninstall.exe, safemode_inst.exe, shell_inst.exe, and speed.exe.

Here are several of the trial and errors from terminal:
```
replaced@replaced:~$ wine start 'D:\Autorun.exe'
fixme:exec:SHELL_execute flags ignored: 0x00000100
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

replaced@replaced:~$ wine start 'Z: \Autorun.exe'
fixme:exec:SHELL_execute flags ignored: 0x00000100
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

replaced@replaced:~$ wine start /unix /media/cdrom/AutoRun.exe
fixme:exec:SHELL_execute flags ignored: 0x00000100

*Pop-up Message: Error: Path not found.*
replaced@replaced:~$ wine '/media/NFSMW_DISC1/AutoRun.exe'
*Pop-up Message: Unable to locate required file or required file is corrupted. Z:\home\replaced\AutoRun.DLL*
```

This is running NFSMW-CD. I rather not mess around with swat till I can get NFSMW working because SWAT requires 2 separate installations.

Any help, please?:(

---

### Post by bobwyajnr on 2011-05-11
Bear in mind that Wine inherits the UNIX and Windows concepts of a 'Working Directory' on the commandline. For example if you type:
```
pwd
```
The shell will tell you exactly where you are in the UNIX filesystem hierarchy (**pwd** = *Present Working Directory*).

You are plodding along on the right lines, you had just missed one vital step! The last answer you gave was right (well almost)! But look at the error message:

**[COLOR="Red"]*Pop-up Message: _Unable to locate required file_ or required file is corrupted. _Z:\home\replaced_\AutoRun.DLL*[/COLOR]**

So what does that tell you? Well you are *working* in your home directory (~ = **/home/replaced**). The Windows program **autorun.exe** tells WINE to look in it's present *working directory* (which as we have said - is your presently your Linux home directory) for any associated dynamic link library (.dll) and other executable files (.exe), etc. it may require. Oh dear! But the associated .dll file is in **/media/cdrom/**!!

Try amending the last try you made to run the software to:
```
cd /media/cdrom/
wine AutoRun.exe

```
Where **cd** is a system command for *Change Directory* (sorry you didn't say how familiar you are with the command line stuff!)

In general when launching CD/DVD -based Windows game/application installers you will want to be in the root folder of the CD/DVD. So:
```
cd /media/cdrom
```
then work relative to this folder to launch Windows applications/setup programs. e.g.:
```
wine ./autorun/autorun.exe
```
(a **dot .** folder : means your present working directory)
Where, in my example CD, the autorun executable is in a folder called *autorun*.

The Z: drive in WINE is simply a notional drive that points to the root of the UNIX filesystem (i.e. **/**). So it is not confined to your CD/DVD drive.

You can map in WINE virtual drive to your **/media/cdrom** folder by using the **winecfg** command/GUI. This should be in your WINE section of the main Ubuntu menus or accessible via the commandline. Typically I think WINE maps in your optical drive(s) starting at **D:** (WINE virtual Windows drives).

You can access WINE virtual drives by typing:
```
wine explorer
```
which provides a very rough & ready implementation of Windows explorer (i.e. the filesystem shell GUI - not IE)! I usually prefer to use the Linux (BASH) command line to run Windows applications (or make menu shortcuts). For debugging purposes you have to use the command line!

Report back here on the next set of errors! :guitar:

Bob

---

### Post by TurtleKing on 2011-05-11
I can't get passed a pop for the 2nd CD:
"Please insert CD/DVD 2 in drive Z:"
I am not sure what it is asking me by reading that message. I already put the 2nd CD on the tray, and clicked on the ok button several times. I am reading through google-fu currently since I got several interesting results. However, I would prefer your solution since you know where I am starting from.

---

### Post by TurtleKing on 2011-05-11
It seems to be that the computer cannot mount the 2nd CD. I previously got an error when I tried with PoL stating that the CD was read only, therefore it couldn't exec it or something. Any suggestions?

---

### Post by bobwyajnr on 2011-05-11
> **TurtleKing said:**
> I can't get passed a pop for the 2nd CD:
"Please insert CD/DVD 2 in drive Z:"
I am not sure what it is asking me by reading that message. I already put the 2nd CD on the tray, and clicked on the ok button several times. I am reading through google-fu currently since I got several interesting results. However, I would prefer your solution since you know where I am starting from.

Hi **TurtleKing**

The reason why you cannot eject drive **Z:** is because it is a link pointing at your system root (UNIX) folder (**/**) - *it is not a WINE virtual DVD/CD drive*. I stupidly suggested a way of installing software that only works for a single CD/DVD application installer!! *Duh*!! Thankfully there is more than one way to skin a cat :popcorn:

Right heres the simple guide to doing a multiple CD/DVD install in WINE:
[LIST=1]
[*] Command line (launch winecfg GUI as background process):
```
winecfg &
```
Make sure your optical drive shows up in the **drives** tab - note the location (e.g.  typically will be **D:**)

[*] Put in CD1 (and mount)

[*] Command line (browse to WINE mounted CD drive folder - correct **d:** drive if necessary):
```
cd ~/.wine/dosdevices/d:/
ls
```

[*] Locate your setup/autorun .exe file in the root CD folder listing and run it:
```
wine setup.exe
```
(replace setup.exe with the actual executable name - note all this is case sensitive in usual UNIX style...)

[*] When WINE has finished installed CD1 and asking for CD2. Try physically ejecting CD1 and popping in CD2. Does the CD2 installer continue?

[*] [COLOR="Red"]If and only if the CD2 installer doesn't start automatically:[/COLOR] (and it damn well should - that WINE bug was fixed ages ago :cool:). Eject CD2 then force-ably unmount the D: drive in WINE by typing:
```
wine eject d:
```

[*] Rinse and repeat steps (5)-(6) for the other installer CDs...

[/LIST]

Sorry 'bout the earlier inaccurate advice. I haven't installed any multiple CD installers in WINE for 2-3 years now! Hey just one of the benefits of using the Valve **Steam** app.

Sadly, for the ordinary user, the use of WINE still requires a lot of command line savvy. It's worth getting yourself an old copy of the book "Linux in a Nutshell" (or similar) - worth it's weight in gold :P

Bob

---

### Post by TurtleKing on 2011-05-11
Still stuck on the 2nd CD pop-up like if it couldn't read it. I tried:
```
replaced@replaced:~/.wine/dosdevices/d:/media/NFSMW_DISC1$ wine AutoRun.exe
simba@GLADOS:~/.wine/dosdevices/d:/media/NFSMW_DISC1$ fixme:win:EnumDisplayDevicesW ((null),0,0x33ac38,0x00000000), stub!
*repeats*
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x807, disabling mixer
err:avicap:query_video_device Video 4 Linux support not enabled
*repeats several times*
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:mscoree:GetCORVersion (0x33c1f4, 600, 0x33c1e4): semi-stub!
fixme:mscoree:LoadLibraryShim (0xc620c4 L"fusion.dll", (nil), (nil), 0x33ba24): semi-stub
err:setupapi:do_file_copyW Unsupported style(s) 0x144
*repeats several times*
fixme:mscoree:LoadLibraryShim (0xc620c4 L"fusion.dll", (nil), (nil), 0x33bd38): semi-stub
replaced@replaced:~/.wine/dosdevices/d:/media/NFSMW_DISC1$ wine AutoRun.exe
replaced@replaced:~/.wine/dosdevices/d:/media/NFSMW_DISC1$ err:menubuilder:Process_Link unable to load L"C:\\users\\Public\\Start Menu\\Programs\\StartUp\\EA_RESTART_001.lnk"
err:menubuilder:wWinMain failed to build menu item for L"C:\\users\\Public\\Start Menu\\Programs\\StartUp\\EA_RESTART_001.lnk"
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x807, disabling mixer
**replaced@replaced:~/.wine/dosdevices/d:/media/NFSMW_DISC1$ wine eject d:**
Warning: could not find DOS drive for current working directory '(unreachable)/', starting in the Windows directory.
Drive d: is not a CD or is not mounted
replaced@replaced:~/.wine/dosdevices/d:/media/NFSMW_DISC1$ cd
replaced@replaced:~$ wine eject d:
Drive d: is not a CD or is not mounted
replaced@replaced:~$ 
```
The bolded part is the point where I am stuck on the 2nd CD and look for a solution. Let me know if it makes it easier for you, if I give you the username@computer part (I was told by an online friend not to give that info away). In addition, would it be helpful to tell you what the winecfg list as drivers?

---

### Post by bobwyajnr on 2011-05-11
> **TurtleKing said:**
> Still stuck on the 2nd CD pop-up like if it couldn't read it.


OK. Sorry slight inaccuracy. I tried:
```
wine eject d:
```
on my system and it physically ejects the DVD driver drawer!

Make sure CD2 is mounted (in Ubuntu/UNIX) - e.g. double click on the CD drive if it isn't auto-mounted (showing up on your desktop), etc. - before you allow the Windows game installer to continue.

Are you sure you are mounting CD2? You can check by typing:
```
cd ~/.wine/dosdevices/d:/
ls
```
You will get an error message if the CD/DVD drive is not mounted! (Since a direct link to the drive device is used by WINE.)
[COLOR="Red"]ls: reading directory .: Input/output error[/COLOR]
- that is bad :eek:


I gathered that replaced@replaced was replaced - don't worry about that... Sounds like a reasonable security measure!

Bob

---

### Post by TurtleKing on 2011-05-11
There seems to be a problem with wine not letting the 2-CD mount. Outside of the installer (without it) it will recognize NFSMW_DISC2 in  filesystem/media/. But when I try to get it to mount while wine is running after 1-CD install it will not mount.
```
replaced@replaced:~/.wine/dosdevices/d:$ cd media
replaced@replaced:~/.wine/dosdevices/d:/media$ ls
floppy  floppy0
replaced@replaced:~/.wine/dosdevices/d:/media$
```
After closing the installer:
```
replaced@replaced:~/.wine/dosdevices/d:/media$ ls
floppy  floppy0  NFSMW_DISC2
replaced@replaced:~/.wine/dosdevices/d:/media$ 
```

---

### Post by TurtleKing on 2011-05-12
Well, I tried several recommendations but can't still manage to get passed this 2-CD pop-up. Can anybody help me with this, please?

---

### Post by TurtleKing on 2011-05-13
bump

---

### Post by TurtleKing on 2011-05-14
Hey bob if your still around. Is it possible to install the games in my other win7 hard drive and use wine to move it over to this Ubuntu hard drive? 

I tried copy and paste with SWAT 4 but the game wouldn't run with wine.

---

### Post by TurtleKing on 2011-05-14
Also, read about a different method of coping the files in the other CD into folder on desktop, and just getting wine to looking for the files in those folders. However, I am not sure how to use the terminal or winecfg to achieve this, any help?

---

### Post by bobwyajnr on 2011-05-14
> **TurtleKing said:**
> Also, read about a different method of coping the files in the other CD into folder on desktop, and just getting wine to looking for the files in those folders. However, I am not sure how to use the terminal or winecfg to achieve this, any help?

Hi

I'd don't like to keep sending someone else on a wild goose chase... So I've tried installing the game myself - using my own copy.
I'm seeing the installer crash out - on both the WINE 1.2.xx and 1.3.xx series. But I'll keep trying other stuff at this end!

I would recommend trying the folder method - for sure - for SWAT4. I just can't 100% vouch for it since I haven't tried it myself yet. It was reported to work on the AppDB page and it would be something I would try myself. Make sure you have 1.2Gb or so (additional) HD space in your /home partition.

Just create a folder in you home page:
```
mkdir ~/SWAT4
```

Then put in CD1, mount this and type:
```
cp -Rv /media/SWAT_1/ ~/SWAT4
```

Then put in CD2, mount this and type:
```
cp -Rv /media/SWAT_2/ ~/SWAT4
```

Obviously change the **/media/xxxxx/** path as appropriate for the 2 CDs (TAB completion is your friend here!) You are going to run into problems if the installer doesn't play friendly with a DVD (single disc) format of course! Caveat emptor, etc.!

Launching the SWAT installer is a case of:
```
wine ~/SWAT4/Autorun.exe
```
(again replace the executable name as appropriate - TAB completion is your friend)


Often I find it's to do with running applications on a non-native FS partition or mount (e.g. not a native Linux filesystem) like a NTFS partition or a UDF CD-ROM. Strange as it seems to happen even if I have the filesystem (e.g. NTFS) mounted with my user as the owner (and a recent NTFS-3G build from source)...

One of the problems with WINE is that older games can break. People won't even notice because the 'mass market' for WINE is Source-based games from Valve/Steam and the likes of Adobe Photoshop... I'd love to get into development work in WINE but heck the source takes longer to compile than the Linux kernel! :popcorn:

Good luck
Bob

---

### Post by TurtleKing on 2011-05-14
I tried the folder option, and I am now writing a how-to since the folder option is not very specific. :)
Thanks for the reply, and I just was kind of weirded out that you didn't respond even to let me know you were stumped on what to do next.

---

### Post by bobwyajnr on 2011-05-14
> **TurtleKing said:**
> I tried the folder option, and I am now writing a how-to since the folder option is not very specific. :)
Thanks for the reply, and I just was kind of weirded out that you didn't respond even to let me know you were stumped on what to do next.

Hey no problem! ):P

Uhhmmm before you get to carried away writing an install guide... :popcorn:
Still doesn't address the problem that you can't turn more than a 360 degree rotation, in one direction, using the mouse (did you notice that)!! Ahhh the on-going mouse warp problem! Needs a patch to WINE to fix (no easy mousewarp overrides for this sucker).

We are being promised a mainline addition of a fix to this problem (which only seems to affect 110% of all Windows games being run on WINE) - yet again - in the released 1.3.20 version of WINE (not yet in the Ubuntu WINE PPA). Could compile it from source I suppose... :D

Bob

---

### Post by TurtleKing on 2011-05-14
Well I specified in the how-to that my goal is to get them over the 2CD, 3CD, etc pop-up. Whether the program works or not is up to WINE really. Installing it a 2nd time to make sure I am giving correct instructions.
[http://ubuntuforums.org/showthread.php?t=1758390](http://ubuntuforums.org/showthread.php?t=1758390)

---

### Post by TurtleKing on 2011-05-14
I will keep this thread unsolved in the event they make a super 99% working solution for the future.

---

### Post by bobwyajnr on 2011-05-14
> **TurtleKing said:**
> I will keep this thread unsolved in the event they make a super 99% working solution for the future.

Hi

Uhmmm sadly WINE 1.3.20 won't even compile (yet)... Oh well - might to wait for a fix. I'll report back if the mouse problem is really fixed...

+1 for a native Linux Steam client. Every few months we get an update, that breaks WINE compatibility and we have to wait for a fix for it! :mad:

Bob

---

### Post by TurtleKing on 2011-05-14
Did you check out the thread over at steam forums for Native Steam Client for Linux? Not sure if it is cool with Ubuntu Forums, but it would be great if they could sponsor it with a sticky or not not give us a hassle if we have in our signature (not saying they do, but the rules do say no advertising).

---

### Post by bobwyajnr on 2011-05-14
> **TurtleKing said:**
> Did you check out the thread over at steam forums for Native Steam Client for Linux? Not sure if it is cool with Ubuntu Forums, but it would be great if they could sponsor it with a sticky or not not give us a hassle if we have in our signature (not saying they do, but the rules do say no advertising).

I am not registered on the Steam forums (but do have a whole lotta of Steam games). I'll have a read of that thread - thanks! :popcorn:

I read with interest about the speculation by Michael on [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=ODIwNQ"). Of course even if Valve released a client it would be on their own time - i.e. very slow (HL2.0 ep3, cough, cough :) )

Bob

---

### Post by bobwyajnr on 2011-05-14
Hi **TurtleKing**

Good news! After a lot of cursing and swearing at the Git (I mean the WINE Git tree :o:) ) I got WINE 1.3.20 to compile successfully (cough, cough I think Git was still running my earlier bisection operation). Anyway great news your SWAT 4 game will run with a full axis of mouse rotation (no 360 degree lock anymore).

Pickup the PPA here:
[Ubuntu WINE Team PPA]("ppa:ubuntu-wine/ppa")

The turn-around time for the 'team' is very\\:D/ quick - so 1.3.20 should be out in a day or two. Lucky timing to be trying to install SWAT 4. I think some people have been waiting about 5 years (literally) for this fix! :popcorn:

So I would say you can mark the thread as solved (OK the CD problem is a pain in proverbials...) Game runs at maximum settings, you can turn around, what more do you want?:D

Bob

---

### Post by TurtleKing on 2011-05-14
> **bobwyajnr said:**
> Hi **TurtleKing**

Good news! After a lot of cursing and swearing at the Git (I mean the WINE Git tree :o:) ) I got WINE 1.3.20 to compile successfully (cough, cough I think Git was still running my earlier bisection operation). Anyway great news your SWAT 4 game will run with a full axis of mouse rotation (no 360 degree lock anymore).

Pickup the PPA here:
[Ubuntu WINE Team PPA]("ppa:ubuntu-wine/ppa")

The turn-around time for the 'team' is very\\:D/ quick - so 1.3.20 should be out in a day or two. Lucky timing to be trying to install SWAT 4. I think some people have been waiting about 5 years (literally) for this fix! :popcorn:

So I would say you can mark the thread as solved (OK the CD problem is a pain in proverbials...) Game runs at maximum settings, you can turn around, what more do you want?:D

Bob
Folder method does not work for SWAT 4 because unlike NFSMW, SWAT 4 crashes upon the 2CD pop-up. In NFSMW install wizard, it would let you cancel the installation. In addition, NFSMW would work even if you closed the terminal, SWAT 4 on the other hand crashes the terminal (no new commands work) and if you close the terminal the SWAT 4 Install Wizard closes. I think I have the newest version of wine, but I will double-check just to be sure. Did you install the game? Until I can install it , no solved cookie.:(

By the way, PPA link is broken.

---

### Post by bobwyajnr on 2011-05-15
> **TurtleKing said:**
> Folder method does not work for SWAT 4 because unlike NFSMW, SWAT 4 crashes upon the 2CD pop-up. In NFSMW install wizard, it would let you cancel the installation. In addition, NFSMW would work even if you closed the terminal, SWAT 4 on the other hand crashes the terminal (no new commands work) and if you close the terminal the SWAT 4 Install Wizard closes. I think I have the newest version of wine, but I will double-check just to be sure. Did you install the game? Until I can install it , no solved cookie.:(

By the way, PPA link is broken.

Are you following/ reading my previous instructions???  :confused:

I put all the files/folders from both CDs into a _SINGLE_ harddisk folder (somewhere in your /home directory is a good place) _THEN_ I launched the SWAT 4 installer. So effectively you are making an installer that could be burnt directly to a single DVD... You should not see any popup's about additional CDs (since all the install files are already in a common harddisk folder accessible to the installer)...

Worked like a charm for me :) NB If you get complaints about overwriting write-protected files, etc. when copying the CD2 files/folders over into the same folder... Don't worry just say no to each of these copy operations. (Basically you want the common Autorun.exe, etc. files from CD1 not CD2.)

Ahhh, you wanted the HTTP link to the Wine PPA webpage on Launchpad not the direct PPA reference (how old fashioned of you, cough, cough :popcorn: ):
[HTTP link to WINE PPA!!]("https://launchpad.net/~ubuntu-wine/+archive/ppa")

You can't have the newest 1.3.20 version of WINE (unless you downloaded the source and compiled - without even realizing it :P). I don't know if they're back-porting that mouse fix patch to the next iteration of the 1.2.xx 'stable' branch of WINE... You can check you installed WINE version with:
```
wine --version
```

Like I said I have the game installed (on my desktop) and working fully with WINE 1.3.20. I've already submitted an update to the WINE AppDB page to alert people who are waiting for the mouse fix to be mainlined in WINE (since 2006 in fact!!)

All the best
Bob

---

### Post by TurtleKing on 2011-05-15
> **bobwyajnr said:**
> Are you following/ reading my previous instructions???  :confused:

I put all the files/folders from both CDs into a _SINGLE_ harddisk folder (somewhere in your /home directory is a good place) _THEN_ I launched the SWAT 4 installer. So effectively you are making an installer that could be burnt directly to a single DVD... You should not see any popup's about additional CDs (since all the install files are already in a common harddisk folder accessible to the installer)...

Worked like a charm for me :) NB If you get complaints about overwriting write-protected files, etc. when copying the CD2 files/folders over into the same folder... Don't worry just say no to each of these copy operations. (Basically you want the common Autorun.exe, etc. files from CD1 not CD2.)

Ahhh, you wanted the HTTP link to the Wine PPA webpage on Launchpad not the direct PPA reference (how old fashioned of you, cough, cough :popcorn: ):
[HTTP link to WINE PPA!!]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

You can't have the newest 1.3.20 version of WINE (unless you downloaded the source and compiled - without even realizing it :P). I don't know if they're back-porting that mouse fix patch to the next iteration of the 1.2.xx 'stable' branch of WINE... You can check you installed WINE version with:
```
wine --version
```Like I said I have the game installed (on my desktop) and working fully with WINE 1.3.20. I've already submitted an update to the WINE AppDB page to alert people who are waiting for the mouse fix to be mainlined in WINE (since 2006 in fact!!)

All the best
Bob
I am still not to savvy on using the ppa thing, so I didn't know what I was suppose to do with the first one. Usually when I come across a ppa link, all I am suppose to do is copy it into terminal or add it to the software sources area. So I assumed for the first post about it, you wanted me to visit a link (reason why I mentioned it was broken). I will try the SWAT 4 Install using your method, hopefully, it will finally surrender to Linux.:P I will post back to let you know the outcome.

---

### Post by TurtleKing on 2011-05-15
Hmm I have feeling this will not go well. How did you get past the part where it ask if you want to replaced the 2CD's autorun.exe with the 1CD? I just let the 1CD be the one that stays, but it might need it in order to recognize 2CD.:confused:

---

### Post by bobwyajnr on 2011-05-15
> **TurtleKing said:**
> Hmm I have feeling this will not go well. How did you get past the part where it ask if you want to replaced the 2CD's autorun.exe with the 1CD? I just let the 1CD be the one that stays, but it might need it in order to recognize 2CD.:confused:

Hi

Sorry, thought I'd made that clear about moving the files into a single unified folder. **cp** (the Linux shell file/folder copy command) will complain that it is overwriting files (when copying CD2). You should be able to say **no** there - so that you keep the common files from CD1. (To be honest it usually doesn't matter - typically the Autorun.exe is the same file on each CD)... Things get more ugly when you get sophisticated DVD copy protection, etc.!!

I would get yourself on the fast track to familiarity with **WINEPREFIX**'s. These allow you to have separate 'Virtual' Windows installations (similar in structure to the default one at ~/.wine). So you can isolate different applications and game installs, from each other, in completely separate file structures. Sounds more complicated than it is in practice! Once I got familiar with the concept - I was sold!

For example I have put my SWAT 4 game install in a completely separate prefix from my other WINE installed Windows applications. It will have it's own (separate) copy of the Windows file-system, registry, etc. and it's own independent **wineserver** process, etc (if WINE installed Windows application goes south they don't all go south!!).

[Do make time to download and read through the clear(ish) WINE PDF user help documentation.]("http://www.winehq.org/documentation") Your WINE user experience will be an exercise in frustration till you get quite savvy with how to use it.

I would also advise getting a cheap(!!), second copy of "Linux in a Nutshell" (O'Reilly). It's brilliant as an introduction/quick reference for command line applications. OK you can read the GNU/Linux man pages - but it helps to back them up with another reference. Also you will know that when someone tells you to enter:
```
sudo rm -Rf /*
```
it's bad - **really bad**! :!: :!: :!: [COLOR="Red"](BTW don't try it!!)[/COLOR] :!: :!: :!:

I would also suggest installing [q4wine]("http://q4wine.brezblock.org.ua/documentation/en_gb/05-first-steps.html") (if you aren't a KDE/Qt hater :-) ). This application is in the repositories and is brilliant for killing off a hung WINE application (OK there are probably better uses for it...) It shows all the processes, associated with each WINE prefix, that are currently running on your system.

Don't worry about not being tech savvy (yet). I did a Computer Science degree so I am not the typical Ubuntu (L-Mint KDE) user!

Bob

---

### Post by TurtleKing on 2011-05-15
SWAT 4 Installed. Now if I can get my control the world through your computer application working.:P Anyways, how does NFSMW run on your pc? On my it runs like a window which is annoying since the docky at the bottom of the desktop and the panel show up. I have put the docky on hide under windows as with panel, but then their s a space reserved at the top. I will mark this thread solved, although I wish it installed 100% well (no folder creation to bypass install).

---

### Post by bobwyajnr on 2011-05-15
> **TurtleKing said:**
> SWAT 4 Installed. Now if I can get my control the world through your computer application working.:P Anyways, how does NFSMW run on your pc? On my it runs like a window which is annoying since the docky at the bottom of the desktop and the panel show up. I have put the docky on hide under windows as with panel, but then their s a space reserved at the top. I will mark this thread solved, although I wish it installed 100% well (no folder creation to bypass install).

I wouldn't worry about the installer issues... That's a one off thing after all. 

Never accept second best for when you actually running a game (well try and avoid it anyway)! Are you really running the game in a decorated 'Window' or is it trying to run full screen with your dock trying get in front or pushing the game window up?

In the latter case it could be your Compiz effects aren't playing ball with Windows (WINE) games that need access to the OpenGL stack. Get hold of the **fusion-icon** (in Synaptic) - if you don't have it installed already. Fire it up. It will sit in your system tray. Right click on it and select Metacity as your window manager. Your dock will go all ugly (if you don't have compositing - transparency - enabled in Metacity) - fixing that is easy enough though.

Anyway using Metacity you should be able to get SWAT 4 (or any other Windows game) to run fullscreen without adding to the problems it has! In theory this is the case ](*,)](*,) - I've found however that the Steam client doesn't play ball with Metacity and you can get a lot of graphical/GTK corruption (e.g. windows leaving trails behind them when moved, etc.)

I should point out that KVM (the KDE window manager) has a nice option/feature to disable desktop effects for fullscreen applications. So I didn't have to do anything with compositing/windows effects settings to run SWAT 4 :P. I'm a bit of convert (especially since it has a hack to allow previews of minimised windows - Compiz is supposed to support it eventually...)

Good luck!
Bob

---

### Post by bobwyajnr on 2011-05-16
Hi

[COLOR="Red"]I'd advise everyone who reads this thread not to install WINE 1.3.20 (if it gets added to the Ubuntu PPA repository at all) - it's causing a _lot_ of serious game regressions...[/COLOR]

I'll be reverting back to 1.3.19 myself...

Bob

---

### Post by TurtleKing on 2011-05-17
> **bobwyajnr said:**
> I wouldn't worry about the installer issues... That's a one off thing after all. 

Never accept second best for when you actually running a game (well try and avoid it anyway)! Are you really running the game in a decorated 'Window' or is it trying to run full screen with your dock trying get in front or pushing the game window up?

In the latter case it could be your Compiz effects aren't playing ball with Windows (WINE) games that need access to the OpenGL stack. Get hold of the **fusion-icon** (in Synaptic) - if you don't have it installed already. Fire it up. It will sit in your system tray. Right click on it and select Metacity as your window manager. Your dock will go all ugly (if you don't have compositing - transparency - enabled in Metacity) - fixing that is easy enough though.

Anyway using Metacity you should be able to get SWAT 4 (or any other Windows game) to run fullscreen without adding to the problems it has! In theory this is the case ](*,)](*,) - I've found however that the Steam client doesn't play ball with Metacity and you can get a lot of graphical/GTK corruption (e.g. windows leaving trails behind them when moved, etc.)

I should point out that KVM (the KDE window manager) has a nice option/feature to disable desktop effects for fullscreen applications. So I didn't have to do anything with compositing/windows effects settings to run SWAT 4 :P. I'm a bit of convert (especially since it has a hack to allow previews of minimised windows - Compiz is supposed to support it eventually...)

Good luck!
Bob
SWAT 4 does not work (it seems to crash after hitting play) and in the terminal it gives the following output:
```
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d4800

```
NFSMW runs in full-screen thanks to that recommendation about running metacity, however, the intro plays but none of the mouse button respond (or keyboard if you could use that to skip the intro). I have to use my shortcut key to close it, and then reset the resolution back to normal. Funny thing is I was like :D and then I was like :(.

---

### Post by TurtleKing on 2011-05-18
Starting a new thread to try and find a solution for having the 2 games works okay.
[http://ubuntuforums.org/showthread.php?p=10832045#post10832045](http://ubuntuforums.org/showthread.php?p=10832045#post10832045)

---

