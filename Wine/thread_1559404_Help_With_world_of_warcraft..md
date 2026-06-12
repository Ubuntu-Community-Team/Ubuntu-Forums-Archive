---
title: "Help With world of warcraft."
date: 2010-08-23
forum: Wine
---

### Post by Mr_VeRiTy on 2010-08-23
Hi, I'm trying to install world of warcraft from disk.
First I tried these instructions from winehq 
```
Below are the instructions for installing from WoW Disks :- 

To install from the CDs the files need to be copied over to your computer as attempting to install directly from disk will result in failure. 

Create a folder in a convenient location such as on the desktop called wow_install

You will only need to install WoW using the Wrath of the Litch King disks. (The Wrath disks will install the WoW core game and the Burning Crusde as well).

Insert Disk 1 of the Wrath of the Litch King.

When you open the disk you will not be able to see all the files as they are hidden. To get them to show run the following code in Terminal :-

sudo mount -o remount,unhide /dev/sr0 

If that code doesn't work try this one :-

sudo umount /dev/cdrom
sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
Then open the disk again and you should see all the files. 

Open the disk and copy all the files to your wow_install folder.

Now insert Disk 2 of the Wrath of the Litch King and follow the same step above to unhide the files. 

Copy only the Installer Tome #.mpq files to the wow_install folder. (# will be a number. Basically from Disk 2 copy only the Installer Tomes that have a number in their name (NOT the one without a number, we got that one from Disk 1)).

Once complete eject the disk and run the Installer.exe in the wow_install folder with wine. (simply right click it and selct "Open with Wine Windows Program Loader").

WoW will now install.

Once the installation is complete a shortcut will be on the desktop to run WoW. Of course you will have to go through the patching process.

```
But got confused, as it wanted to overwrite some files from disk one with files from disk two, then I tried these instructions from the wowwiki.com site:
```
Create a new folder on your computer. Copy all of the files from the first CD and all but the Installer.exe file from the rest to this directory on your hard drive (overwrite when prompted). Copying the Installer.exe from the other CD's will cause the install to fail with
Unrecognized key "options". (AttributeParser::Parse)
Then run:
cd /<path-to-directory>/
wine Installer.exe
Replace <path-to-directory> with the right path to the directory where you copied all the files. You should now have the installation running, but make sure the CD media is out of the drive or it will check there and you'll be stuck in it again.
```
But I got the error "please begin the installation from disk one" and the output from wine in terminal was
```
luke@computer:~/Desktop/wow_install$ wine Installer.exe
err:wineboot:pendingRename couldn't get file attributes (2)
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
Missing symbol {OriginalInstallPath}! (SymbolTable::UnmappedSymbolSubstitution)
fixme:font:CreateScalableFontResourceW (1,L"C:\\users\\luke\\Temp\\Blizzard Installer Temporary Data - 0032f401\\FrizQuadrata.fot",L"C:\\users\\luke\\Temp\\Blizzard Installer Temporary Data - 0032f401\\FrizQuadrata.ttf",(null)): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13e030,0x13df78): stub
err:mmtime:TIME_MMTimeStop Timer still active?!

```
Any help on how to install it please, I can't install it on a windows partition as I have none, and I can't use the download client as I cant download 7GB of files as my download speed is 
so slow, plus I already bought the disk. If you need more info just ask. Also I'm on a laptop if that changes anything.

---

### Post by MrPanda on 2010-08-24
i installed it from the download client, it got done installed it went thought they patches and froze so i restarted the launcher from my desktop and all it will say is starting world of warcraft and then nothing happens, so then i reinstalled it going to a folder and launching the .exe file again. this time i saved it to my desktop now i have a world of warcraft.temp file and everything in the file has  a .temp i can execute these files because they have a .temp so what can i do i really want to play wow on linux.

---

### Post by Zirts on 2010-08-24
Cant you just insert the cd open the CD folder, locate the installer.exe or whatever, right click on it, copy the full path, open up Terminal and type wine and the path to it?

---

