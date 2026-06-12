---
title: "Where is wine"
date: 2006-12-09
forum: Repositories &amp; Backports
---

### Post by Klarsin on 2006-12-09
I downloaded and installed wine from synaptics. It said that wine was installed. I found wine files, but not in the application menus. Maybe don't know how it is to be used. Is  wine suposed to show in the applications menu or just stay in the system files and work automatically?

---

### Post by synt4xerr0r on 2006-12-09
Im having the same problem im guessing that when you download something that is to be run through wine u right click on it and select run through wine probbably

---

### Post by yahurd on 2006-12-09
to open say, setup.exe in cd drive with wine, i would just type "wine /media/cdrecorder/setup.exe" in a terminal, just type wine then point to file

---

### Post by corevette on 2006-12-10
there is no gui for wine (there might be a 3rd party addon though).  to use wine, go to the terminal/console and navigate to the .exe file you want open.  once you get to that folder, letsay you wanted to open setup.exe you'd type in the prompt ```
wine setup.exe
```

---

### Post by Klarsin on 2006-12-11
Trying to open setup.exe and get this:

me:~$ wine
Wine 0.9.9
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
me:~$ wine --version
Wine 0.9.9
me:~$ wine/media/cdrom0/setup.exe
bash: wine/media/cdrom0/setup.exe: No such file or directory
me:~$


Me is not root. Do I have to be in root to do this?
I checked out the navigation in the file system and this should be the correct path.

---

### Post by mcduck on 2006-12-12
the problem there is that you need to have a space between 'wine' and the file you want to run :)

wine /media/cdrom0/setup.exe --right
wine/media/cdrom0/setup.exe --wrong

---

### Post by Klarsin on 2006-12-12
Thanks, it installed great, but after saving the first file I can't find it anywhere to reopen it. It was supposed to be under c:drive/my home folder somewhere. But there is no c: drive, so I thought I'd find it in my home folder but its not there. how do I designate where this file is to be put during install? And where is it now?

---

### Post by mcduck on 2006-12-13
I haven't used wine myself, but if I remeber right it puts it's 'drives' inside ~/.wine. (hidden directory inside your home)

So if I'm right c-drive would be ~/.wine/c

Probably 'man wine' will tell you the right place ;)

---

### Post by martijn hoekstra on 2006-12-15
I would be nice to see a new nautilus item on binary files with a "run in wine" option. Not sure where that suggestion would go actualy

---

### Post by Erunno on 2006-12-16
Just a small suggestion:

Go to [http://www.winehq.com](http://www.winehq.com) and get the newest version from wine (add the repository which is mentioned in the Ubuntu download section). Wine is under constant heavy development and with each release it's less likely that you will encounter problems with windows applications (truth to be told, sometimes an update also breaks application compatiblilty but the good outweighs the bad in my opinion).

Cheers,
Erunno

---

### Post by Peetke on 2006-12-20
Run "winecfg" after the install (from your user, not as root). This will setup a lot of things and you can tweak/configure all kinds of things.

---

