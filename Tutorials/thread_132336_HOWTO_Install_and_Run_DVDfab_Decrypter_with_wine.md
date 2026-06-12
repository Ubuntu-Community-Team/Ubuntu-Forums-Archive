---
title: "HOWTO: Install and Run DVDfab Decrypter with wine"
date: 2006-02-18
forum: Tutorials
---

### Post by Sabot on 2006-02-18
The first thing you need to do is get the current version of Wine from WineHQ installed on your machine.  [Here is a link to a guide on how to do this.]("http://ubuntuforums.org/showthread.php?t=56892&referrerid=41376")

Then you need to download DVDFab Decrypter. [Here is a link to download DVDFab Decrypter]("http://www.dvdidle.com/free.htm").

To install DVDFab Decrypter, place the downloaded file in your home directory.  Then open the Terminal and enter:
```
wine DVDFabDecrypter29.exe
```

If you download a different version of DVDFab Decrypter, just use that name instead of what I have listed above.

After DVDFab Decrypter has been installed, do not have it run at the end of the install process.  We need to install a dll and configure Wine first.

The dll you will need is mfc42.dll.  This has to come from an install of Windows XP.  To save you some time [here is a link to download this file]("http://www.opensimplesolution.com/dll.zip").  Place the zip file in your home directory.  Then Unzip and place it in .wine/drive_c/windows/system/.

```
unzip dll.zip -d ~/.wine/drive_c/windows/system/
```

To configure Wine, what you will need to do is open winecfg and make it use your freshly installed dll.  Click the Libraries tab, enter mfc42.dll in the New Override area, and click add.  Then press Apply.

```
winecfg
```

[IMG]http://www.opensimplesolution.com/winecfgdll.png[/IMG]

Now lets set up our DVD drive so it comes right up in DVDFab Decrypter. To do this we need to choose the Drives section in winecfg and choose Advanced.  Click the letter of the drive that is your DVD drive.  Then set it's type to CD-ROM.  Then click Apply and OK.  Now lets create an icon in the Applications menu to run DVDFab Decrypter.

[IMG]http://www.opensimplesolution.com/winecfgdrives.png[/IMG]

To create an icon in your Applications menu type in the following command and then cut and past the Desktop Entry info into this new text file and save it.
```
sudo gedit /usr/share/applications/dvdfabdecrypter.desktop
```
[Desktop Entry]
Name=DVDFab Decrypter
Exec=wine .wine/drive_c/Program\ Files/DVDFab\ Decrypter/DVDFabDecrypter.exe
Icon=gnome-dev-cdrom.png
Type=Application
Categories=Application;AudioVideo

Now you should be up and running.  Just select the icon in your Sound and Video section of Applications and start backing up your DVD's.

To shrink your DVD's you will want to look as [this guide on how to install DVDShrink in Wine]("http://www.mrbass.org/linux/ubuntu/dvdshrink/").  Make sure you don't use their copy of mfc42.dll. It does not work with DVDFab Decrypter.

***After further testing it looks like this is not the complete solution to geting DVDFab working.  It runs, but it does not convert disks correctly. If anyone has more to add please do!***

---

### Post by professor_chaos on 2006-02-19
Good job. Its up and running now, I hope it decrypts fine.

Thanks for posting this

---

### Post by Sabot on 2006-02-25
After running this on a few disks.  It looks like it will only back up disks that have no protection on them.  When ever I try to back up a protected disk I get an error when I try to read the files with DVD Shrink.  The error is "invalid data in video_ts.vob"  It looks like we may need one more dll to make this work.  I have not been able to track down the correct one.:(

---

### Post by tsb on 2006-03-31
I have used this tutorial to install DVDFab Platinum w/o any issues so far.

---

### Post by villain_s_deeds on 2009-02-28
It didn't work for me, though I followed your recipe.  I am new here, however.  I've decided to just put windows back on, but only install the few programs I still need.  I'd rather reboot my machine every time I switch to a different app than be frustrated by Wine.  Perhaps someday I'll be ready, but like I said I'm new here.

---

### Post by cwilhoit on 2009-11-16
It seems to work fine for me so far. I did the disk to disk and saved as an ISO. I viewed the ISO with VLC. I really appreciate the info! :p

---

### Post by daqron on 2010-05-06
Not bad. Four years later and this still works almost exactly as written.

The .desktop shortcut doesn't work, not just because the executable filename has changed. But that's not really a big deal. I just created a launcher in AWN using basically the same run command:
```
wine .wine/drive_c/Program\ Files/DVDFab\ 7/DVDFab.exe
```
Also the link to the DLL is dead, but it's easy enough to locate it on a windows machine.

Cheers!

---

### Post by Blackbird++ on 2010-10-09
I have a new problem using DVDFab 8.0.2.2:
The preferences menu is not working. I can expand or collapse the entries, but cannot click one and edit some preferences. :(
Any ideas?

---

### Post by mc4man on 2010-10-09
Really don't use but was curious - to navigate the settings (or ones available) you need to use a combo of left click with cursor in left side box and then arrow key for each setting.
So - left click, arrow, left click, arrow, left click. arrow, ect.ect. - I'm sure you'll get the idea after a bit (watch for focu
To go back up from a main category to one higher then close that category with the little arrow key

---

### Post by Blackbird++ on 2010-10-10
omg. :) Thank you very much!

---

### Post by Vege 4wd on 2010-10-25
All I did was download dvdfab 8, drag it to the programs folder in wine.(updated wine from ppa).
    Double clicked it and went through the install wizard and it started immediately and loaded the dvd I forgot was in my drive.:guitar:

---

### Post by dually on 2011-10-31
Hey, can I just use the mfc42.dll from windows 7?

---

### Post by DGINSD on 2012-12-17
I know this is an older thread, but has anyone got the newer Qt based versions of DVDfab to work in wine. The most current version I've got to work in DVDfab 8.0.0.2, everything after that is listed as DVDfabQtX.X.X.X. and tries to launch but fails.

---

### Post by N00b-un-2 on 2012-12-17
thanks for the info.  Just a thought though; why use DVDFab on WINE?  In my experience DVDFab has a lower success rate at ripping disks than MakeMKV or Handbrake (or DVDRIP or K9Copy or DVD9-5 or...)  While DVDFab does has some nice options for transcoding files, I've found that it is less capable than free software like FFMPEG/WinFF, Handbrake, VLC, etc...
It just seems like a lot of work to accomplish something that can be done easier, faster and with better results using free and natively supported software.

---

### Post by dually on 2012-12-17
I think it's pretty easy to use Makemkv and then Handbrake, for ripping dvd and bluray on Ubuntu.

---

### Post by cmaiyem on 2013-01-10
This is quite funny.  I am using basically the exact same tutorial in 2013, more than half a decade later, and it works just fine in Wine on Ubuntu 12.04-amd64 inside a VirtualBox VM running on Windows 7 64bit, ripping directly to a network share mounted as shared folder in the VM.  I copied the Windows 7 C:\windows\system32\mfc42.dll to ~/.wine/drive_c/windows/system32 as well as to ~/.wine/drive_c/windows/system (because some tutorial said system yet the original file was located in system32, so i wasn't sure which target folder). I'm doing this because I don't really trust the software to be free of malware/spyware, therefore the multilayer setup.. Well, it just works :D

---

