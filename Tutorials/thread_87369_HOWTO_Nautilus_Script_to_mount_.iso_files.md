---
title: "HOWTO: Nautilus Script to mount .iso files"
date: 2005-11-07
forum: Tutorials
---

### Post by animacide on 2005-11-07
I recently found a nautilus shell script on an older post to the forum that could mount .iso files, but it couldn't handle spaces in filenames or mount more than one file at once.  After some struggle I've come up with these scripts which handle multiple concurrent mounts and filenames with spaces.  You'll want to save these under ~/.gnome2/nautilus-scripts/ and make them executable:

Mount:
```
#!/bin/bash
#
# nautilus-mount-iso

gksudo -u root -k /bin/echo "got r00t?"

sudo mkdir /media/"$*"

if sudo mount -o loop -t iso9660 "$*" /media/"$*"
then
        if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted.
        
        Open Volume?"
        then
                nautilus /media/"$*" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$*"
        zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
        exit 1
fi

```

Unmount:
```
#!/bin/bash
#
for I in "$*"
do
foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`

sudo umount "$I" && zenity --info --text "Successfully unmounted /media/$I/" && sudo rmdir "/media/$I/"
done
done
exit0

```

To use either one just right click on the .iso file and use scripts -> mount.  Hope someone finds this useful.  Does anyone know if there's a way to make nautilus just unmount by right clicking on the volume icon on the desktop and selecting unmount volume?

---

### Post by manicka on 2005-11-08
I have added these scripts to the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Nautilus_Scripts")

---

### Post by Darrena on 2005-11-12
Great script man!  Thank you for posting it!

---

### Post by magnusbb on 2005-11-13
One problem with this script, is, that if it is not possible to mount the iso file, it still creates a directory in /media. And it is not deleted. This can lead to heavy "clutter" after a while.

---

### Post by DaBruGo on 2005-11-18
I am going to see if I can use this to get a LIVE USB setup working that we are trying in thread 71567



DAVE

---

### Post by RattyMan on 2005-11-26
This doesn't work with any ISO file that is outside your home directory, other than that, great script

---

### Post by -DarkMind- on 2005-12-13
great script!  thanks :D

---

### Post by domino on 2005-12-14
Great little script! Is there a way to modify the ISO contents if locally mounted? 

RattyMan, I can, and I can even mount an ISO stored in my ntfs partition. Do you have root enabled?

---

### Post by animacide on 2005-12-22
Just wanted to let everyone know that I've updated the mounting script to be more error tolerant.  Now if an error occurs it tells you and it cleans up after itself by removing the directory in media.  I also borrowed an idea from another thread where Gandalf added optional nautilus open.  Hope this helps.  I may also try to convert this into a Nautilus Actions style script so it only shows up on the context menu of appropriate .iso files.

---

### Post by animacide on 2005-12-22
[QUOTE=domino]Great little script! Is there a way to modify the ISO contents if locally mounted?[/QUOTE]

Unfortunately, I don't think the loopback device allows for this.  I think you would have to copy the contents or extract it with fileroller, and then use mkisofs or nautilus' built in burning to make a new iso.

---

### Post by AgenT on 2005-12-22
If all else fails, you could try a symlink.

---

### Post by maxdevis on 2006-01-29
what's a symlink?

---

### Post by maxdevis on 2006-01-29
is it possible to make it that when the icon of the mounted iso appears on my desktop, i can unmount by letting the script run on the icon of the desktop?


thanks

---

### Post by RaptorRaider on 2006-01-29
Why not also make a script to mount .nrg's and .bin/.cue's?

---

### Post by animacide on 2006-01-31
[QUOTE=RaptorRaider]Why not also make a script to mount .nrg's and .bin/.cue's?[/QUOTE]

Unfortunately linux can't do that (correct me if I'm wrong).  You would need to convert the .nrg or .bin/.cue files to .iso and then work from there.  You can use nrg2iso & bchunk (Both in Synaptic).

---

### Post by RaptorRaider on 2006-02-01
[QUOTE=animacide]Unfortunately linux can't do that (correct me if I'm wrong).[/QUOTE]
Linux can actually do that, unfortunately only a few know how.

A few months ago I downloaded a huge .nrg file and successfully mounted it after Googling for many, too many hours really.
Instead of mounting with "iso9660" you're supposed to type "type2978" or something like that - I'm afraid I don't remember exactly.

Would anyone with more knowledge about this subject be so kind to help us here?

---

### Post by tr4veler on 2006-02-03
The scripts wheren't working for me under Dapper.  Turns out gksudo was seg faulting.  Pulling out the ```
-u root -k
``` fixed that.

I also found a mount-iso 0,9,1 for KDE that claims to handle iso, bin, cue, xdvdfs, nrg but, haven't looked too far into it yet.

Questions...

How can I unmount by right clicking on the desktop icon instead of the orginal iso?

Can the desktop icon be a cd instead of a hd?

---

### Post by mustang on 2006-02-03
Great script. Thank you for taking the time to write it.

---

### Post by robert_pectol on 2006-02-03
Great scripts!  Thanks.
[QUOTE=tr4veler]Questions...

How can I unmount by right clicking on the desktop icon instead of the orginal iso?

Can the desktop icon be a cd instead of a hd?[/QUOTE]
I recently wrote a similar script for Nautilus which handles both mounting and unmounting of images in the same script.  It also allows you to unmount the image by right-clicking on the desktop icon or the image itself.  It's supposed to support .nrg files but that functionality is currently untested... Anyone care to test it and report back?  If so, let me know and I'll post it to a new thread.

And yes.  You can change the desktop icon for the mounted image.  Simply mount it as normal and once the default icon for it appears, simply right-click it and select, "Properties" from the menu.  In there you can select a custom icon for it.  However, you'll have to do it on a per-image basis since the change won't be applied across the board.  I did notice that selecting a custom icon for a particular image is persistant though.

---

### Post by tr4veler on 2006-02-03
Cool script.  Works good so far.  I'm looking for a nrg to test it with, but mount and unmount work great so far.

---

### Post by engla on 2006-02-05
Great script, very useful.

But why pollute your scripts menu, when we can do this context-sensitive?

Put the scripts in a local place, like ~/bin or ~/scripts or wherever you like. Select an iso, choose properties, and look at the Open With.. tab.
Click add, click 'use custom command' and click browse. Select your Mount script, then repeat this with your Unmount script. Now you have in your context menu whenever you select .iso files, an option to mount or unmount!

---

### Post by cutOff on 2006-02-06
Nice and useful. Just works.

Thanks

---

### Post by ounas on 2006-02-28
Thanks I needed this .

-Ounas \\:D/

---

### Post by adamkane on 2006-03-16
How to mount ISO BIN/CUE IMG/CCD NRG:
[http://ubuntuforums.org/showthread.php?t=144236](http://ubuntuforums.org/showthread.php?t=144236)

---

### Post by Nightwish on 2006-03-20
No, those are defective :P
gksu segfaults with -k root, i don't think it needs it anyway. also, it attempted for me to create directories with the full path, which is not what i want. so, here's a quick fix and a cleanup.
Mount:
```
#!/bin/bash
#
# nautilus-mount-iso

