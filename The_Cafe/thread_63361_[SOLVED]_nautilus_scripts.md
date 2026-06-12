---
title: "[SOLVED] nautilus scripts"
date: 2005-09-07
forum: The Cafe
---

### Post by arnieboy on 2005-09-07
One area that has not been discussed in too much detail is the area of nautilus scripts. These scripts extend the usability of nautilus many times over and I personally love using them. For the uninitiated, all nautilus scripts are listed on the right click menu in any nautilus file manager window and many CLI tasks can be click-automated with these scripts.
The best place to start with nautilus scripts and a few examples would be:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

I am starting this thread to encourage ubuntu users to come forward with ideas which they would want to have in a nautilus script. 

**Users** come forward with your wishlist!

**Programmers and enthusiasts**, come forward with the scripts that u already use or have created with a short description of what it does (and also due acknowledgements if necessary). I will keep compiling them in this post (the thread starter) after some testing to make sure they work. 
When the time is ripe and so is this thread, I will shift it to the HowTo forums. If things go right, this will emerge as one of the most educational and popular threads on this forum.

So get set and get started!

---

### Post by vinbuntu on 2005-09-07
[QUOTE=arnieboy]One area that has not been discussed in too much detail is the area of nautilus scripts. These scripts extend the usability of nautilus many times over and I personally love using them. For the uninitiated, all nautilus scripts are listed on the right click menu in any nautilus file manager window and many CLI tasks can be click-automated with these scripts.
The best place to start with nautilus scripts and a few examples would be:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

I am starting this thread to encourage ubuntu users to come forward with ideas which they would want to have in a nautilus script. 

**Users** come forward with your wishlist!

**Programmers and enthusiasts**, come forward with the scripts that u already use or have created with a short description of what it does (and also due acknowledgements if necessary). I will keep compiling them in this post (the thread starter) after some testing to make sure they work. 
When the time is ripe and so is this thread, I will shift it to the HowTo forums. If things go right, this will emerge as one of the most educational and popular threads on this forum.

So get set and get started![/QUOTE]
 I'm just a user and not a programmer (but a user that loves ubuntu!)  
What I'd like to see is a selection under the contextual menu of nautilus when I right click in nautilus/the desktop that states "I want to..." It would be a _task based menu_ listing that when hovered over would open a menu to the right with the following choices:

Browse the Internet (initiates command to open default browser)
Send an e-mail (opens compose window of default e-mail)
Check e-mail (opens main window of default e-mail)
Instant Message (opens Gaim or equivalent)
Listen to a song/album (opens Muine or something simple like it)
Write a note (open tomboy)
Post a blog entry (?)
Make an appointment (open evolution/sunbird)
Find... (launch BEST)

The idea is to have not too many tasks (we do have menus for a reason) but to put task that one thinks of quickly at the touch of a right click) .  I think compose e-mail and listen to a song (for those times you want to hear a particular song that you can quickly search in muine for) are the most useful.  I didn't put open terminal because that's an available option already.  I know that there are panel applets for tomboy and best as well as the calendar of the panel which can be used to launch evolution so these three aren't that important I guess, but might be nice.

---

### Post by ow50 on 2005-09-07
Here's a couple Nautilus scripts I have made, that others too might find useful. I'm not very comfortable with bash code, so there might be some errors or suboptimal solutions.

**Spell-check**
Easily adjustable to other languages and modes (e.g. --mode=sgml for SGML).
```
#!/bin/bash

# Check the spelling of an American English document with Aspell.

gnome-terminal --geometry=75x40+350+180 \
               -x aspell -c -x --lang=en_US "$1"
```

**Resize images**
Thumbnails are named "tn-<original>". Other people might prefer to change that to something else.
```
#!/bin/bash

# Resize selected image files.

size=`zenity --entry \
             --title "Create thumbnails" \
             --text "Biggest thumbnail dimension (pixels)"`

if [ $size = "" ]; then
	exit 0
fi

for arg; do
	convert -size "${size}x${size}" -resize "${size}x${size}" "$arg" "tn-$arg"
done
```

**Rename to lower case**
The current character range fits for Finnish. I don't know how this would work for non-latin character sets.
```
#!/bin/bash

# Change filenames of selected files to lowercase.

for arg; do
	rename 'y/A-ZÅÄÖ/a-zåäö/' "$arg"
done
```