### Post by MrPanda on 2010-08-24
i was installing it just like this guys was [http://www.youtube.com/watch?v=tTk9y5QKzQk](http://www.youtube.com/watch?v=tTk9y5QKzQk)
and i am just trying to install it again now. i have saved it to my desktop and i get a worldofwarcraft.temp file what do i do with that?

---

### Post by sydbat on 2010-08-24
MrPanda - I know this might sound stupid, but...have you tried installing WOW like you would on a Windows machine? It just might work and solve your problems. I believe those instructions you found are IF you are unable to install normally through WINE.

---

### Post by MrPanda on 2010-08-24
ok i am dumb, it does work with just the discs i have tried it with CSS and i didn't work so i just thought it wouldn't work with wow. lol srry guys for me being retarded. i have a question thought will i run into trouble with the patches?

---

### Post by sydbat on 2010-08-24
> **MrPanda said:**
> i have tried putting the disc in and running it with wine dont work.  The installation was halted. You can resume downloading and installing at a later time by running the Installer again either from the web site or from the copy you saved locally.Is WINE configured to read from the CD?

Also, found this - [http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

and this - [http://wine-review.blogspot.com/2010/01/running-world-of-warcraft-in-ubuntu.html](http://wine-review.blogspot.com/2010/01/running-world-of-warcraft-in-ubuntu.html)

---

### Post by sydbat on 2010-08-24
> **MrPanda said:**
> ok i am dumb, it does work with just the discs i have tried it with CSS and i didn't work so i just thought it wouldn't work with wow. lol srry guys for me being retarded. i have a question thought will i run into trouble with the patches?You changed your post while I was answering. However, maybe the links I provided might help someone else.

Also, I have no idea how the patching works through WINE. Give it a try and let us know how it goes. More info from you after doing it will help others.

---

### Post by MrPanda on 2010-08-24
well the discs are working srry for being so dumb it didn't work with CSS so i just thought it wouldn't work with wow. again i am srry. i just have one more question while i have some one here will i have trouble with the patches after i get the game downloaded and installing the patches?

---

### Post by oleink on 2010-08-24
> **MrPanda said:**
> well the discs are working srry for being so dumb it didn't work with CSS so i just thought it wouldn't work with wow. again i am srry. i just have one more question while i have some one here will i have trouble with the patches after i get the game downloaded and installing the patches?

Hey don't be so down on yourself we all make some foolish mistakes every once in a while even though we actually know somewhere in the back of our minds how to accomplish our tasks

---

### Post by sydbat on 2010-08-24
> **oleink said:**
> Hey don't be so down on yourself we all make some foolish mistakes every once in a while even though we actually know somewhere in the back of our minds how to accomplish our tasksThis.

And just do the updates and let us know how they work. If they do not, it will be a bit of a pain (because of the time spent), but you can share what happened and we can figure things out together.

If it goes fine, let us know that too, so others can benefit from your experience.

---

### Post by MrPanda on 2010-08-24
thank you, i just thought since i had problems with CSS i would have problems with wow. thank you guys for all of you help.

---

### Post by MrPanda on 2010-08-24
i get installation failed on the last disc of Burning Crusade. srry about double posting.  The file "C:\Program Files\World of Warcraft\Data\expansion.MPQ : Sound\Music\ZoneMusic\Azuremyst\AV_DraeneiWalkUni03r.mp3" could not be written. If this problem persists, please contact Blizzard Technical Support. (MPQTarget::DoMPQCopy)

and when your in the login screen you can type anything you want for a username and password and it downloads and wants you to restart to install the patch then when you do that, that is when it comes up with install wow and move it to a public folder. kinda thinking about giving up on playing wow.

---

### Post by oleink on 2010-08-24
Sorry I can't be of more help.  Ive given up on windows completely and don't even use wine (I will when I build my gaming computer but only for specific games and I may just buy Cedega) But anyway what i was gonna say is take a look at Regnum Online.  It isn't WOW but it's still a pretty fun game and it's free

---

### Post by Ms_Angel_D on 2010-08-24
Moved top Wine forum

---

### Post by cwwilson721 on 2010-08-25
> **MrPanda said:**
> i get installation failed on the last disc of Burning Crusade. srry about double posting.  The file "C:\Program Files\World of Warcraft\Data\expansion.MPQ : Sound\Music\ZoneMusic\Azuremyst\AV_DraeneiWalkUni03r.mp3" could not be written. If this problem persists, please contact Blizzard Technical Support. (MPQTarget::DoMPQCopy)

and when your in the login screen you can type anything you want for a username and password and it downloads and wants you to restart to install the patch then when you do that,[COLOR=Red] that is when it comes up with install wow and move it to a public folder[/COLOR]. kinda thinking about giving up on playing wow.You ARE installing in XP mode, right? Otherwise sound and other things will be a BIG issue.

The other thing that comes into play for patches is the nefarious "folder permissions". Make SURE you can access the WoW folder. There are TONS of posts on how to get around this.

I've been playing wine/WoW for years, and the worst thing is the folder permissions getting borked by patches.

---

### Post by sydbat on 2010-08-25
Another thought - Have you installed [winetricks]("http://wiki.winehq.org/winetricks")? It might help solve your problems.

---