gksudo -k /bin/echo "got r00t?"
BASENAME=`basename "$*"`
sudo mkdir /media/"$BASENAME"
echo $BASENAME

if sudo mount -o loop -t iso9660 "$*" /media/"$BASENAME"
then
        if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted.

        Open Volume?"
        then
                nautilus /media/"$BASENAME" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$BASENAME"
        zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"
        exit 1
fi


``` 
Unmount:
```
#!/bin/bash
#
BASENAME=`basename "$*"`
foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
sudo umount /media/"$BASENAME" && zenity --info --text "Successfully unmounted /media/$BASENAME/" && sudo rmdir "/media/$BASENAME/"

``` 
cleaned up the unmount code, BTW.

---

### Post by jon_gunnar on 2006-03-22
[QUOTE=tr4veler]The scripts wheren't working for me under Dapper.  Turns out gksudo was seg faulting.  Pulling out the ```
-u root -k
``` fixed that.

[/QUOTE]

Thanks for this.Works well now.
And thanks a lot to the original scripter too of course.

---

### Post by chollis888 on 2006-07-16
Just wanted to say thanks to the original poster, tried this on iso's and nrg's worked perfect don't have bin/cue's to try.:mrgreen:

---

### Post by orb9220 on 2006-07-16
Well the mount script from Nightwish works but the unmount doesn't

#!/bin/bash
#
BASENAME=`basename "$*"`
foo=`gksudo -m "enter your password for root terminal access" /bin/echo "got r00t?"`
sudo umount /media/"$BASENAME" && zenity --info --text "Successfully unmounted /media/$BASENAME/" && sudo rmdir "/media/$BASENAME/"

Any Idea's or is it something stupid I don't understand which is possible and still trying to grasp the whole permissions thing.

Any Help is always appreciated.

---

### Post by orb9220 on 2006-07-16
Sidenote:
sudo umount /media/FIREWALL.iso
from the term works fine

---

### Post by Aragorn on 2006-07-17
Hi at all! 

I've patched the iso mounter...now it can mount a file from every position in the home directory and it creates a mount point without the .iso extension. 

#!/bin/bash
# mount

gksudo -k /bin/echo "got r00t?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo mkdir "/media/$BASENAME"

zenity --info --title "ISO Mounter" --text "$BASENAME e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"


if sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME"
then
        if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted. Open Volume?"
        
          then
                nautilus /media/"$BASENAME" --no-desktop
        fi
        
        exit 0
else
        sudo rmdir "/media/$BASENAME"
        
        zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"
        
        exit 1
fi



#!/bin/bash
# unmount

gksudo -k /bin/echo "got r00t?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo umount "/media/$BASENAME"

sudo rmdir "/media/$BASENAME"

zenity --info --text "Successfully unmounted /media/$BASENAME"

exit 0

---

### Post by chollis888 on 2006-07-17
I used these scripts, posted by animacide, with no problems at all in dapper.
 
Mount:
 
 
 
 

```
 [LEFT]#!/bin/bash[/LEFT]
 
 
 
 
 
