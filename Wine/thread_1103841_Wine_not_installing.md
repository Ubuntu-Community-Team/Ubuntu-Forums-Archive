---
title: "Wine not installing"
date: 2009-03-23
forum: Wine
---

### Post by Tony_photoplus on 2009-03-23
I am trying to load a few softwares onto Wine and I keep getting the same problem. 

[SIZE="2"]An error occurred while loading the archive.[/SIZE]
[/media/cdrom0/Autoplay.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Autoplay.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Autoplay.exe or
          /media/cdrom0/Autoplay.exe.zip, and cannot find /media/cdrom0/Autoplay.exe.ZIP, period.

The same message appears all the time regardless of what the program I am trying to load.  At the moment I am loading Adobe photoshop 7 (a legal version, not a crack).  I have loaded this on Wine before and had no problems.  Any suggestions please and not to use Gimp please.  

Thanks

Tony

PS Just thought is it because I am now running a dual core 64 bit computer? The Ubuntu is 8.10 64 bit.

---

### Post by jacksaff on 2009-03-23
64bit should be able to run anything 32bit can as long as you install ia32-libs  -- "sudo apt-get install ia32-libs"
There are also quirks with wine and cd drives if the application has any form of cd authentication.

---

### Post by Tony_photoplus on 2009-03-23
> **jacksaff said:**
> 64bit should be able to run anything 32bit can as long as you install ia32-libs  -- "sudo apt-get install ia32-libs"
There are also quirks with wine and cd drives if the application has any form of cd authentication.


I think its already loaded
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So I am thinking to get what I want out of an OS I need to downgrade to 32bit Ubuntu until they have caught up with technology.  But as I have found I still have problems because its 64 bit.  So I am dammed if I do and dammed if I don't.

Tony

---

### Post by cogadh on 2009-03-23
Are you certain that Wine is installed correctly? The error message you are getting is very similar to the one you get when you try to run an .exe but haven't actually installed Wine yet.

---

### Post by Tony_photoplus on 2009-03-23
> **cogadh said:**
> Are you certain that Wine is installed correctly? The error message you are getting is very similar to the one you get when you try to run an .exe but haven't actually installed Wine yet.

It certainly looks as if its all loaded. Looked in my files, and package manager everything.  I am just looking to assess if I can update the Wine, it updating now and we will see if that cures the problem.

Tony

---

### Post by Tony_photoplus on 2009-03-23
Ok, I have now tried the latest Wine and its sour.  I have tried a few programs and nothing, just the same message

Tony

---

### Post by hikaricore on 2009-03-23
Run wine from a terminal and do it properly:

> wine program.exe

For whatever reason you're running things from Nautilus and your system thinks they are zip files.

---

### Post by Tony_photoplus on 2009-03-24
> **hikaricore said:**
> Run wine from a terminal and do it properly:



For whatever reason you're running things from Nautilus and your system thinks they are zip files.

Since updating Wine I did try that and it didn't work, however, it did work when I put terminal into cd desktop.  But that only worked for the downloads .exe program providing I took them out of my download file and onto the desktop.  The same process didn't work for the Photoshop and I didn't know how what to do then.  So I opened up the disk to view the files and just to see I right clicked the Photoshop.exe and not the 'Autoplay'.  I clicked on open with Wine and surprise!!  It opened up and started loading and now its working.  BUT!  I have a problem with the docks and I know thats a Wine fault which they might or might not sort out.

Thanks for the input

Tony

---

