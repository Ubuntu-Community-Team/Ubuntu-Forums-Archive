---
title: "Simple BASH script to use rsync for local USB backup"
date: 2009-03-05
forum: The Cafe
---

### Post by kyouens on 2009-03-05
Hi everyone,

I wrote a very simple bash script to keep me from having to re-learn rsync every time I want to make a change to my backup scheme.  I'm using it to backup my home directory to an external USB drive attached to my 8.10 Thinkpad.  I have it set up to run as a cron job every night.

It's nothing fancy, but with a little modification, somebody else might find it useful:

```

#!/bin/bash

################################
# A very simple bash script to help build an rsync command to backup to a local directory.
# Written for my Ubuntu 8.10 with an external USB disk.
# Replace the options below with ones suitable to your system.
# Make sure your user has write permissions for the backup directory.
# Use at your own risk.
#
# Kenny Youens 3/4/09

TARGETPATH="/media/Shakespeare" 			#Backup volume mount point (no trailing slash).
TARGETDIR="/Backup/Nucleus/" 				#The backup directory (use trailing slash).
SOURCEDIR="/home/kyouens/"				#Source directory (use trailing slash).
EXC_FROM="/home/kyouens/.scripts/backup_exclude.txt"	#Set this if you want to use an exclusion file.
EXCLUDE_01=".gvfs" 					#You want to leave this here if you're using a new GNOME.
EXCLUDE_02=""						#To exclude an additional directory enter it here.
EXCLUDE_03=""						#To exclude an additional directory enter it here.
EXCLUDE_04=""						#To exclude an additional directory enter it here.
EXCLUDE_05=""						#To exclude an additional directory enter it here.
PARAMS="-arvzh --delete"				#Rsync arguments.  These presets are good for a routine backup.
LOGGING="Y"						#To disable logging set this to N.
LOGDIR="/home/kyouens/.scripts/logs/"			#Directory to contain log files.
DRYRUN="Y"						#Set this to N to write changes (otherwise rsync is simulated).
ZENITY="Y"						#Turn on simple Zenity notification (if you have Gnome).
################################

# Turn on basic error catching.
set -e
set -u

# Ensure that backup media is mounted
if [ ! -e $TARGETPATH ]; then
	echo "$TARGETPATH is not mounted.  Backup cannot proceed."
	if [ "$ZENITY" = "Y" ]; then
		zenity --notification --window-icon="warning" --text="Rsync backup directory $TARGETPATH is not mounted.  No backup was performed." &
	fi
	exit
fi

# Put the rsync command parameters together
ARGUMENTS="$PARAMS"
if [ "$EXC_FROM" != "" ]; then
	ARGUMENTS="$ARGUMENTS --exclude-from $EXC_FROM"
fi
if [ "$EXCLUDE_01" != "" ]; then
	ARGUMENTS="$ARGUMENTS --exclude $EXCLUDE_01"
fi
if [ "$EXCLUDE_02" != "" ]; then
	ARGUMENTS="$ARGUMENTS --exclude $EXCLUDE_02"
fi
if [ "$EXCLUDE_03" != "" ]; then
	ARGUMENTS="$ARGUMENTS --exclude $EXCLUDE_03"
fi
if [ "$EXCLUDE_04" != "" ]; then
	ARGUMENTS="$ARGUMENTS --exclude $EXCLUDE_04"
fi
if [ "$EXCLUDE_05" != "" ]; then
	ARGUMENTS="$ARGUMENTS --exclude $EXCLUDE_05"
fi
if [ "$LOGGING" = "Y" ]; then
	ARGUMENTS="$ARGUMENTS --log-file=$LOGDIR$(date +%a)_rsync.log"
fi
if [ "$DRYRUN" != "N" ]; then
	ARGUMENTS="$ARGUMENTS -n"
fi

# Run the command
rsync $ARGUMENTS $SOURCEDIR $TARGETPATH$TARGETDIR
if [ "$ZENITY" = "Y" ]; then
zenity --notification --window-icon="info" --text="Rsync backup to $TARGETPATH complete." &
fi

```

---

### Post by randyklein99 on 2009-04-30
Very nice.  I'm going to try this tonight.  Thanks for sharing.

---

### Post by JohnFH on 2009-04-30
Nice one.  One thing I noticed though is that it will fail if there's a space in the file or path name.  This caught me out before.

---