[LEFT]#[/LEFT]
  
[LEFT]# nautilus-mount-iso[/LEFT]
  
 
[LEFT]gksudo -u root -k /bin/echo "got r00t?"[/LEFT]
  

[LEFT]sudo mkdir /media/"$*"
 
[LEFT]if sudo mount -o loop -t iso9660 "$*" /media/"$*"
then
   if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted.[/LEFT]
  
[LEFT]   Open Volume?"
   then
           nautilus /media/"$*" --no-desktop
   fi
   exit 0
else
   sudo rmdir /media/"$*"
   zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
   exit 1
fi[/LEFT]
  
 
 

[/LEFT]
 
 
 

```  
 
[LEFT]Unmount:[/LEFT]
  
 
 
 
 

```
 [LEFT]#!/bin/bash[/LEFT]
 
 
 
 
 
[LEFT]#[/LEFT]
  

[LEFT]for I in "$*"
 
[LEFT]do

foo=`gksudo -u root -k -m "enter your password for root terminal
[LEFT]access" /bin/echo "got r00t?"`[/LEFT]
  
[LEFT]sudo umount "$I" && zenity --info --text "Successfully unmounted /media/$I/" && sudo rmdir "/media/$I/"
done
done
exit0[/LEFT]
  
 
 

[/LEFT]
 
 
 
 

[/LEFT]
 

```  
 
 
 
 
 
 
 
 
 
 
 
 
 
Here is a step by step.
 
First open a terminal and do a:
```
sudo gedit ~/mount-iso
``` I used root to create the files so there was no conflicts later. Then in the empty file I cut and pasted the mount script and saved with crtl-s and exit.
 
Then the same for Unmount script:
```
sudo gedit ~/unmount-iso
``` Then in this empty file cut and paste the unmount script. Save with 
crtl-s and exit.
Ok next to make them executable do a:
```
sudo chmod +x ~/mount-iso
``` and then:
```
sudo chmod +x ~/unmount-iso
``` Ok now to put them in the right spot:
```
sudo mv ~/mount-iso ~/.gnome2/nautilus-scripts/
``` 
next:
```
sudo mv ~/unmount-iso ~/.gnome2/nautilus-scripts/
``` 
And thats it.
Now to use the new scripts find and .Iso or .Nrg anywhere you have it. I've mounted both types from my ntfs storage partition with no problems. Just right click the image file go to scripts and then choose mount or unmount. Could'nt get any better than that. Goodluck and if you need more fuctions or just want to try some other scripts check the [UDSF Here]("http://doc.gwos.org/index.php/Mount_ISO_script").
 
Edit: It doesn't work with img's on the desktop.

---

### Post by Aragorn on 2006-07-17
The animacide's script can "only" mount iso / nrg image in the home directory...if you put your iso file in ~/Desktop for example you can't mount it...

Bye

Aragorn

---

### Post by chollis888 on 2006-07-18
Well animacide's script is the only one I use and it mounts my images from everwhere but the desktop strange. And that even includes my windows partition. Sorry yours did'nt work like that  but I just did it last nite maybe it's been edited since you used it, I don't know, as I said I just did it.  And decided  to post the results and the way I did it. Give it another go, ;)    However I did just find there's this one nrg I cant mount on my ntfs partion, but all the rest are fine.

---

### Post by Aragorn on 2006-07-18
Really strange. Rattyman has the same problem and the $* in the original script doesn't get the right path in all the directory. Can you try to put an iso image in the ~/Desktop direcoty and mount it?

Bye

Aragorn

---

### Post by chollis888 on 2006-07-18
Yea, I dont get it either. Maybe it has something to do with the mount icon having the exact same name as the image does, and it causes some conflict, is what I'm guessing. I'm no programmer but at first site that seems to be it. I tried the other script that suppose to take the .iso part off the mounted image icon with no success. O well I'll just use the home folder, its less work when I'm in terminal anyway "~/".:-k Hey wait, just thought of something else, I could change the mount directory itself from /media/ to /mnt/ that would probably solve it. O well it works for what I need it for.

---

### Post by utnubu001 on 2006-07-18
this is great cause most of my movies are .iso
and i could only mount them under windoze

thanks mate

btw vlc somehowe manages to play isos without having to mount them..

---

### Post by mirak63 on 2006-07-18
Hi,
I use something similar with nautilus actions and fuseiso instead of mountloop. The advantage is that you don't need a sudo.

add yourself in fuse group
```
sudo adduser $USER fuse
```
load fuse module do only once
```
modprobe fuse
```
make fuse load on startup you don't need modprobe fuse the next time
```
echo fuse >> /etc/modules
```
logout and relog to gnome (it's needed to enter the group)
```
sudo apt-get install fuseiso fuse-utils
```
Then import the *.schemas file with nautilus actions.
Put the scripts fuseisomount and fuseisumount in ~/bin/
```
cp fuseismount fuseisoumount ~/bin
```
chmod them executable with
```
cd ~/bin
chmod u+x fuseismount fuseisoumount
```

Then in nautilus after maybe a restart of nautilus, you right click on an iso, and do mount.
The iso will be mounted in /tmp/nameoftheiso/
probably /media/ would be a better place, you can change the script.

To unmount, left click the iso and do unmount.

The name of the actions are in french, "monter" = "mount", "démonter" = "unmount", you can rename them.

:-D

edit:

To have the iso in /media, do
sudo chmod o+rwt /media/
This gives the bahavior of /tmp to /media, users can create anything they want but can not delete others files.
I realised that in /media the drive_mount applet show the iso unlike in /tmp I think.

---

### Post by adamkane on 2006-07-24
I've already written a Nautilus-script to mount ISO files. It can handle special characters, and can mount ISO files located in any directory.

How to mount ISO BIN/CUE IMG/CCD NRG:
[http://ubuntuforums.org/showthread.php?t=149963](http://ubuntuforums.org/showthread.php?t=149963)
[http://ubuntuforums.org/showthread.php?t=144236](http://ubuntuforums.org/showthread.php?t=144236)

---

### Post by chollis888 on 2006-08-04
> **Nightwish said:**
> No, those are defective :P
gksu segfaults with -k root, i don't think it needs it anyway. also, it attempted for me to create directories with the full path, which is not what i want. so, here's a quick fix and a cleanup.
Mount:
```
#!/bin/bash
#
# nautilus-mount-iso
 