**Rename to upper case**
The current character range fits for Finnish. I don't know how this would work for non-latin character sets.
```
#!/bin/bash

# Change filenames of selected files to uppercase.

for arg; do
	rename 'y/a-zåäö/A-ZÅÄÖ/' "$arg"
done
```

**Rename**
For advanced users who know their regular expressions.
```
#!/bin/bash

# Rename selected files with rename.

# Get pattern.
pattern=`zenity --entry \
                --title "Rename" \
                --text  "Search for (Perl style regular expression)"`

# Exit if "Cancel" pressed or entry left blank.
if [ $pattern = "" ]; then
	exit 0
fi

# Get replacement.
replacement=`zenity --entry \
                    --title "Rename" \
                    --text  "Replace with (Perl style regular expression)"`

# Exit is no longer possible because "Cancel" press and blank entry both return "".

for arg; do
	rename "s/$pattern/$replacement/g" "$arg"
done
```

---

### Post by arnieboy on 2005-09-07
awesome ow50 :)
These are the ones that I use:
**Open file in gedit as root**
```
#!/bin/bash
# Open file in text editor as root
foo=`gksudo -u root -k -m "enter your password for gedit root access" /bin/echo "root access?"`
sudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS
```
**Open nautilus as root in current location (directory)**
```
#!/bin/bash
# Open nautilus as root in current location (directory)
foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI
```

---

### Post by Ryvaeus on 2005-12-05
Hello, scripters.

This post will actually double as my first post as well, so a big hello to the Ubuntu community as well. Happy to finally be here among you all. ^^

I'm not sure if an "open terminal here" script has already been posted in the forums, but I'd like to submit mine here anyway since it's my first successful Nautilus script and I feel proud about it. Think of it as my "Hello World" to Ubuntu:
**"open-terminal-here"**
```
#!/bin/bash
#created by Ryvaeus
gnome-terminal --working-directory=$NAUTILUS_SCRIPT_CURRENT_URI
```
And here's one with root privileges:
**"root-terminal-here"**
```
#!/bin/bash
#created by Ryvaeus
sudo gnome-terminal --working-directory=$NAUTILUS_SCRIPT_CURRENT_URI
```
I do have a question, though. Regarding my second bit of code, the terminal doesn't seem to ask for the root password and yet it'll open itself up with said privilages anyway. This, needless to say, can be quite dangerous. Is there a way for me to include a prompt for the root password before the terminal is opened?

