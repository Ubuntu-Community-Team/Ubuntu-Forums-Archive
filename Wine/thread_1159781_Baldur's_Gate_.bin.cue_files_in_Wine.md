---
title: "Baldur's Gate .bin/.cue files in Wine"
date: 2009-05-15
forum: Wine
---

### Post by Alex J. on 2009-05-15
Hi,

This involves Wine a little bit, but I thought it was best posted here...sorry if it's in the wrong place. 

I have a set of .bin/.cue files for 6 CDs (Baldur's Gate I) and I was wondering how to get it up and going to use in Wine...I literally have no idea. I know that you would use alc120 or Daemon tools in Windows...but what do linux people do to get this going?

Thanks!

---

### Post by kostkon on 2009-05-15
You can do the same thing in Ubuntu, to mount them that is. You can use *AcetoneISO* for this.

You can download it from [*getdeb.net*]("http://www.getdeb.net/app/AcetoneISO").

---

### Post by wolfyking2 on 2009-05-15
Or you could use this script for mounting

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

and this script for unmounting ```
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
Make an empty file and put these codes in the empty file.  They should become an executable text file.  If you need to know were to put them, put them in /.gnome2/nautilus-scripts/.  Then, make the files executable, and voila!  When you right click an .iso, then their should be a thing called scripts, and their schould be mount iso, and unmount iso.  Oh, and call the empty files Mount Iso and Unmount Iso.

---