gksudo -k /bin/echo "got r00t?"
BASENAME=`basename "$*"`
sudo mkdir /media/"$BASENAME"
echo $BASENAME
 
if sudo mount -o loop -t iso9660 "$*" /media/"$BASENAME"
then
        if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted.
 
        Open Volume?"
        then
                nautilus /media/"$BASENAME" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$BASENAME"
        zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"
        exit 1
fi
 

``` 
Unmount:
```
#!/bin/bash
#
BASENAME=`basename "$*"`
foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
sudo umount /media/"$BASENAME" && zenity --info --text "Successfully unmounted /media/$BASENAME/" && sudo rmdir "/media/$BASENAME/"

``` 
cleaned up the unmount code, BTW.
 
 
Here's an easy fix to get rid of the .iso from mounted images.
Replace:
```
BASENAME=`basename "$*"`
```  
with:
```
BASENAME=`basename "${1%.*}"`
```  
That's just string chopping. It tells the shell to cut off anything after the (.).

Edit: The umount script does'nt work if the directory name does'nt have the .iso on it so here's the fix.

```
#!/bin/bash
#
ImgDir="${1%.*}"
for I in "$1"
do
foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`

sudo umount "$I" && 
zenity --info --text "Successfully unmounted /media/$I/" && 
sudo rmdir "/media/$ImgDir"
done
done
exit0

```

---

### Post by Josh_b on 2006-08-18
> **animacide said:**
> You'll want to save these under ~/.gnome2/nautilus-scripts/ and make them executable:

I'm new to Linux and this is probably a stupid question, but how do I make the file an executable?

Also, is there any script to be able to open .ccd, .img and the other types of image files?

---

### Post by Josh_b on 2006-08-18
> **Josh_b said:**
> I'm new to Linux and this is probably a stupid question, but how do I make the file an executable?

Correction. It **is** a stupid question.](*,)  Figured it out anyway.

---

### Post by bluntu on 2006-08-24
How do you install those scripts? Where do I put them?

//nevermind.

---

### Post by Jose Catre-Vandis on 2006-08-27
> **robert_pectol said:**
> Great scripts!  Thanks.

I recently wrote a similar script for Nautilus which handles both mounting and unmounting of images in the same script.  It also allows you to unmount the image by right-clicking on the desktop icon or the image itself.  It's supposed to support .nrg files but that functionality is currently untested... Anyone care to test it and report back?  If so, let me know and I'll post it to a new thread.