Also, another question. While I was fooling around making scripts for Nautilus (it's quite addicting), I attempted to make a "send via bluetooth" script which should allow the user to send the selected file to a bluetooth-enabled unit. Testing it with my phone, however, I got as far as the prompt for the bluetooth device. When I actually selected my phone, clicked "OK," and accepted the file sending prompt on my phone, however, an error resulted, saying "Unable to read file 'file:///home/ryvaeus/Gaim%20SFX/brad-receive.wav'. I actually tested the bluetooth file transfer capability manually (via terminal) before and after trying the script out, and it worked both times. Is there anything I need to add to the script to get it to work properly? Here's the script:
**"send-via-bluetooth" NOT WORKING**
```
#!/bin/bash
#created by Ryvaeus
exec gnome-obex-send $NAUTILUS_SCRIPT_SELECTED_URIS
```
As a side note, thanks, arnieboy, for making that Automatix script/program. It really, really is a time saver. ^^ I've had to reinstall Ubuntu three times already (mostly because of my own stupid mistakes), and I wish I knew about it earlier.

---

### Post by egon spengler on 2005-12-05
[QUOTE=Ryvaeus]
I do have a question, though. Regarding my second bit of code, the terminal doesn't seem to ask for the root password and yet it'll open itself up with said privilages anyway. This, needless to say, can be quite dangerous. Is there a way for me to include a prompt for the root password before the terminal is opened?[/QUOTE]

By default sudo opens a session that last for a preset amount of time, during this session you don't need to continually enter the password, just the command sudo. By default 15 mins but I assume this can be changed. Is it possible that when testing this script you have already entered the sudo password once within the last 15 mins? If this is what causes this then the command sudo -k at the start of the script will kill any current session thus requiring you to enter a password next time you use sudo

---

### Post by janga on 2005-12-11
Can you guys help me out. I need to convert many many folder.gif to folder.jpg. so i did something like this:

```
#!/bin/bash
exec convert folder.gif folder.jpg $NAUTILUS_SCRIPT_CURRENT_URI 
``` 
but of course it is not working. You know, i am not a programmer...:smile:

EDIT:
I found this: [http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/convert_to_jpeg]("http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/convert_to_jpeg")
It works! But could I let the script delete the old file automatically?

---

### Post by 4linux on 2005-12-11
My wish list:

How about:

move to folder
copy to folder

Something where you right click a file or folder and choose either "move to folder" or "copy to folder" and you get a file browser to select the destination folder.

Thanks,

Pat

---

### Post by arnieboy on 2005-12-11
[QUOTE=4linux]My wish list:

How about:

move to folder
copy to folder

Something where you right click a file or folder and choose either "move to folder" or "copy to folder" and you get a file browser to select the destination folder.

Thanks,

Pat[/QUOTE]
u might find the following thread useful:
[http://ubuntuforums.org/showthread.php?t=101870](http://ubuntuforums.org/showthread.php?t=101870)

Nice to see this old thread revived again. The link that I gave above has a couple of very useful scripts and should be merged with this thread by any mod who sees this.

---

### Post by 4linux on 2005-12-11
Cool.  I'm gonna try that right now...

---

### Post by cowlip on 2005-12-11
[QUOTE=arnieboy]u might find the following thread useful:
[http://ubuntuforums.org/showthread.php?t=101870](http://ubuntuforums.org/showthread.php?t=101870)

Nice to see this old thread revived again. The link that I gave above has a couple of very useful script and should be merged with this thread by any mod who sees this.[/QUOTE]

Thanks I am going to look at the move to copy to thread too.  I also made a bugzilla bug about including it in Nautilus since kDE and windows have it, but no word yet...

EDIT:  It works perfectly, I am very happy now

---

### Post by AgenT on 2005-12-11
[quote=janga] I found this: [http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/convert_to_jpeg]("http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/convert_to_jpeg")
It works! But could I let the script delete the old file automatically?[/quote]

After the convert line, try adding this:
```
rm $picture
```

---

### Post by 4linux on 2005-12-11
[QUOTE=arnieboy]u might find the following thread useful:
[http://ubuntuforums.org/showthread.php?t=101870](http://ubuntuforums.org/showthread.php?t=101870)

Nice to see this old thread revived again. The link that I gave above has a couple of very useful script and should be merged with this thread by any mod who sees this.[/QUOTE]

Well, the oddest thing; It works on some files but not others.  For instance I have a folder with a bunch of jpgs.  With some of them the copyto or moveto script works, on others it does not...just nothing happens.  Got me scratching my head. :confused: 

Same with some other files and folders too.

I'll keep playing with it to see if I can find out more.

---

### Post by benplaut on 2005-12-11
wow... the sudo gedit file, open terminal here, and open root nautilus are really, really useful!

would it be possible to make one that, similar to Mac OS/X, lets you have 3 click file labeling? is there a command-line way to add a label/emblem to a file? it would be incredibly useful

---

### Post by cowlip on 2005-12-11
I jsut wanted to add that you can do some of these wihtout adding scripts, like clicking "open with other application" and then writing in custom application, "gksudo gedit" "totem" "gksudo nautilus" etc

---

### Post by arnieboy on 2005-12-11
Though not pertinent to nautilus scripts directly, this howto would be an extremely interesting link for all u nautilus enthusiasts:
[http://ubuntuforums.org/showthread.php?t=91377](http://ubuntuforums.org/showthread.php?t=91377)

---

### Post by benplaut on 2005-12-12
[QUOTE=cowlip]I jsut wanted to add that you can do some of these wihtout adding scripts, like clicking "open with other application" and then writing in custom application, "gksudo gedit" "totem" "gksudo nautilus" etc[/QUOTE]

yes, except when you open files that you have permissions to, it's pointless and a bd habit to open them with su/sudo

---

### Post by xmastree on 2005-12-12
Here's a script I made, prompted by a question in [this thread]("http://www.ubuntuforums.org/showthread.php?t=60975"). It rotates images using rotate for anything other than jpg, in which case it uses jpegtran to get a lossless transformation.
```
#!/bin/sh
for arg 
do
 filetype=`file -i "$arg"`
if [ -n "`echo $filetype | grep -i 'jpeg' `" ]; then
 jpegtran -rotate 90 -trim "$arg" > temp.jpg;
 mv temp.jpg "$arg"
else
 convert -rotate 90 "$arg" "$arg"
fi
done
```

---

### Post by egon spengler on 2005-12-12
[QUOTE=4linux]Well, the oddest thing; It works on some files but not others.  For instance I have a folder with a bunch of jpgs.  With some of them the copyto or moveto script works, on others it does not...just nothing happens.  Got me scratching my head. :confused: 

Same with some other files and folders too.

I'll keep playing with it to see if I can find out more.[/QUOTE]

Do the files in question have spaces in their names? If so change ```
cp $arg $location
``` to ```
cp "$arg" "$location"
``` and it should work

---

### Post by janga on 2005-12-12
[quote=AgenT]After the convert line, try adding this:
```
rm $picture
```[/quote]

Cool! It works! Thank you. I love this forum.

---

### Post by robert_pectol on 2005-12-12
Here's a little Nautilus script I whipped together after reading this thread earlier today. It allows you to virus scan files and/or directories by right-clicking them. It requires Clam Anti-virus. I'm sure it could be made better or, "tweaked" to add more/different functionality. Feel free! Anyway, I hope it comes in handy for someone...

**[COLOR=Red]UPDATED:[/COLOR]  I've removed the first version and replaced it with this updated version:**

```

#!/bin/bash
#
#  Nautilus anti-virus scanner script - Uses Clam Anti-virus
#  Written by Robert Pectol, December 2005 - http://rob.pectol.com
######################################################################

#  Set some variables used in the script
files_path=`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d ':' -f2 | sed 's/\/\///'`
files=$1
gui=`which zenity`
vscan=`which clamscan`

#  Function to scan file(s)
scan_it()
{
        touch /tmp/scanresult
        if [ "$files_path" = "" ]; then
                #  Script can run from launchers, scripts other than from Nautilus, etc. (doesn't require $NAUTILUS_SCRIPT_CURRENT_URI)
                result=`$vscan -r "$files" --log=/tmp/scanresult | $gui --title "Virus Scanner" --progress \
                --text="Scanning $files..." --pulsate --auto-close; cat /tmp/scanresult` &> /dev/null
        else
                result=`$vscan -r "$files_path/$files" --log=/tmp/scanresult | $gui --title "Virus Scanner" --progress \
                --text="Scanning $files..." --pulsate --auto-close; cat /tmp/scanresult` &> /dev/null
        fi
        rm -f /tmp/scanresult &> /dev/null
        #  Feedback - if scan ended with errors or was terminated prematurely...
        if [ "$result" = "" ]; then
                err_text="Virus scan on $files terminated!"
                errors
        fi
        #  Feedback - if scan completed successfully...
        clean=`echo $result | grep 'FOUND'`
        #  Alter gui feedback according to presense/absense of virus(s) found during scan
        if [ "$clean" != "" ]; then
                $gui  --title "Virus Found!" --error --text="$result" &> /dev/null
        else
                $gui  --title "Virus Scan Results!" --info --text="$result" & &> /dev/null
        fi
}
#  Function to handle errors
errors()
{
        $gui  --title "Virus Scan Error!" --error --text="$err_text" &> /dev/null
        exit 1
}

#  Check for presense of required utilities
if [[ -x "$vscan" && -x "$gui" ]]; then
        scan_it
else
        if [ -x "$vscan" ]; then
                echo "Zenity was NOT found on the system!"
                exit 1
        else
                err_text="Clam Anti-virus was NOT found on the system!"
                errors
        fi
fi
exit 0
__
```

Enjoy!

---

### Post by 4linux on 2005-12-12
[QUOTE=egon spengler]Do the files in question have spaces in their names? If so change ```
cp $arg $location
``` to ```
cp "$arg" "$location"
``` and it should work[/QUOTE]

Yes, some of them did have spaces in the file names.  I'll try the fix, Thanks:)

---

### Post by janga on 2005-12-28
Hi guys.
If anyone of you super-scripters seeks for some challenge:
[We]("http://ubuntuforums.org/showthread.php?t=87531") need a script that scans a directory recursively for folder.jpgs and AlbumArtSmall.jpgs and then writes a .xml file into /home/%user%/.nautilus/metafiles. The aim is to show Album covers instead of default nautilus folder icons automatically. (because in huge mp3-collections, selecting custom icons for every damn folder is really...stupid)

---

### Post by NinjitsuStylee on 2006-07-30
> **janga said:**
> Hi guys.
If anyone of you super-scripters seeks for some challenge:
[We]("http://ubuntuforums.org/showthread.php?t=87531") need a script that scans a directory recursively for folder.jpgs and AlbumArtSmall.jpgs and then writes a .xml file into /home/%user%/.nautilus/metafiles. The aim is to show Album covers instead of default nautilus folder icons automatically. (because in huge mp3-collections, selecting custom icons for every damn folder is really...stupid)

Yes, yes we do.  I've tried editing the .xml by hand (added one folder to see if it would work).  The changes don't seem to do anything :(

---

### Post by mustang on 2006-07-30
**Ryvaeus**,

Thank you for the open-terminal-here script!

---

### Post by adamkane on 2006-07-31
Good to see you're piquing everyone's interest in n-scripts.

My favorite n-scripts are video-convert, audio-convert and mount-cd-image.

---

### Post by zugu on 2006-07-31
Is there any way of having Copy / Cut / Paste / Properties buttons in the nautilus main toolbar (Win98 oldschool) ?? 

Copy To / Move To buttons would also be fine.

---

### Post by mostwanted on 2006-07-31
This script sends the selected files to your Bluetooth device and comes with some succes/failure messages created with Zenity:

```
#!/bin/bash

# Simple script that integrates gnome-obex-send into Nautilus
# Setup of cell phone: http://www.ubuntuforums.org/showthread.php?t=34740
# (C) Simon Gray 2006

if [ "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
	if [ "$(gnome-obex-send $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)" = "" ]; then
		zenity --error --text="No files transferred!"
	else
		zenity --info --title="Transfer complete" --text="The file-transfer is done."
	fi
else
	zenity --error --text="No files chosen! You must choose one or more files."
fi
```

It's GPL. I'm gonna assume everything in this thread is GPL or similarly liberal BTW :)

---

### Post by drewsimon on 2006-07-31
Hey, these are great scripts. Thanks! I'm just learning how to do this. I'm trying make a simple script to wipe files. After I get the wipe function to work I'll add a "Are you sure you want to wipe these files?" dialog box using zenity. But I can't get the wipe business to work. Anyone know what's wrong with this?

```

#!/bin/bash
wipe $NAUTILUS_SCRIPT_SELECTED_URIS -f -r

```

The -f switch subpresses the are you sure question.
The -r switch makes it wipe all subdirs and files in subdirs.

fake edit: I have the wipe package installed.

---

### Post by adrenaline_nz on 2006-08-03
I've been going mad getting all sorts of scripts going, it's great :)

One I would just love would be a script that would list all the files in a directory and subdirectories but not include the folder names and output it into xml or something like that?

---

### Post by drunken-wallaby on 2006-08-29
Hi everyone.

Is it possible to have a nautilus script that does bulk renaming in a way like gthumb has it without having to know anything about regular expressions? That would be really awesome to rename pics from digital cameras...

---

### Post by ounas on 2006-08-29
Thanks from Roi

---

### Post by ounas on 2006-08-29
> **robert_pectol said:**
> Here's a little Nautilus script I whipped together after reading this thread earlier today. It allows you to virus scan files and/or directories by right-clicking them. It requires Clam Anti-virus. I'm sure it could be made better or, "tweaked" to add more/different functionality. Feel free! Anyway, I hope it comes in handy for someone...


Enjoy!

Thanks for this one. works great

:D 

Ounas

---

### Post by wordsmythe on 2006-08-31
This might be a stupid question, but do I need a script to have nautilus display the locations of results when i do a search?

I can do it fine in the console, but it'd be helpful if I could find a way to make it display a "location" column for the results list.

---

### Post by anodizer on 2006-08-31
I think a tag renamer Nautilus plugin/script (like Thunar's) is essential. Is it possible?

---

### Post by grte on 2006-08-31
**Mount Iso**
```
#!/bin/bash 
# 
for I in "$*" 
do 
foo=`gksudo -u root -k -m "enter your password for root terminal 
access" /bin/echo "got r00t?"` 
sudo mkdir /media/"$I" 
sudo mount -o loop -t iso9660 "$I" /media/"$I" && nautilus /media/"$I" --no-desktop 
done 
done 
exit0

```

**Umount Iso**
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

---

