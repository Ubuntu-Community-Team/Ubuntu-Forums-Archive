---
title: "Ubuntu One u1conflict syncing headache"
date: 2011-04-12
forum: Ubuntu One (CLOSED)
---

### Post by raequin on 2011-04-12
Here's my story.  I like the idea of backing up my work via syncing on Ubuntu One.  There are tons of directories and small files that I, at one point, set to synchronize on Ubuntu One.  It didn't work very well for me, just couldn't get it figured out.  Then recently I tried again.  Deleted my online directories, stopped syncing my local directories, then set some sub-directories to sync on Ubuntu One.  I can't relate all the details, the gist is that I was trying to start over with my syncing.

Here's the result, and what I need help with now.  There are hundreds of files and directories on my computer with the new extension ".u1conflict".  I've decided to give up on Ubuntu One, I'll just manually archive these files.  There are no original copies of all these files, just the renamed versions.  How can I get them all back to the original names, i.e. remove the u1conflict extension?  Thanks.

---

### Post by duanedesign on 2011-04-13
Can you tell us what version of Ubuntu One you are/were using so we can look into this issue? This should not happen with Natty but might be an issue with older clients if you do not clear the metadata out.

Here is a script that will remove the .u1conflict from your files. It will also write to the terminal and save a text log of what it does so you know what and where everything is. The log file will be saved to ~/rename-u1conflict-files-rename.log (if you name the script according to the example below)

```

#!/bin/bash

set -e

DIR=${1:-.}

RENAME_LOG=~/rename-u1conflict-files.log

find "$DIR" -depth -name '*.u1conflict' | (
    while read FILE_PATH; do
        BASENAME="${FILE_PATH%.u1conflict}"
        TARGET="$BASENAME"

        COUNTER=0
        while [ -e "$TARGET" ]; do
            COUNTER=$(( $COUNTER+1 ))
            TARGET="$BASENAME.$COUNTER"
        done

        echo "$FILE_PATH:$TARGET" >> $RENAME_LOG

        mv -v "$FILE_PATH" "$TARGET"

    done
)
```

You can follow these commands download the script and run it to rename the U1conflict files:

```
wget http://people.canonical.com/~roman.yepishev/us/rename-u1conflict-files.sh
```

```
chmod +x rename-u1conflict-files.sh
```

```
./rename-u1conflict-files.sh
```

---

### Post by raequin on 2011-04-13
Thanks.

> Can you tell us what version of Ubuntu One you are/were using so we can look into this issue? This should not happen with Natty but might be an issue with older clients if you do not clear the metadata out.

The version installed is 1.2.2-Oubuntu2.  Do you want to tell me how to clear the metadata out?

---

### Post by duanedesign on 2011-04-15
You can clear out the old metadata with the following command.

make sure everything Ubuntu One is quit
```
u1sdtool -q; killall ubuntuone-login ubuntuone-preferences
```

Remove the folder with the metadata
```
sudo rm -rf ~/.local/share/ubuntuone
```

Start Ubuntu One and it will recreate the metadata. This may take a little bit.
```
u1sdtool -c 
```

If for some reason you still have an issue you can do a more thorough purge and reinstall by following[ these steps]("http://ubuntuforums.org/showpost.php?p=8146023&postcount=2"). This includes removing metadata, configuration files, and a complete reinstall of the application.

---

### Post by Rocky37 on 2011-04-29
I have been using Cloud One for some time and have had no issues with it -- until I updated to 11.04 yesterday.

Now I have u1conflicts all over the place.  I see this has been around for a few years and it has been suggested this issue would be gone in 11.04 -- guess what ---IT IS ALIVE AND WELL!  :evil:

---

### Post by Rocky37 on 2011-04-30
> **duanedesign said:**
> Can you tell us what version of Ubuntu One you are/were using so we can look into this issue? This should not happen with Natty but might be an issue with older clients if you do not clear the metadata out.

Here is a script that will remove the .u1conflict from your files. It will also write to the terminal and save a text log of what it does so you know what and where everything is. The log file will be saved to ~/rename-u1conflict-files-rename.log (if you name the script according to the example below)

```

#!/bin/bash

set -e

DIR=${1:-.}

RENAME_LOG=~/rename-u1conflict-files.log

find "$DIR" -depth -name '*.u1conflict' | (
    while read FILE_PATH; do
        BASENAME="${FILE_PATH%.u1conflict}"
        TARGET="$BASENAME"

        COUNTER=0
        while [ -e "$TARGET" ]; do
            COUNTER=$(( $COUNTER+1 ))
            TARGET="$BASENAME.$COUNTER"
        done

        echo "$FILE_PATH:$TARGET" >> $RENAME_LOG

        mv -v "$FILE_PATH" "$TARGET"

    done
)
```

You can follow these commands download the script and run it to rename the U1conflict files:

```
wget http://people.canonical.com/~roman.yepishev/us/rename-u1conflict-files.sh
```

```
chmod +x rename-u1conflict-files.sh
```

```
./rename-u1conflict-files.sh
```

Thank you sooooo much for the above codes --- worked like a champ!!:-\"

---

### Post by [Neurotic] on 2011-05-04
You sir, are a scholar and a gentleman.

Thank you very much, that just saved me hours.

---

### Post by Rocky37 on 2011-05-04
> **'[Neurotic] said:**
> You sir, are a scholar and a gentleman.

Thank you very much, that just saved me hours.

Thank you kind Sir -- I'm happy that this worked for you also.  I know I was delighted!

---

### Post by OttifantSir on 2011-12-01
I am no programmer, and I wouldn't have known where to start if I was asked to make this little script, but for me, with several thousands of pictures named numerical and sequentially, this script gives me 00001.jpg.1 instead of just removing the "u1conflict" from the name. I tried removing the $COUNTER-parts of the script, and removing ".u1conflict" from BASENAME, but this just causes the script to hang. 

I'd love to see an addition to this script with the functionality of asking the user if s/he wants to just remove ".u1conflict" or if s/he wants to add a number to the conflicting files, or give an argument like -r for remove or -n for numbers. The very best would be to add this funtionality to the Ubuntu One Control Panel, but I know this takes a lot more than just adding a few lines to this script, so I'm not getting my hopes up. BTW, I'm using 11.04 x86 and 11.10 x64 on the machines I'm trying to sync.

---

### Post by JonNicholson on 2012-03-01
I'm using Xubuntu 11.10, a recent installation -- I hate Unity, and Xubuntu gives me a traditional, configurable desktop.  Suddenly .u1.conflict files are popping up all over, and they resist renaming.  I try to rename them, and they just immediately go back to the ...u1.conflict name.  

Why, oh why, does UbuntuOne make this so hard?  Doesn't the Ubuntu team realize that people who like Linux like it because they hate Microsoft and Apple making all of their decisions for them?

Anyway, how can we overcome this resistance to renaming on the part of .u1.conflict files?

---