And yes.  You can change the desktop icon for the mounted image.  Simply mount it as normal and once the default icon for it appears, simply right-click it and select, "Properties" from the menu.  In there you can select a custom icon for it.  However, you'll have to do it on a per-image basis since the change won't be applied across the board.  I did notice that selecting a custom icon for a particular image is persistant though.

Robert Pectol
My Website: [http://rob.pectol.com/](http://rob.pectol.com/)
Nautilus Scripts, etc: [http://rob.pectol.com/myscripts](http://rob.pectol.com/myscripts)


I tried just about every other script on this forum to do this, and Rob, yours is the only one that actually worked first time. Many thanks.

---

### Post by robert_pectol on 2006-08-28
> **Jose Catre-Vandis said:**
> I tried just about every other script on this forum to do this, and Rob, yours is the only one that actually worked first time. Many thanks.

You're very welcome!  :)

---

### Post by Josh_b on 2006-08-29
so is there any way to read other image files (.ccd, .img, .mdf/.mds, etc), or do I have to convert them to .ISO's?

---

### Post by rufinojr54 on 2006-10-28
Hi! Anyone can tell me how to do this? How do i make the scripts executable? What i did is created two files and copied the scripts to them. Then restart the nautilus. When i right click on the iso file, nothing in the menu that says script>mount. Please help. ](*,)

---

### Post by HAARP on 2006-10-29
> **Josh_b said:**
> so is there any way to read other image files (.ccd, .img, .mdf/.mds, etc), or do I have to convert them to .ISO's?

Look at my signature to see how to mount those.

> **rufinojr54 said:**
> Hi! Anyone can tell me how to do this? How do i make the scripts executable? What i did is created two files and copied the scripts to them. Then restart the nautilus. When i right click on the iso file, nothing in the menu that says script>mount. Please help. ](*,)

In Nautilus, right click on it and select properties, permissions and there "allow executing"

---

### Post by rickatnight11 on 2007-01-09
This is exactly what I needed!  Thanks so much, works wonderfully.

---

### Post by gkokaisel on 2007-03-04
Thanks for the script! (Though it would be even more perfect if one could just unmount from the desktop)

---

### Post by tlacuache on 2007-03-08
I ran across [this thread]("http://www.ubuntuforums.org/showthread.php?t=276743") which explains how to install CDemu and create nautilus scripts for using it to mount and unmount images. 

This seems to be a better choice than simply using a loopback devices because it supports more image types, and also allows you to mount images with multiple tracks.

-SG

---

### Post by pingpongboss on 2007-03-09
> **Jose Catre-Vandis said:**
> I tried just about every other script on this forum to do this, and Rob, yours is the only one that actually worked first time. Many thanks.

same for me. I love how i can just run the same script on the desktop icon and have it unmount.

---

### Post by Nehvrook on 2007-05-18
Great script animacide, works a treat. Thanks :)

---

### Post by brian.freelancer on 2007-05-19
I've been running around the internet for a solution to this and I finally found one that worked (for me) :)

The thing is made for Debian, though and, as a no0b, about the only thing I know is that Ubuntu is based on Debian. <correct the n0ob if necessary> :)

[http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html)

I found a bit of a problem with this line, though:

    “sudo mv ~/mount-iso ~/.gnome2/nautilus-scripts/”

Which should probably be:

    “sudo mv ~/mount.sh ~/.gnome2/nautilus-scripts/”

hmmm...maybe I was meant to change the filename...anyway, it worked! woohoo! I hope this helps someone.

---

### Post by thexfactor_sid on 2007-06-30
an awesome one man.!

---

### Post by slasherx2 on 2007-08-11
Haha, awesome script, will save me remembering the full command to mount an ISO. Thanks :D

---

### Post by hotdoog on 2007-10-18
Hi, this (original script) didn't work for me at first. Before I read the entire thread I hacked something together that worked better for me - using pushd and popd, plus mkdir -p and rmdir -p so the directories worked. Then I discovered that others had better solutions already. I haven't tested those yet, but I'll probably get the one that can read space characters etc...

Anyways the biggest problem i was having that the script wasn't showing in the nautilus scripts menu. This was weird because I had the -x permissions correctly set.

Anyways, my edited scripts showed up there but not the original. My only guess about the change was that the 2nd line with the # -then blank- was changed to #with my notes in it. Could it be the # -blank- line was screwing it up?

I'm running dapper BTW, perhaps that is a bug to dapper?

---

### Post by Gen2ly on 2007-10-19
I liked engla's idea, just using it as a bash script.

```
#!/bin/bash
#
# nautilus-mount-iso

gksudo -k /bin/echo "got r00t?"

if sudo mount -o loop -t iso9660 "$*" /media/iso; then
    echo "mounted"
    nautilus /media/iso; else
    echo "mount error"
fi
```

