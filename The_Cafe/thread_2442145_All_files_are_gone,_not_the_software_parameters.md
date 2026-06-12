---
title: "All files are gone, not the software/ parameters"
date: 2020-04-30
forum: The Cafe
---

### Post by Chelidze on 2020-04-30
Strangest thing happened to my friends lubuntu 16.04 for the second time.
Second time this happened all the files on the PC are gone, however when you enter home directory every original folder is there.
All system configurations hasn't changed and all software presets settings are there.

Strange thing is that only i know the root password of the system and besides using chrome and libreoffice nothing was being used on it.
Clearly he wouldn't go into folders in the system and delete file by file to than be angry about it.
I looked at the system and no backup no nothing looks squeaky clean.
He gave it to an it shop and they are trying their luck with it, to try to roster the files.

When i asked him what happened he sad nothing i saved an odt file and then shut down the system.


What could have happened.

---

### Post by TheFu on 2020-04-30
Is he using snaps or other application constraining tools like firejail?

snaps limit where files can be stored and the locations are set by the snap package team, but limited to $HOME and a few other places, but only if specifically requested through a separate snap command.

Firejail et al can be run in a --private option which prevents **any** saving of anything on the file system. That is a feature. ;)

Or the disk could be failing.  SSDs fail all the time.  Check the SMART data.

---

### Post by Chelidze on 2020-04-30
> **TheFu said:**
> Is he using snaps or other application constraining tools like firejail?

snaps limit where files can be stored and the locations are set by the snap package team, but limited to $HOME and a few other places, but only if specifically requested through a separate snap command.

Firejail et al can be run in a --private option which prevents **any** saving of anything on the file system. That is a feature. ;)

Or the disk could be failing.  SSDs fail all the time.  Check the SMART data.


Well no pretty much chrome and libreoffice nothing else is being used there.
it's a regular disc drive and i don't think it can fail that way at least i never seen, i would say it filed when the files couldn't be open but missing files are strange.
 only files being deleted in different directory and ntfs partition that is left from old windows install, no files were effected there.
The folder file tree looked intact however for example downloads (files inside are gone), documents (files inside are gone), desktop (files inside are gone)

It's like someone factory reset the phone, but even there it's strange because chrome settings and log ins were all uninfected. 

I know i might be a stretch but is that a virus or something, but even there i don't understand i know there is ransomware on linux but just deleting files on partition what kind of a virus is that.

---

### Post by TheFu on 2020-04-30
Don't use any GUI tool. No file manager. 

Show the **ls -al** for the HOME directory involved. We need some facts.
Check the SMART data.
Check df -hT
Check lsblk -e 7 -o name,size,type,fstype,mountpoint
Check ls -al $HOME

---

### Post by Chelidze on 2020-04-30
> **TheFu said:**
> Don't use any GUI tool. No file manager. 

Show the **ls -al** for the HOME directory involved. We need some facts.
Check the SMART data.
Check df -hT
Check lsblk -e 7 -o name,size,type,fstype,mountpoint
Check ls -al $HOME


Sorry there is a reason why i posted this in cafe because as i mentioned 

> He gave it to an it shop and they are trying their luck with it

---

### Post by TheFu on 2020-04-30
Don't be surprised when they format it, load Windows and return it with a smile and a $250 bill.

---

### Post by Chelidze on 2020-04-30
> **TheFu said:**
> Don't be surprised when they format it, load Windows and return it with a smile and a $250 bill.

if that will not happens and i will try a follow up but that happened second time with it, first time it happened i was just like i have no idea you mist have deleted files on it. just updated stuff and after a month same thing happened and even if there is a refresh function on lubuntu that i'm not aware of it you will need su password that only i know, that is almost as complex as 123456, but sure no one would enter it.

He has the tendency to f up every computer so i was tired with his windows bs and to years ago installed lubuntu on it, he managed to f it up as well

---

### Post by The Cog on 2020-04-30
Does he use the command line?

Either of these commands might do it:
```
rm */*
find -delete
```
Do "hidden" files (starting with a dot) disappear as well?

---

### Post by Chelidze on 2020-05-01
> **The Cog said:**
> Does he use the command line?

Either of these commands might do it:
```
rm */*
find -delete
```
Do "hidden" files (starting with a dot) disappear as well?

He doesn't use commend line but i think i sow few hidden .doc files
Also it might be downloaded files before i had a  a chance to take a look at it.

Also when the IT tech got it they say they managed to recover files on it

---

### Post by sdsurfer on 2020-05-01
What about the user? If, as you say, from root you can see all the directories (can you see the files as well?), perhaps it's an issue with the user name used to log in to the GUI. Just a thought.

---

### Post by Chelidze on 2020-05-01
> **sdsurfer said:**
> What about the user? If, as you say, from root you can see all the directories (can you see the files as well?), perhaps it's an issue with the user name used to log in to the GUI. Just a thought.

Well the the user works log out log in every thing works but when i checked first time it happened (it happened twice) the space well pretty much empty other then os.

Maybe @**TheFu** is right and it is actually bad HDD how ever why would every file disappear at the same time, ok at least wouldn't there be some corrupt files left.

---

### Post by rbmorse on 2020-05-01
Does 16.04 have that xdg "feature" that recreates /home directories specified in /etc/xdg/user-dirs.defaults if they are missing on startup? 

 I forget when that started. Could that be what we're seeing here?

---

### Post by Chelidze on 2020-05-01
> **rbmorse said:**
> Does 16.04 have that xdg "feature" that recreates /home directories specified in /etc/xdg/user-dirs.defaults if they are missing on startup? 

 I forget when that started. Could that be what we're seeing here?


Sorry cant deduct the information here, not sure what xdg does, when i asked the IT guys what they did with the laptop they sad we used EaseUS to recover files from it some were damaged but we managed to save quite a few.

I don't have access to that laptopt but yesterday when i used it no error massages no nothing, the languages the tool bar the software had all preferences customization saved as if nothing has happened only thing that was a problem all the files were gone.
Second time it happened on that installation.

---

