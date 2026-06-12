---
title: "[windows] Syncing folders outside &quot;Documents and Settings&quot; should be allowed"
date: 2011-10-07
forum: Ubuntu One (CLOSED)
---

### Post by Gloosy on 2011-10-07
In Linux, all user files are contained in his home directory and that's fine. But Windows way is totally different: the system is in one folder, the software is in another and ALL the other folders and secondary partitions belong to user.

In fact, most of the technically advanced users do not use their windows home folders at all. Another common practice is giving one partition to the OS and the other one to the user files.

So, allowing sync folders only under user home folder is totally uncomfortable and this should be changed.

---

### Post by s3rgio on 2011-10-12
I agree. All my documents are in a separated partition (too many windows re-installations...).

---

### Post by SeijiSensei on 2011-10-12
I don't use Ubuntu One, but couldn't you get around this restriction by mounting the Windows partions(s) first in Linux then syncing?  It's what I do when I need to rsync from a Windows filesystem to an image on a Linux server.

---

### Post by Lisiano on 2011-10-15
Not sure what the problem is, you can always mount or bind your Windows or Data partition inside your /home/username directory.
For example
```
sudo mount --bind /media/Win7 /home/$USER/Windows
```
```
lisiano@Lisiano-Ubuntu:~$ sudo mount --bind /media/Win7 /home/lisiano/Windows
lisiano@Lisiano-Ubuntu:~$ cd Windows
lisiano@Lisiano-Ubuntu:~/Windows$ ls
AECS5COMMONPATH                 NosTale(UK)
bf3 2011-10-01 17-36-08-58.mp4  NVIDIA
bf3 2011-10-01 21-39-48-99.mp4  PerfLogs
bf3 2011-10-04 19-47-39-38.jpg  ProgramData
bf3 2011-10-04 20-45-04-26.mp4  Program Files
Boot                            Program Files (x86)
bootmgr                         Recovery
BOOTSECT.BAK                    $RECYCLE.BIN
cygwin                          shared.log
Documents and Settings          System Volume Information
fl-server-errors.log            Tools
HOSTCS5DEST                     Users
MoTemp                          Windows
lisiano@Lisiano-Ubuntu:~/Windows$ 
```
Now just going to any folder inside the Windows partition will let me sync that folder.

As for doing it in Windows, you can always make a Hard link that will make Ubuntu One think the files are inside "Users". Don't remember how to make them though.
Edit: Found it -> [http://www.howtogeek.com/howto/windows-vista/using-symlinks-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/using-symlinks-in-windows-vista/)

---

### Post by mastablasta on 2011-10-17
what we talk about here is that this feature to choose the folder you want to sync should be built in.

ubuntu one for windows --->>> uninstalled....

---