Associate the bash script to the regular .iso and now just double-clicking will open it.

---

### Post by franzag on 2007-10-23
nice scripts for mount DVD data, i discover that totem actually support DVD Isos!, just left click open with  totem, and play lol
Ubuntu 7.10

---

### Post by altonbr on 2007-11-05
I've added the scripts to the specified location and then ran
```
$ killall nautilus
```
but the "scripts" menu still doesn't come up on a right-click. What am I doing wrong?

Edit: I didn't make them executable. Sorry.

---

### Post by LordKelvan on 2008-01-02
Hi:

I would just like to say thanks to all the people who posted different versions of the scripts.  In particular, thanks to:

[LIST=1]
[*]animacide (original creator)
[*]Nightwish (added the ability to extract only the filename, which was something I wanted to do but my newbness prevented)
[*]chollis888 (added the ability to remove the ".iso" from the mount directory, which was something I wanted to do, but again my newbness prevented)
[/LIST]

I have one small request that would make this solution even more perfect: is it possible to have a menu entry which automatically changes from "mount" to "unmount" depending on whether you have previously mounted the ISO?

Edit: I previously mentioned that I was adding the scripts as custom commands under the "Open With..." submenu because I wanted the scripts to appear for ISO files only.  Today, I found out that Nautilus -Actions allows for the same behaviour.  When you are adding a new action, you can specify the conditions under which your action will appear in the context menu (i.e. the menu that appears when you right-click something).  You can do it based on filename (e.g., "*.iso" for our particular case) or on MIME type (e.g., "application/x-cd-image" for our particular case).  Of course, my original request still stands.

---

### Post by goodtimetribe on 2008-01-27
Ok guys. I don't use gnome and I don't use nautilus, and so i don't bother installing zenity... but i do have kdialog installed in kde, so i modified the scripts to work with kubuntu and kde... only i can't get the unmount to work....i've got it started, so i'd appreciate some kind soul to find my error...thanks

here's my working **mount.sh**

```

#!/bin/bash
# mount
# script was originally written for gnome and nautilus
# found http://www.ubuntuforums.org/showthread.php?t=87369&page=3
# modified to support kde/kubuntu by Joshua Kersey / goodtimetribe
 
kdesu /bin/echo "got r00t?"

BASENAME=`basename $1`

sudo mkdir "/media/$BASENAME"

kdialog --title "ISO Mounter" --msgbox "$BASENAME e $1"


if sudo mount -o loop -t iso9660 $1 "/media/$BASENAME"
then
if kdialog --title "ISO Mounter" --yesno "$BASENAME Successfully Mounted. Open Volume?"

then
konqueror /media/"$BASENAME" 
fi

exit 0
else
sudo rmdir "/media/$BASENAME"

kdialog  --error "Cannot mount $BASENAME!" --title "ISO Mounter" 

exit 1
fi


```

Here's my **unmount.sh**. I didn't think it worked, but I think I found my error. Try it and make any modifications you think necessary.

```

#!/bin/bash
# unmount
# script was originally written for gnome and nautilus
# found http://www.ubuntuforums.org/showthread.php?t=87369&page=3
# modified to support kde/kubuntu by Joshua Kersey / goodtimetribe

kdesu /bin/echo "got r00t?"

BASENAME=`basename $1`

sudo umount "/media/$BASENAME"

sudo rmdir "/media/$BASENAME"

kdialog --info --text "Successfully unmounted /media/$BASENAME"

exit 0

```

---

### Post by Argus on 2008-02-07
Thanks this is a great set of scripts

---

### Post by doorknob60 on 2008-02-09
Worked great fir me :) Now less wasting my blank CD's :D

---

### Post by liviopl on 2008-03-01
gksudo is very distro-independent... NOT.

And next thing is wrong - usage of zenity. Intrusive dialogs... Use libnotify instead.

---

### Post by karq on 2008-03-12
Greate scripts, but I have one problem I cant unmount them. It says successfully unmounted but the folder is still in the media folder and contains that iso and I cant delete that mounted iso too.

---

### Post by phantom74 on 2008-04-04
> **Nightwish said:**
> No, those are defective :P
gksu segfaults with -k root, i don't think it needs it anyway. also, it attempted for me to create directories with the full path, which is not what i want. so, here's a quick fix and a cleanup.
Mount:
```
#!/bin/bash
#
# nautilus-mount-iso

gksudo -k /bin/echo "got r00t?"
BASENAME=`basename "$*"`
sudo mkdir /media/"$BASENAME"
echo $BASENAME

if sudo mount -o loop -t iso9660 "$*" /media/"$BASENAME"
then
        if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted.

        Open Volume?"
        then
                nautilus /media/"$BASENAME" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$BASENAME"
        zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"
        exit 1
fi


``` 
Unmount:
```
#!/bin/bash
#
BASENAME=`basename "$*"`
foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
sudo umount /media/"$BASENAME" && zenity --info --text "Successfully unmounted /media/$BASENAME/" && sudo rmdir "/media/$BASENAME/"

``` 
cleaned up the unmount code, BTW.



