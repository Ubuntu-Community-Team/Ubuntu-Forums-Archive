---
title: "Installing Diablo2: LOD Wine"
date: 2011-06-12
forum: Wine
---

### Post by Driger on 2011-06-12
Hi, wasnt sure whether to post this in gaming and leisure or wine so i picked here... sorry if its in the wrong place:D

Im trying to install diablo 2 expansion from the cd onto my already working diablo 2 instillation in wine which was also installed with the cd's. but i have run into trouble. i put in the LOD expansion disc and nothing happened. so i went to the disc and clicked the installer.exe and nothing productive happened with that either (just wine could not open executable bit warning) i then tried to get it to work by going to the terminal and typing

```
cd .wine
``````
wine "d:\installer.exe"
```Then this came up:
Warning: could not find DOS drive for current working directory '/home/scott/.wine', starting in the Windows directory.
wine: cannot find L"D:\\installer.exe"

i searched around a bit and read that "To get around this copy the contents of all installer disks into a local  directory and change the ownership of the files therein to your own  user"

when i attempted to copy the files from the cd to a folder i had created in my home folder i got the following error
* There was an error copying the file into /home/scott/untitled folder. Error opening file: Permission denied*

**Im guessing if i can copy the files to a folder in my home then i will be able to run the .exe with wine and successfully install the game? **

**How do i copy the files from the disc to a folder when im denied permission to copy and paste them?**

if you have any other ideas on how to get this work other than copying the contents of the disc to a folder in my home please tell me!

---

### Post by Driger on 2011-06-13
i tried to mount the disc as read and write but it didn't work 

i tried to edit the permissions by using this code

```
chmod a=r '/media/cdrw/installer.exe'
```and i recieved this message *"chmod: changing permissions of `/media/cdrw/installer.exe': Read-only file system"*

nothing happened so i looked around and found out that i had to mount the disc as rw so i used these codes to do it

```
umount /media/cdrw 
```then signed in as root with
```
sudo su
```entered this into the terminal to mount with read and write privileges 
```
mount -o rw /media/cdrw
```but i received this message
*mount: block device /dev/sr0 is write-protected, mounting read-only*

This is very frustrating. why cant wine just open the installer when i click on it?

 why do i have to go around and change all this file permission stuff for the expansion disc when diablo 2 by itself installed with no major difficulties?

---

### Post by Dougie187 on 2011-06-13
have you checked to see if the cd is mounted as drive d in wine configure?

I'm not sure if that will help or not.

---

### Post by Driger on 2011-06-13
Yeah its mounted as d in wine configure

had an issue with that while instaling classic diablo 2

this is what i did to fix that problem 
(found from this thread [http://ubuntuforums.org/showthread.php?t=1766852](http://ubuntuforums.org/showthread.php?t=1766852))

Made a directory called /media/cdrw.
Open a terminal and make the command
```
sudo mkdir /media/cdrw
```Made these two commands in the terminal to make a change in fstab to connect the directory to the cd-drive
```
gksudo gedit /etc/fstab
```and added this line
**/dev/sr0 /media/cdrw udf,iso9660 users,noauto,rw 0 0** to the bottom 
Started Wine config and changed/added the path in D: to **/media/cdrw**
and used advanced to set D: to CD-ROM.

Would what i did there be interfering with the instillation of the expansion perhaps?

---

### Post by P-I H on 2011-06-13
I got it working with this methode, but I used wine "d:\SETUP.EXE" to start the installation.

I just looked at the LOD CD and there is no file called installer.exe. There is a file called INSTALL.EXE and one called SETUP.EXE.

---

### Post by Driger on 2011-06-13
> **P-I H said:**
> I got it working with this methode, but I used wine "d:\SETUP.EXE" to start the installation.

I just looked at the LOD CD and there is no file called installer.exe. There is a file called INSTALL.EXE and one called SETUP.EXE.

Interesting, i might have a different version of the disc than you do as all that is on the disc is ; autorun.inf, disc.ico, installer.exe and, installer tome.mpq.... attached is a screenshot of the disc contents if that helps.

anyways i tried going to the terminal and using

```
cd .wine
```then tryed to open the installer.exe by draging and dropping it onto the terminal (which gave me this)

```
wine '/media/cdrw/installer.exe'
```the message i got from doing that was; Warning: could not find DOS drive for current working directory '/home/scott/.wine', starting in the Windows directory.
wine: cannot find L"D:\\installer.exe"

and i have no clue what that means unfortunatly

---

### Post by Driger on 2011-06-15
still no luck, going to try with playonlinux

---

### Post by Turtlicious on 2011-06-18
First: Did it work?

Second: I pretty much mounted it with Furious ISO then installed from their, then I patched and put some No-CD Cracks and I was golden.

---

### Post by Breambutt on 2011-06-18
Okay, you've burnt the CD yourself? Kinda curious content too, mine has plenty of more files on it. I know at least the downloadable purchases were a little different.

How about then *wine '/media/Diablo II LOD/installer.exe'* ?

---

### Post by RoflHaxBbq on 2011-06-19
Do not install from the CDs.
It is possible. I have done it before, but it's easier to do it another way.

Make a clean directory. Copy all data from the CD1 into this directory. In wine config, list this directory as a drive. Click advanced and make sure it is listed as a CD drive.
Make another clean directory and copy the data from the second disc if there is one. (I can't remember). Do not list it as a drive yet. Do the same with disc 3, 4 etc.

Navigate to the first directory containing the data from CD 1. Run installer.exe. When it asks for you to insert disc 2 if there is one, minimize the installer and go to wine config. Remove the entry for the directory containing disc 1 data and make an entry for the directory containing disc 2 data. List it as a CD drive. Maximize the installer and click next. It will think that disc 2 is inserted. Repeat for all other discs as appropriate.

Once you have installed it, run the latest patch and reset your wine config to what it was beforehand.

---

### Post by Wose on 2013-04-17
Solution for Google searchers:

> **Driger said:**
> why do i have to go around and change all this file permission stuff for the expansion disc when diablo 2 by itself installed with no major difficulties?

Probably because your expansion disc has a newer installer. The Diablo II Gold version has the same issue.
The Problem is that the CD contains permissions that wont allow your user to access the relevant files.
To fix this, you mus force your own user as owner of the files. This can be done (in a Terminal) with:
```
sudo mount -o uid=$USER /media/cdrom
```

Assuming that the cd is unmounted. Then it should be possible to execute the installer normally.

Note: To change the discs, you have to unmount the current one with ```
sudo umount /media/cdrom
``` and mount the next one just like before (for the multi disk Gold version install).

---

### Post by overdrank on 2013-04-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

