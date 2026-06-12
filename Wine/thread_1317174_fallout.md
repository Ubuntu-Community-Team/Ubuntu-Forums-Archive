---
title: "fallout"
date: 2009-11-06
forum: Wine
---

### Post by crowdedelevator on 2009-11-06
is there anyway to run this in wine? its a mdf/mds file
im fairly new to linux

---

### Post by Melcar on 2009-11-06
The original Fallout?  Don't you have the disks?  It installs and plays just fine.  
If not, the file you got is an image file.  Either burn it to a disk or mount it on your HDD.  Then proceed with the installation as normal.

---

### Post by crowdedelevator on 2009-11-06
yes the original, and how do i mount it?

---

### Post by Melcar on 2009-11-06
sudo mount -t iso9660 -o loop /<location of image to mount> /<location where you want to mount the image>.
Or if you want a frontend you can install [AcetoneISO]("http://www.acetoneteam.org/").

---

### Post by beastrace91 on 2009-11-06
You mount in Linux using the mount command. Do the following: ```
sudo mkdir /mnt/image
sudo mount -o loop -t iso9660 /pathtoimagefile/myimage.iso /mnt/image
```

Then your mounted image will appear in /mnt/image

For reading on it can be found [here](http://lindesk.com/2007/05/how-to-mount-isomdf-images-in-linux/)

Regards,
~Jeff

---

### Post by crowdedelevator on 2009-11-06
wish i knew how to use the console . you guys throw out things like that and i just copy/paste

---

### Post by Melcar on 2009-11-06
> **crowdedelevator said:**
> wish i knew how to use the console . you guys throw out things like that and i just copy/paste


That's how most of us learned in the first place :D.  Eventually commands start getting engraved in your brain.

---

### Post by crowdedelevator on 2009-11-06
i dont know much of anything about computers, but it just fell into my lap to try ubuntu and im hooked. i knew how to use windows pretty well, not dos commands or anything, but im hooked on linux

---

### Post by crowdedelevator on 2009-11-06
> **beastrace91 said:**
> You mount in Linux using the mount command. Do the following: ```
sudo mkdir /mnt/image
sudo mount -o loop -t iso9660 /pathtoimagefile/myimage.iso /mnt/image
```Then your mounted image will appear in /mnt/image

For reading on it can be found [here]("http://lindesk.com/2007/05/how-to-mount-isomdf-images-in-linux/")

Regards,
~Jeff
i have a folder with a mds file and a mdf file.

folder> FALLOUT.mds
and  FALLOUT.mdf
how do i make the iso file? 
that way i can use brasero dick burner, and burn the iso

---

### Post by Melcar on 2009-11-06
Can't Brasero burn mdf/mds files?  I don't remember.  AcetoneISO allows you to convert images to ISO format as well.

---

### Post by crowdedelevator on 2009-11-06
well theres two files and it only let me choose one but not a second and they probably would be a waste. ill get  that program you mentioned

---

### Post by Melcar on 2009-11-06
What are the file sizes?  The actual image file of the game should be bigger than 100MB I would think.  Or you can try to mount the files and see which one has the game data.  Just create a folder on your desktop (or home folder) and use that as the mount point.

sudo mount -o loop -t iso9660 /<location of image file> /<folder you just created>

---

### Post by crowdedelevator on 2009-11-06
acetoneISO does not work. will not download from that rinkydink site, but since thats the case, i cant mount it

---

### Post by crowdedelevator on 2009-11-06
mdf file is 691.7 MB
mds file is 492 bytes
 so i now know the mdf file is the actual game, but i cant mount it. because i hav no mount program

---

### Post by Melcar on 2009-11-06
Try the getdeb site:

[http://www.getdeb.net/search.php?keywords=acetoneiso]("http://www.getdeb.net/search.php?keywords=acetoneiso")

---

### Post by Melcar on 2009-11-06
> **crowdedelevator said:**
> mdf file is 691.7 MB
mds file is 492 bytes
 so i now know the mdf file is the actual game, but i cant mount it. because i hav no mount program


The command should mount the file with no problems.  You just need to specify the location of the file and the where you want to mount it.

---

### Post by crowdedelevator on 2009-11-06
> **Melcar said:**
> Try the getdeb site:

[http://www.getdeb.net/search.php?keywords=acetoneiso](http://www.getdeb.net/search.php?keywords=acetoneiso)

got it, mounted it. now what? i opened install through wine yet it did nothing at all

---

### Post by Melcar on 2009-11-06
Do you have WINE configured yet?  Either run the WINE configuration from your GNOME menu or run winecfg from the terminal.  Usually it autoconfigures itself, but check that your drivers (CD-ROM, HDD) are being detected.  Also, change the application to run as Windows 98.  After that just run wine setup.exe from the terminal.

---

### Post by crowdedelevator on 2009-11-06
wine doesnt show the mount at all. and the fallout folder is empty on the configure file opener

---

### Post by Melcar on 2009-11-06
Under the Drive tab WINE will show your hard drives, CD ROMs, and other drives in your system.  Just make sure they all have the correct location.  AcetoneISO mounts the image on a virtual drive in you hard drive, so as long as WINE detects your HDD you're fine.  Once you mount the image you can simply double click on the setup file.  If that doesn't work you can try right clicking on the exe file, go to "Open with Other Application" and look for "Wine Windows Program Loader".  Alternatively you can always run it from a terminal:

```
wine /<location of file to run>/setup.exe
```

---

### Post by crowdedelevator on 2009-11-06
[http://i858.photobucket.com/albums/ab143/thecrowdedelevator/Screenshot-1-1.png](http://i858.photobucket.com/albums/ab143/thecrowdedelevator/Screenshot-1-1.png)
this is the mounted fallout folder
[http://i858.photobucket.com/albums/ab143/thecrowdedelevator/Screenshot-1.png](http://i858.photobucket.com/albums/ab143/thecrowdedelevator/Screenshot-1.png)
this is wine configuration screen. and the cursor is over the mounted fallout 

figured these pics might help you get a visual.

---

### Post by Melcar on 2009-11-06
Simply double clicking on the .exe file should do it.

---

### Post by crowdedelevator on 2009-11-06
> **Melcar said:**
> Simply double clicking on the .exe file should do it.
all it does is go into the console dos esque window woth the black background, and it says not enough something, whilst flashing on and off once.
it just flashes once and closes

---

### Post by Melcar on 2009-11-06
Did you manage to get it working?

---

### Post by crowdedelevator on 2009-11-08
nope. i try over and over and im missing the master data. any ideas? it asks for the disk to be in the tray and i made a data disk and it was a fail.

---

### Post by Melcar on 2009-11-08
Maybe the image file you have is corrupted/wrong?

---

### Post by crowdedelevator on 2009-11-08
[LIST]
[*]i figured so i just deleted it. i kept sending you msgs but no avail.
[/LIST]
im having such an off linux day its giving me a head ache hahaha

---

### Post by clearscreen on 2009-11-09
> **crowdedelevator said:**
> well theres two files and it only let me choose one but not a second and they probably would be a waste. ill get  that program you mentioned

Maybe for next time: That's not a problem :) It's kind of like cue and bin. You simply select the cue file which contains the name of the bin and some other information. It will properly burn it to when you select that single file.

---

