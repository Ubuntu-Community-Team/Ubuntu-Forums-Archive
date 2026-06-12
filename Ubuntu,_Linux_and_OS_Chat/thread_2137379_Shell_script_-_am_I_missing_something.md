---
title: "Shell script - am I missing something?"
date: 2013-04-20
forum: Ubuntu, Linux and OS Chat
---

### Post by f00dl3 on 2013-04-20
Question - I've migrated (or am mostly migrated) from Windows XP to 64 bit Ubuntu to keep up with the times and get away from arcaic 32 bit O/S environments, and more specifically, avoid Windows 8's phone GUI with a 10 foot pole.

I am working on migrating an old batch file to clean my SD Card from my phone. I got all the commands working fine through the shell, but when I attempt to execute the shell script I wrote it appears to be adding a \r on the end of each "rm" command.

I have attempted putting the directory path in quotations, and doing it without the -r (recursive) option. I've also attempted running it as SUDO.  I'm guessing I'm missing something terribly obvious.

Also, can't get the script to output to a text file, even though the command works perfect when typed manually in the shell.

Here is the script:

```
echo Cleaning crap off this MicroSD card... 
rm -r /media/astump/SPH-D700/.tubemate/* 
rm -r /media/astump/SPH-D700/albumthumbs/* 
rm -r /media/astump/SPH-D700/Android/data/* 
rm -r /media/astump/SPH-D700/AppGame/* 
rm -r /media/astump/SPH-D700/bluetooth/* 
rm -r /media/astump/SPH-D700/.thumbnails/* 
rm -r /media/astump/SPH-D700/DolphinMagazines/* 
rm -r /media/astump/SPH-D700/GoLauncherEX/advert/* 
rm -r /media/astump/SPH-D700/GoStore/* 
rm -r /media/astump/SPH-D700/tmp/* 
rm -r /media/astump/SPH-D700/TunnyBrowser/app_cache/* 
rm -r /media/astump/SPH-D700/TunnyBrowser/app_databases/* 
rm -r /media/astump/SPH-D700/TunnyBrowser/app_geolocation/* 
rm -r /media/astump/SPH-D700/TunnyBrowser/app_icons/* 
rm -r /media/astump/SPH-D700/TunnyBrowser/app_thumbnails/* 
rm -r /media/astump/SPH-D700/TunnyBrowser/cache/* 
rm -r /media/astump/SPH-D700/Video/temp/* 
rm -r /media/astump/SPH-D700/bootex.log 
rm /media/astump/SPH-D700/DiskCacheIndex*.tmp 
rm /media/astump/SPH-D700/latest_attachment 
rm /media/astump/SPH-D700/tmp.png 
echo  
echo Listing and deleting LOST DATA FILES 
ls /media/astump/SPH-D700/LOST.DIR/* 
rm -r /media/astump/SPH-D700/LOST.DIR/* 
echo  
echo Writing log file... 
echo "SD-Clean build 53 ran at $(date)">>SD-Clean.log 
echo  
echo "Done. If any lost data files were listed, check integrity of SD card."
```

and here is the output with the errors

```
astump@astump-EX58-UD4P:/media/astump/SPH-D700$ sudo sh SD-Clean.sh
[sudo] password for astump: 
Cleaning crap off this MicroSD card...
rm: cannot remove `/media/astump/SPH-D700/.tubemate/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/albumthumbs/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/Android/data/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/AppGame/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/bluetooth/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/.thumbnails/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/DolphinMagazines/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/GoLauncherEX/advert/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/GoStore/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/tmp/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/TunnyBrowser/app_cache/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/TunnyBrowser/app_databases/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/TunnyBrowser/app_geolocation/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/TunnyBrowser/app_icons/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/TunnyBrowser/app_thumbnails/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/TunnyBrowser/cache/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/Video/temp/*\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/bootex.log\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/DiskCacheIndex*.tmp\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/latest_attachment\r': No such file or directory
rm: cannot remove `/media/astump/SPH-D700/tmp.png\r': No such file or directory
```

Listing and deleting LOST DATA FILES
: No such file or directorytump/SPH-D700/LOST.DIR/*
rm: cannot remove `/media/astump/SPH-D700/LOST.DIR/*\r': No such file or directory

Writing log file...
: Invalid argumentD-Clean.sh: cannot create SD-Clean.log

Done. If any lost data files were listed, check integrity of SD card.

---

### Post by steeldriver on 2013-04-20
It's likely not anything in Ubuntu that's adding the \r - that's a Windows line termination character, presumably you copied and then modified your original bat file and the line terminations got copied across

You can either run your file through a utility like dos2unix or do the same with a sed oneliner

```
sed -i $'s/\r//' SD-Clean.sh
```

or with 'tr'

```
tr -d $'\r' < SD-Clean.sh > SD-Clean-(2).sh
```

['tr' can't operate interactively on the file, so it needs to write out to a new file - you can rename it after (which is a bit safer since you still have the old file if something goes wrong); most versions of sed can do interactive edits on the fly with the -i switch but you need to be sure you know what you're doing]

---

### Post by f00dl3 on 2013-04-20
Thank you! That worked like a charm!

---