great job man, now it worked for me, great simple script!!!

---

### Post by Endolith on 2008-04-24
There is a utility called gISOmount in Synaptic for this.  I'm going to try it as soon as my upgrade torrent finishes. :)

---

### Post by igpf on 2008-06-13
this is great, what a time saver... being a noob and all.
thanks.

---

### Post by Kirizan on 2008-06-28
Wow, after all of this gISOmount is great.  Just install the package and run, I've mounted with it, but I haven't unmounted anything yet.  It seems to work very well so far though.  I'll post back after I try unmounting and see if there are any problems

---

### Post by blueyez on 2008-08-11
why install gisomount and / or other similar applications ? 
just because are ready for you desktop ?

command line is better :) owns !

---

### Post by Endolith on 2008-08-11
> **blueyez said:**
> why install gisomount and / or other similar applications ? 
just because are ready for you desktop ?

command line is better :) owns !

Because it's simpler and easier to remember than the cryptic command line, of course.

---

### Post by muks on 2008-09-08
I mounted an iso file using the following command:
```
 sudo mount -o loop -t iso9660 /home/mukul/Desktop/CBTNuggets/CBT1.ISO /mnt/iso/
```

Now how to unmount it??

---

### Post by rickatnight11 on 2008-09-08
```
sudo umount /mnt/iso
``` I believe.

---

### Post by muks on 2008-09-08
> **rickatnight11 said:**
> ```
sudo umount /mnt/iso
``` I believe.

This didn't work.

---

### Post by rickatnight11 on 2008-09-08
Hm, what output did you get?

---

### Post by niccholaspage on 2008-09-08
Thank you for this awesome Script!I can finally Mount without having to extract a ISO! Thanks a LOT.

---

### Post by stlouie65 on 2008-09-16
> **Aragorn said:**
> Hi at all! 

I've patched the iso mounter...now it can mount a file from every position in the home directory and it creates a mount point without the .iso extension. 

#!/bin/bash
# mount

gksudo -k /bin/echo "got r00t?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo mkdir "/media/$BASENAME"

zenity --info --title "ISO Mounter" --text "$BASENAME e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"


if sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME"
then
        if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted. Open Volume?"
        
          then
                nautilus /media/"$BASENAME" --no-desktop
        fi
        
        exit 0
else
        sudo rmdir "/media/$BASENAME"
        
        zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"
        
        exit 1
fi



#!/bin/bash
# unmount

gksudo -k /bin/echo "got r00t?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo umount "/media/$BASENAME"

sudo rmdir "/media/$BASENAME"

zenity --info --text "Successfully unmounted /media/$BASENAME"

exit 0

Did some simple deduction of your unmount script and came up with this. It works fine for me, it may help others.
CODE:
Unmount

#!/bin/bash
# unmount

