---
title: "Mount - UnMount Nautilus Action Script (Ubuntu 11.04+)"
date: 2011-10-09
forum: Tutorials
---

### Post by GlennLChugg on 2011-10-09
Seems everybody in Linux was unable to provide us with a "working" ISO  Mounter now they changed the gksudo, so I just wrangled it until I made  one:

   	 	```
#!/bin/bash # mount  BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS` MNTDIR="$HOME/mnt/$BASENAME" INNAME="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"  if [ -d "$MNTDIR" ]; then gksudo -s "umount "$MNTDIR"" rmdir "$MNTDIR" exit 0 fi  mkdir -p "$MNTDIR"  if gksudo -s "mount -o loop "$INNAME""$MNTDIR"" then nautilus "$MNTDIR" --no-desktop exit 0 else gksudo -s "umount "$MNTDIR"" rmdir "$MNTDIR"  zenity --error --title "Mounter" --text "Cannot mount $INNAME"  exit 1 fi
``` 
The trick with the new gksudo is it can only execute one command  or call a script after it's allowed. So I simply use the users own home  folder to mount to (read only) "~/mnt/", I also removed the CD emulation  so you can now mount UDF's or VHD's, pretty much anything can be  mounted with it.

Just save the above code to "Mount - UnMount", go into it's properties  and make it Executable then place it in  "/home/glenn/.gnome2/nautilus-scripts/", where glenn is your own users  name.

---

