---
title: "wine messed up"
date: 2010-01-06
forum: Wine
---

### Post by wirate on 2010-01-06
I followed some instructions on a forum i do not remember and deleted some files. now when i do
 	Code:
 	sudo apt-get remove wine 
 	Quote:
 	 	 		 			 				Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-liberation ttf-mscorefonts-installer cabextract winbind
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 55.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135509 files and directories currently installed.)
Removing wine ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing wine (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1) 			 		 	 	 
and when i do
 	Code:
 	sudo apt-get install wine 
 	Quote:
 	 	 		 			 				Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up wine (1.0.1-0ubuntu:cool: ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing wine (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by houseworkshy on 2010-01-06
This may or not be pertinant.  I had problems removing wine on an installation quite some time ago.  I can't remember how I got into the mess but what had happened was that files, from something on wine which I had removed, wouldn't delete from the recycle bin.  In the end it turned out to be a permissions issue which I dealt with by changing the permissions of the relevant files.  It may be worth checking the permissions of the files which are in your way as wine seems to have the ability to change them.  When you have regained control over them again an apt-get auto clean may also help before the reinstall stage ( unless your only motivation for reinstalling was to get rid of the thing ).  You can access permissions by right clicking on a file then clicking on "properties" then on the relevant tab.  Only an idea.

---

### Post by houseworkshy on 2010-01-06
I've just had a hunt around the net for your error codes and there is a lot out there but I couldn't find anything identical.  For similar things the solutions mostly involved force installs followed up by apt-get updates.  For details on this take a look at the manual page on apt-get in the terminal ( man apt-get ).  Probably better to try gentle methods first.

---

### Post by SchizmWolf on 2010-01-06
I don't know if this will work or not, but I had a problem installing wine the first time. What I did to fix it was:
```
 sudo apt-get purge wine | sudo apt-get install -f | sudo apt-get install wine 
```

It was a pretty simple fix, dunno if it'll work on yours though. Never heard of that particular problem.

---

### Post by Soulcage on 2010-01-06
Karmic's package is wine1.2 now. Wine is a dummy package now. Atleast after adding the repo like it says at winehq.

---

### Post by wirate on 2010-01-06
> **SchizmWolf said:**
> I don't know if this will work or not, but I had a problem installing wine the first time. What I did to fix it was:
```
 sudo apt-get purge wine | sudo apt-get install -f | sudo apt-get install wine 
```It was a pretty simple fix, dunno if it'll work on yours though. Never heard of that particular problem.


gives the same error. and wine1.2 is also broken

---

### Post by Soulcage on 2010-01-07
I wonder if you can find the command(s) you ran by: gedit ~/.bash_history
in a terminal.

---

### Post by wirate on 2010-01-07
I deleted files in nautilus with root priveleges. and I clear bash history with bleachbit regularly :(

---

### Post by houseworkshy on 2010-01-08
Usually bleach won't remove the system log files, may be worth looking there especially at the auth.log  Bleach can cause problems as it can take out far too much.  I use it to clean flash and thumbnails quickly but not for much else as it is very good at breaking things.  It may even be the real cause of the problems.
While you are in admin have a look at synaptic.  One can highlight an installed program and look at it's properties, one of these properties is a full list of &#8220;installed files&#8221;.  Methodically going through these may be a way of finding out what you deleted when following the advice on that forum, check the permissions of files which are still there too.    
This would take some time.  There is another choice, when stuck, you could put the live cd in the drive when the system is running, add the cd to the software sources, and let it do it's stuff.  Including replacing new with old.  This can mend things when you don't have a clue what's broken but it is a retrograde step and you may have to do some of the same fiddling arounds you did when you first installed.

---