sudo umount /media/*.iso
sudo rmdir /media/*.iso

zenity --info --text "Successfully unmounted media"

exit 0

---

### Post by johnswb on 2008-09-28
Great script.  

The only thing I didn't see was how to add the scripts to nautilus location and make them executable.  Noobs such as my self really needs this info.
This is how I did it, I'm not sure if this is the norm but it worked for me. 

**This created the file:**
```
sudo gedit ~/.gnome2/nautilus-scripts/Mount.pl
```

**This made it executable:**
```
sudo chmod +x ~/.gnome2/nautilus-scripts/Mount.pl
```


**This created the file:**
```
sudo gedit ~/.gnome2/nautilus-scripts/Unmount.pl
```

**This made it executable:**
```
sudo chmod +x ~/.gnome2/nautilus-scripts/Unmount.pl
```

After doing this I was able to use these AWESOME scripts!

---

### Post by BrentNewland on 2008-10-04
I've made one along the same lines, it's a single file solution (no separate mount and unmount, just unmounts anything at the mount point before loading) and it will let you write to the image as well. Also notifies you whether it mounted or not.

[http://ubuntuforums.org/showthread.php?t=52255](http://ubuntuforums.org/showthread.php?t=52255)

---

### Post by geezerone on 2008-10-21
I have tried some mount/unmount scripts but get error "Cannot Mount".

---

### Post by bandaidsrcool on 2008-10-31
how about.. for the super newbs.. someone makes a 'click here' button?
maybe right clicking & having the option to mount? i cant make sense of natalus junk & ubuntu should be more advanced than windows, not more of a pain. (not everyone wants to spend 2hrs learning how to install something)
~curious if ubuntu is just another way of making ppl *eat* countless hours.

---

### Post by dyous87 on 2009-02-03
I just found this script looking for a way to mount/ unmount .iso's without having to go manually through the command line every time. Thanks a lot, it works great and makes life much easier!

David

---

### Post by altonbr on 2009-02-04
> **dyous87 said:**
> I just found this script looking for a way to mount/ unmount .iso's without having to go manually through the command line every time. Thanks a lot, it works great and makes life much easier!

David

There is a program called 'archive mounter' in Ubuntu 8.10 Intrepid that has the exact same qualities as this script. It should appear when you right-click an ISO file.

---

### Post by dyous87 on 2009-02-04
Thank you!! That was dumb of me, I never even noticed it was there!

David

---

### Post by phoenix81000 on 2009-02-20
I tried the 8.10 mount script and it did not let me execute an .exe which was on the .iso disc.. tried it with this script (from 1st post) and worked perfectly. 

Iso was located in /media/disk/downs which is defiantly not my ~

---

### Post by altonbr on 2009-02-22
> **phoenix81000 said:**
> I tried the 8.10 mount script and it did not let me execute an .exe which was on the .iso disc.. tried it with this script (from 1st post) and worked perfectly. 

Iso was located in /media/disk/downs which is defiantly not my ~

Have you ran the file through the terminal?
aka
```
wine /media/disk/downs/file.exe
```
Maybe the file doesn't run through whatever version of wine you have?

---

### Post by SentientFluid on 2009-02-28
> **animacide said:**
> ```
if sudo mount -o loop -t iso9660 "$*" /media/"$*"
```

In the mount script I would recommend changing "iso9660" to "auto", like this:
```
if sudo mount -o loop -t auto "$*" /media/"$*"
```

The script wasn't able to mount an .iso that was ISO-13346 until I made that change.  Still seems to work fine for everything else.

---

### Post by wolfyking2 on 2009-05-09
Thank you very much for this script :)

---

### Post by dreamcarrior on 2009-05-10
I followed the instruction to place the script in ~/.gnome2/nautilus-scripts, but it does not work. Every time I got the zenity to show "Cannot Mount xxxxx.iso"

I separately execute the commands in the script, and I found that gksudo is not recognized.
sudo mount works, and I could mount the iso file. However, when put together as a script, it does not work. Does anyone know what is going on?

I have Gnome Desktop under Fedora Core 10. But I don't think there is much difference between Fedora and Ubuntu in terms of the automount script.

The code I used.
```
#!/bin/bash
#
# nautilus-mount-iso

# gksudo -u root -k /bin/echo "got r00t?"

mkdir ~/media/"$*"

if sudo mount -o loop -t iso9660 "$*" ~/media/"$*"
then
        if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted.

        Open Volume?"
        then
                nautilus ~/media/"$*" --no-desktop
        fi
        exit 0
else
        rmdir ~/media/"$*"
        zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
        exit 1
fi
```

---

### Post by Levo on 2009-06-10
Nice script, thanks. I have made some improvements to it, I may post it later.

---

### Post by qva5 on 2010-02-14
Nice scripts indeed. This is what called vivid community.

However my suggestion is to first try out solutions already embeded in your Ubuntu before creating new scripts, for something which has already been done and is supported.
The  bash scripts are great if you want to mount/unmount from command line, but if all you need is to have this in nautilus, it could be not worth the hassle.

As someone has already written, since 8.10 you can right click on image file and open it with **"archive mounter"**. If you need something more you could go with **gisomounter **or** cdemu**.

---

### Post by frumple on 2010-07-28
@qva5,

The main problem with archive mounter is that it doesn't result in a proper path, therefore nothing can be excecuted. 

CDEmu isn't on the main repositories and gISOmounter produces errors when run as user. 

The script is an elegant and compact solution, besides not having any dependencies.

@all,

Since most ISOs have long names and rarely more than one file needs to be mounted at the same time, I changed the script a little bit the scripts.

ISO Mount:```
#!/bin/bash

gksudo mkdir /media/ISO

if sudo mount -o loop,user,uid=1000,gid=100 -t auto "$*" /media/ISO
then
        if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted. 
	
Open Volume?"
        then
                nautilus /media/ISO --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/ISO
        zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
        exit 1
fi
```

Also with this script the volume is user manageable, meaning that you can unmount it just by right-clicking on the volume icon and selecting 'unmount', without the need for a specific script!

Regards,
Eduardo Ristow

---

### Post by malikjunaid on 2011-09-11
> **RattyMan said:**
> This doesn't work with any ISO file that is outside your home directory, other than that, great script

I just tried the scripts and it DOES work outside the home as well.

Cheers

---

### Post by yangxinle on 2011-09-12
Great little script! thank you very much....&#65306;P

---

