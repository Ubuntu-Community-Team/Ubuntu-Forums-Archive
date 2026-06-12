---
title: "HOWTO: Custom commands in nautilus (TB Attachment example)"
date: 2005-11-17
forum: Tutorials
---

### Post by KillerKiwi on 2005-11-17
The sendto extension in breezy only works with evolution :(

The solution **Nautilus Actions**

Install Package
```
sudo apt-get install nautilus-actions
```
or click [nautilus-actions]("apt://nautilus-actions")

you may need to restart nautilus
```
nautilus -q
```

You will find the application under
System->Preferences->Nautilus Application Actions Configuration

Click "Add"
Fill in label - **Send Attachment Email via Thunderbird**
Fill in Path - **mozilla-thunderbird**
Fill in Parameters - **-compose "attachment=%u"**
Select the "Conditions" tab
Fill in Filenames Pattern - *****
Check the "Only Files" options
Click "OK"
Close

Done

Pre configured Nautilus Actions you can import are available from
[http://www.grumz.net/index.php?q=configlist](http://www.grumz.net/index.php?q=configlist)
includes many options such as
    * Merge many PDF files into a single one
    * Test a 7z archive for integrity
    * Create a 7z archive
    * Font installer
    * OptiPNG (Optimize PNG images)
    * thunderbird send to [http://www.grumz.net/?q=node/232](http://www.grumz.net/?q=node/232)

---

### Post by arnieboy on 2005-11-18
great howto and thanks for the nautilus configuration editor.. that really expands the possibilities of customizing nautilus a whole lot.

---

### Post by lizardking on 2005-11-19
cool! i hope that this is integrated in the next nautilus release..
The open terminal script si not too good
```
gnome-terminal --working-dir=%d
```

---

### Post by Omer on 2005-11-19
To search in the current folder:
**Label=** Search...
**Tooltip=** Search for files
**Path**= gnome-search-tool
**Parameters=** --path=%M
**File pattern=** *
**Appears if...=** only folders
**Appears if selection has...=** False
**Appears if scheme...=** file (remote locations don't work)

---

### Post by Omer on 2005-11-19
[QUOTE=lizardking]cool! i hope that this is integrated in the next nautilus release..
The open terminal script si not too good
```
gnome-terminal --working-dir=%d
```[/QUOTE]

or install *nautilus-open-terminal*.

---

### Post by Omer on 2005-11-19
To print a batch of documents::
**Label=** Print
**Tooltip=** Print selected documents
**Path**= ooffice2
**Parameters=** -p %f
**File pattern=** *.doc ; *.xls ; *.ppt ; *.odt ; *.ods ; *.odp ; *.odg ; *.sxw ; *.pps (or whatever ooo can handle)
**Appears if...=** only files
**Appears if selection has...=** True
**Appears if scheme...=** ALL

---

### Post by arnieboy on 2005-11-19
the only feature that this editor lacks is the ability to edit right click menus in nautilus when NO files or folder are selected. 
I have added a feature request on the app's homepage and if this is implemented, it will make it a complete menu editor for nautilus and I will personally see to it that **this gets into ubuntu universe**.

---

### Post by KillerKiwi on 2005-11-20
[QUOTE=arnieboy]great howto and thanks for the nautilus configuration editor.. that really expands the possibilities of customizing nautilus a whole lot.[/QUOTE]

Cheers arnieboy

PS Thanks again for Automatix, makes my life so much easier :)

---

### Post by magnusbb on 2005-11-20
[QUOTE=arnieboy]the only feature that this editor lacks is the ability to edit right click menus in nautilus when NO files or folder are selected. 
I have added a feature request on the app's homepage and if this is implemented, it will make it a complete menu editor for nautilus and I will personally see to it that **this gets into ubuntu universe**.[/QUOTE]

Thanks for your initiative.

Yes, implementing this feature would be fantastic, and it shouldn't be too difficult either.

---

### Post by animacide on 2005-11-20
Here's a setting to open files/folders as root.  It works so much more conveniently than the nautilus script I was using.

Label: Sudo...
Tooltip: Open with root privelages
Path: gnome-sudo
Parameters: "gnome-open %u" (be sure to put in the quotes)
File Pattern: *
Appears if selection contains: both
Don't check multiple files or files option (if anyone has an idea on how to make that work let me know)
Check these in scheme list: file, sftp

---

### Post by Omer on 2005-11-25
nautilus-actions 0.99 has been released

* Support for stock icons and custom icons.
* More HIGification.

Get it [here]("http://idefix.eup.uva.es/paquetes/unstable/nautilus-actions_0.99-1_i386.deb").

---

### Post by chaumurky on 2005-11-29
[quote=arnieboy]the only feature that this editor lacks is the ability to edit right click menus in nautilus when NO files or folder are selected. 
I have added a feature request on the app's homepage and if this is implemented, it will make it a complete menu editor for nautilus and I will personally see to it that **this gets into ubuntu universe**.[/quote]

Perhaps then you could include it in Automatix along with the "TB Send To" entry... :KS

---

### Post by magnusbb on 2005-12-11
Open current or selected folder in Konqueror:

Label= Open In Konqueror
Tooltip= Opens the selected folder in Konqueror
Path= konqueror
Parameters= %M
File pattern= *
Appears if...= only folders
Appears if selection has...= False
Appears if scheme...= file (remote locations don't work)

---

### Post by Sevoma on 2005-12-11
I made one, but I can 't get it to work. It installs .deb's with a zenity progress thing and makes a log.

here it is:

Label: Install Deb
Tooltip: Install the selected Debian Package
Icon: /usr/share/pixmaps/debian-logo.png
Path: zenity --progress --pulsate --title "Please Wait" --text $"Installing %f" & && gksudo dpkg -i
Parameters: %M" > ~/install_log.txt && killall zenity
File Pattern: *.deb

If anybody could make it work that would be great. This would be possible by executing a script also.

---

### Post by MetalMusicAddict on 2005-12-11
Weird. I installed the new .deb after removing the old one. Added the Print, Search and TB attachment actions. Rebooted but I see nothing on right-click.

---

### Post by zappa on 2005-12-11
Very nice indeed, thanks to all!

---

### Post by henriquemaia on 2005-12-11
Thanks a lot for this howto.

For the kmail folks like me, use:

Click "New Config"
Enter a Name: **Kmail send to**
Fill in label: **Send attachment via kmail**
Fill in Path: **/usr/bin/kmail**
Fill in Parameters: **--attach "%u"**
Fill in File Pattern: *****

With the custom icon option, you can put your favorite kmail icon in the menu.

---

### Post by henriquemaia on 2005-12-11
[QUOTE=MetalMusicAddict]Weird. I installed the new .deb after removing the old one. Added the Print, Search and TB attachment actions. Rebooted but I see nothing on right-click.[/QUOTE]

Have you edited with sudo? That didn't work for me either. You have to edit for your current user.

Hope this helps.

---

### Post by MetalMusicAddict on 2005-12-11
Ahh... You are a wise man. ;)

---

### Post by benplaut on 2005-12-12
can this do anything that nautilus-scripts can't, or is it just a pretty face for the same thing?

---

### Post by KillerKiwi on 2005-12-12
[QUOTE=benplaut]can this do anything that nautilus-scripts can't, or is it just a pretty face for the same thing?[/QUOTE]

It is a nicer nautiles-scripts yes, also it only displays items that are relevnet so you dont try and mount a odt file instead of an iso.

---

### Post by animacide on 2005-12-12
Another example, I use this to play folders of media files in totem.

Label: Play...
Path: totem
Parameters: %M
File Patterns: *
Show for folders only

---

### Post by arunsub on 2005-12-14
I got the following message when i entered nautilus -q

(nautilus:16049): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:16049): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:16049): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:16049): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:16049): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

It then opened nautilus. I right clicked a file and selected send to and didn't see any entry for thunderbird. Any idea?

---

### Post by joergenlie on 2005-12-23
This works almost fine. If I mark several items that i want to send in the same mail, I don't get the TB sendto option when I right click? The option only appears when I try to send one file.

Any suggestions?

JØrgen

---

### Post by Virtual DarKness on 2006-01-10
I looked around and found a way to have it works also if thunderbird is already running (it didn't worked for me in that case..)

here is the script to call instead of mozilla-thunderbird and then you just have to put "**%u**" as action parameter:

```
#!/bin/sh

res=`ps xc | grep -c mozilla-thunder`
if [ $res -gt 0 ]; then

        exec mozilla-thunderbird -remote "xfeDoCommand(ComposeMessage,attachment=$1)"

else

        exec mozilla-thunderbird -compose "attachment=$1"

fi
```

bye,
Giovanni.

p.s.
Thanks Omar for the Search tip ;)

---

### Post by quonsar on 2006-01-10
nautilus actions is the shiznit!!!!

=====================
Play in Beep Media Player
Path: beep-media-player
Parameters: %M
File Pattern: *
Folders/Files: Both
Multiple? checked
=====================

=====================
Open with GThumb Viewer
Path: gthumb
Parameters: %M
File Pattern: *
Folders/Files: Both
Multiple? checked
=====================

=====================
Open Terminal
Path: gnome-terminal
Parameters: --working-directory=%M
File Pattern: *
Folders/Files: Only Folders
Multiple? unchecked
=====================

=====================
Open Root Terminal
Path: gnome-sudo
Parameters: 'gnome-terminal --working-directory=%M'
File Pattern: *
Folders/Files: Only Folders
Multiple? unchecked
=====================

=====================
Send to Email
Path: /home/quonsar/.scripts/nautilus-sendmail
Parameters: "%u"
File Pattern: *
Folders/Files: Only Files
Multiple? checked
=====================

nautilus-sendmail is simply the script VirtualDarKness posted above. (substitute your actual path for the /home/quonsar/.scripts part)

---

### Post by fabs0028 on 2006-01-11
thanx the software is pretty usefull :)

Here is a deb for amd64 users.

---

### Post by maxdevis on 2006-01-30
i want to mount iso's.
the script works
but the menu not?
it gives me the error from the script.

#!/bin/bash
#
# nautilus-mount-iso

foo=`gksudo -u root -k -m "" /bin/echo "got r00t?"`

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
        zenity --error --title "ISO Mounter" --text "Kan niet mounten $*!"
        exit 1
fi

---

### Post by maxdevis on 2006-02-04
i want to make a menubutton so gxine loads the subtitle of an avi.
it works when i give in the terminal this:
gxine file:///home/michiel/file#subtitle:/home/michiel/file.srt

when i make a script it also works,
but when i want to do it with nautilus actions, it loads the avi, but not the subtitle.
i tried to add the script to nautilus actions, but again he loads the avi, not the srt.

---

### Post by MetalMusicAddict on 2006-02-04
Is there a way to make [THIS]("http://www.ubuntuforums.org/showthread.php?t=87369") script work is Nautilus Actions? Its a mount/unmount .iso script.

---

### Post by maxdevis on 2006-02-09
A new nautilus actions available!!!!

[QUOTE=MetalMusicAddict]Is there a way to make [THIS]("http://www.ubuntuforums.org/showthread.php?t=87369") script work is Nautilus Actions? Its a mount/unmount .iso script.[/QUOTE]


if you want to mount iso who are movie-dvd's, 
you can play iso's right away in a mediaplayer, without mounting

---

### Post by GrumZ on 2006-02-09
[QUOTE=maxdevis]i want to make a menubutton so gxine loads the subtitle of an avi.
it works when i give in the terminal this:
gxine file:///home/michiel/file#subtitle:/home/michiel/file.srt

when i make a script it also works,
but when i want to do it with nautilus actions, it loads the avi, but not the subtitle.
i tried to add the script to nautilus actions, but again he loads the avi, not the srt.[/QUOTE]

In fact Nautilus-actions use a Glib function to parse the command line, and it seems that this function parse the # character as the sign of comment and so ignore the end of the line. To workaround it, just put a backslash before the # sign like this :

```
file://%d/%f\#%d/%f.srt
```

---

### Post by GrumZ on 2006-02-09
[QUOTE=maxdevis]i want to mount iso's.
the script works
but the menu not?
it gives me the error from the script.

#!/bin/bash
#
# nautilus-mount-iso

foo=`gksudo -u root -k -m "" /bin/echo "got r00t?"`

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
        zenity --error --title "ISO Mounter" --text "Kan niet mounten $*!"
        exit 1
fi[/QUOTE]


Let's try this little rewrite of it and check if it makes it works better :

```
#!/bin/bash
#
# nautilus-mount-iso

image_name=`basename $2 .iso`

foo=`gksudo -u root -k -m "" /bin/echo "got r00t?"`

sudo mkdir /media/"$image_name"

if sudo mount -o loop -t iso9660 "$1" /media/"$image_name"
then
        if zenity --question --title "ISO Mounter" --text "$2 Successfully Mounted.
        
        Open Volume?"
        then
                nautilus /media/"$image_name" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$image_name"
        zenity --error --title "ISO Mounter" --text "Kan niet mounten $2!"
        exit 1
fi
```

and use this as parameters in Nautilus-actions :

```
%d/%f %f
```

I don't manage to test it because gksudo doesn't works on my Fedora box and when I removed it, the script didn't work because sudo ask for a password under X even though it didn't ask for it in command line.

---

### Post by joselin on 2006-02-11
Great work. Now i can send files to my BT devices

Label: SenSend to Bluetooth Device
Path: gnome-obex-send
Parameters: %M
File pattern: *
Appears if selection contains only files.

Cheers

---

### Post by pakux on 2006-02-15
looking at the first posts on this thread I followed the link to nautilus-actions [homepage]("http://www.grumz.net/?q=taxonomy/term/2/9"). There is available a new release (1.0), and even a breezy  [deb package]("http://www.grumz.net/download/nautilus-actions_1.0-1_i386.deb").

now my three cents on custom actions:

***********
Enqueue in xmms
Path: xmms
Parameters: %M -e
File Pattern: *
Folders/Files: Both
Multiple? checked
***********

---

### Post by tjwhaynes on 2006-03-03
When you copy files from CD onto hard disk, they carry their permissions with them and remain unwritable. This is easy to fix from the command line but time consuming in the GUI. This action allows you to recursively set the writable flag on selected files and directories.

Label: Recursive writable
Tooltip: Make all of the selection writable, including all subfolders.
Action: chmod
Parameters: -R u+w %M

Files/Folders: Both (or you could make this just apply to folders).

Cheers,
Toby Haynes

---

### Post by Bazon on 2006-03-06
**enqueue in XMMS:**
(displays only for audiofiles and folders in contrast to method above)

for files:
path: xmms
parameter: -e %M
symbol: /usr/share/xmms_mini.xpm

filter: *.mp3; *.ogg; *.wav (and whatever you want)
only files: checked
multiple checked: checked

Scheme:
file

for folders:
path: xmms
parameter: -e %M
symbol: /usr/share/xmms_mini.xpm

filter: *
only folders: checked
multiple checked: checked

Scheme:
file

**play in XMMS:**

for files:
path: xmms
parameter:  %M
symbol: /usr/share/xmms_mini.xpm

filter: *.mp3; *.ogg; *.wav (and whatever you want)
only files: checked
multiple checked: checked

Scheme:
file

for folders:
path: xmms
parameter: %M
symbol: /usr/share/xmms_mini.xpm

filter: *
only folders: checked
multiple checked: checked

Scheme:
file

**tag with Easy Tagger**
path: easytag
parameter: %M
symbol: /usr/share/EasyTAG.xpm

filter: *
only folders: checked
multiple checked: not checked

Scheme:
file

---

### Post by jms830 on 2006-03-24
**Easy convert webshots .wbz to .jpg using wbz2jpg for nautilus-actions:**

download and follow the instuctions here [http://www.angelfire.com/darkside/wbz2jpg/](http://www.angelfire.com/darkside/wbz2jpg/)
then in nautilus-actions

Label: Convert to JPEG
Tooltip: Converts wbz to jpg
Path: /usr/bin/wbz2jpg
Parameters: %M %M.jpg

File Pattern: *.wbz
only files: checked
multiple checked: checked

scheme: file

I can't seem to get it to work for more than one file at a time, but it works.

---

### Post by GrumZ on 2006-03-29
I'm happy to annouce you that it is now possible to share your actions on the official web site of Nautilus-actions. :D 

There is already a few configs submited and you have the possibility to submit your own configs too.

the configuration repository can be found at the following address :

[http://www.grumz.net/configlist](http://www.grumz.net/configlist)

You can found more information about this [here]("http://www.grumz.net/node/200")

Happy sharing ! :cool:

---

### Post by sellotape on 2006-03-31
Gnome easy install of deb files by right clicking on them.

[QUOTE=Sevoma]I made one, but I can 't get it to work. It installs .deb's with a zenity progress thing and makes a log.

here it is:

Label: Install Deb
Tooltip: Install the selected Debian Package
Icon: /usr/share/pixmaps/debian-logo.png
Path: zenity --progress --pulsate --title "Please Wait" --text $"Installing %f" & && gksudo dpkg -i
Parameters: %M" > ~/install_log.txt && killall zenity
File Pattern: *.deb

If anybody could make it work that would be great. This would be possible by executing a script also.[/QUOTE]
I've made a script to install deb files from the right click menu.  Please be kind it's my first Linux script.  Very easy to use, with progress bar.

Copy and paste the following script into a file call it "installer" and save it in your home folder, then make it executable.
[COLOR="Blue"]
#!/bin/bash
#
# nautilus-deb-installer

package_name=`basename $1`

if zenity --question --title "Alert" --text  "Do you wish to install the package $package_name?"
then
	foo=`gksudo -u root -m "Please enter your password to install $package_name" /bin/echo "0"`
	sudo dpkg -i "$1" | zenity --progress --pulsate --title "Please Wait" --text $"Installing $package_name"
	zenity --info --title "Installation Complete" --text "The package $package_name has been installed"
else
	zenity --info --title "Installation aborted" --text "The package $package_name was not installed"
	exit 1
fi
[/COLOR]
Then in Nautilus Actions:

Label: Install Package
Path: /home/<your username>/installer
Parameters: %M
File Pattern: *.deb
Files only 

Then when you right click on a deb file you will be able to install it.  :)

---

### Post by MetalMusicAddict on 2006-03-31
Very nice. In Dapper there is a very nice .deb installer now. Works with Synaptic.

---

### Post by ctof78 on 2006-05-22
hello,

is it possible to install nautilus-actions with default action available for all users ?
I means, if i install an action like "send to" and after that if i add a new user into my system, is this user have automaticly this action withou any other installation.

Thx
Christophe

---

### Post by lazyr on 2006-06-20
[QUOTE=ctof78]hello,

is it possible to install nautilus-actions with default action available for all users ?
I means, if i install an action like "send to" and after that if i add a new user into my system, is this user have automaticly this action withou any other installation.

Thx
Christophe[/QUOTE]

All files/folders in the /etc/skel/ directory are copied to the new home directory by the adduser script. So what you can do is this:
- Create a new user
- Configure everything to your liking
- Copy the necessary configuration files to /etc/skel/
- Now if you create a new user, it's configuration should be identical to the one you just copied.

Try to keep track of the file changes and copy only those files necessary to meet your goals. For example: you don't need to copy .bash_history .xsession-errors and various "auth" files. Also remember to preserve attributes, and owner/group should be both set to root.

---

### Post by hype on 2006-06-20
nautilus-actions is really good. ;)
 I just added a --play options after the audacious enqueue script :p
Really nice, usefull and easy to configure.

---

### Post by airtonix on 2006-06-26
jms830 : no sure what it is your using to make screen shots of pages but the GDgraphics extension for firefox does an excellent job of making PNGs of the entire page

---

### Post by H.E. Pennypacker on 2006-06-29
Is there a way to have Nautilus Actions appear in either Applications > System Tools or System > Administration.  Either one will do, but I'd prefer System Tools.

Nautilus Actions is pretty useful, but I'd like something that is less technical.  Unless you're getting actions from others, you have to know what you're doing.  I'd rather have something that doesn't require as much input, although there's not that much right now anyway.

Is there an easier to use version of Nautilus Actions...one that is less technical?

---

### Post by H.E. Pennypacker on 2006-06-29
[QUOTE=H.E. Pennypacker]Is there a way to have Nautilus Actions appear in either Applications > System Tools or System > Administration.  Either one will do, but I'd prefer System Tools.[/QUOTE]

I've found Nautilus Actions installs itself into System > Preferences.

---

### Post by MetalMusicAddict on 2006-07-02
Im looking for a script/action to to batch resize .jpegs.

---

### Post by catlett on 2006-07-02
Just FYI
nautilus-actions is available in Synaptic Package Manger
> nautilus extension to configure programs to launch
Nautilus actions is an extension for Nautilus, the GNOME file manager.
It allows the configuration of programs to be launched on files selected
in the Nautilus interface. It is listed (of course) as "nautilus-actions". I don't know if it is in the regular repos or if you need universe etc. I have them all enabled and nautilus-actions is in my synaptic, so I don't know if it was there before adding the extra repos or not. Again no real reason other than FYI.

---

### Post by GrumZ on 2006-07-03
[QUOTE=H.E. Pennypacker]Nautilus Actions is pretty useful, but I'd like something that is less technical.  Unless you're getting actions from others, you have to know what you're doing.  I'd rather have something that doesn't require as much input, although there's not that much right now anyway.

Is there an easier to use version of Nautilus Actions...one that is less technical?[/QUOTE]

I would really like to make a version that is more accessible but I don't have much ideas on how to do it ? :-k 
I had thought about a kind of wizard mode, which will make an action creation step by step with more explanation at each step. Another idea was to create two mode like winzip on windows : "easy mode" and "expert mode", the latter will have more options and the first one will have some options hidden with usual default values but I'm not sure it will be better.
For the moment all my new ideas will complicate the interface and I have big difficulties to find a way to add them all without bloating the interface. On the other hand, some of these new ideas will make lots of actions avoid their need for a script (eg, the possibility to launch the command given with each file in a loop instead of being given all together to the command at once).

If you have any ideas to make nautilus-actions easier, please don't hesitate to contact me at grumz _AT_ grumz _dot_ net or open a feature request on Bugzilla :

[http://bugzilla.gnome.org/simple-bug-guide.cgi?product=nautilus-actions](http://bugzilla.gnome.org/simple-bug-guide.cgi?product=nautilus-actions)

TIA

GrumZ
--
[http://www.grumz.net](http://www.grumz.net)

---

### Post by Chemist2006 on 2007-01-31
> **KillerKiwi said:**
> The sendto extension in breezy only works with evolution :(

Click "New Config"
Enter a Name **TB Send To**
Fill in label - **Send Attachment Email via Thunderbird**
Fill in Path - **mozilla-thunderbird**
Fill in Parameters - **-compose "attachment=%u"**
Fill in File Pattern - *****
Check all boxs under "Appears if schema in list"
Click "save"
Close


Unfortunately with this parameters it is possible to send via Thunderbird only one attachment. 
Does anyone know how to configure script so that I will be able to attach multiple files for sending via Thunderbird? For example I want to send 10 photos to my friend with one right click on selected items. I have tried to check in Nautilus Actions "appears if selection has mutliple files and folders", but it doesn't work. Only the first of selected multiple files is attached.
Can anyone help?

Thanx

---

### Post by Gnounc on 2007-02-15
ok, im new to linux in general, so nautilus-actions makes almost no sense to me,
but i am looking to implement a bash command i found for mounting ISO images as a CD-ROM drive (Starcraft from ISO) the bash command works fine, but i would verymuch like a right click accesable option to mount and dismount iso's. Or a draggable Launcher.

The code i have is basic:

mount file.iso /cdrom -t iso9660 -o loop

ive been trying all day to figure it out myself, and reading forum posts and tutorials to understand the syntax....i guess im not that quick, any help would be very much appreciated.

feel free to email me or IM me

[email]forumwatch@yahoo.com[/email]

~Gnounc

---

### Post by berylator on 2007-04-03
> **arnieboy said:**
> the only feature that this editor lacks is the ability to edit right click menus in nautilus when NO files or folder are selected. 
I have added a feature request on the app's homepage and if this is implemented, it will make it a complete menu editor for nautilus and I will personally see to it that **this gets into ubuntu universe**.

I have the solution:

You have to manually add a Advanced Condition and just delete the "new-scheme" field. Put a checkmark beside it, restart nautilus and it will work!

At least on my computer, it works. Hope this helps.

cheers,

berylator

---

### Post by colo505 on 2007-06-14
Thanks, this really helped! 

Looking for similar solution to zip+email a file..can anyone help?

---

### Post by AlwaysLearning on 2007-07-28
> **jms830 said:**
> **Easy convert webshots .wbz to .jpg using wbz2jpg for nautilus-actions:**

download and follow the instuctions here [http://www.angelfire.com/darkside/wbz2jpg/](http://www.angelfire.com/darkside/wbz2jpg/)
then in nautilus-actions

Label: Convert to JPEG
Tooltip: Converts wbz to jpg
Path: /usr/bin/wbz2jpg
Parameters: %M %M.jpg

File Pattern: *.wbz
only files: checked
multiple checked: checked

scheme: file

I can't seem to get it to work for more than one file at a time, but it works.

Hi jms830,

The problem you are encountering is that %M passes through a space-delimited list of files. If you had the files foo.wbz and bar.wbz selected in your home directory the actual parameters given to wbz2.jpg would look something like "/home/jms/foo.wbz /home/jms/bar.wbz /home/jms/foo.wbz /home/jms/bar.wbz.jpg"

When trying to handle multiple files with a program that expects an "in" and and "out" filename for each operation you'll need to redirect your action through a script like the following (save it to something like ~/Scripts/wbz_to_jpeg.sh):
```
#!/bin/sh

(while [ $# -gt 0 ]; do
	/usr/bin/wbz2jpg "$1" "$1.jpg"
	echo $1
	shift
	done
) | zenity --progress --auto-close --auto-kill --pulsate --text "Converting WBZ files to JPEG..."
```

You'll want to keep the quotes around "$1" and "$1.jpg" to allow for spaces contained in folder paths or file names. Then, your nautilus action will look like the following:
> Label: Convert to JPEG
Tooltip: Converts wbz to jpg
Path: ~/Scripts/wbz_to_jpeg.sh
Parameters: %M
File Pattern: *.wbz
only files: checked
multiple checked: checked
scheme: file

I do a bit of work with Canon RAW files (.CR2) converting to TIFFs and JPEGs for processing by various astrophotography software. Dave Coffin's dcraw is a lovely tool for doing this and wrapped in scripts like the above to use in nautilus actions makes life a breeze. Converting CR2's to JPEGs (8-bits per channel):
```
#!/bin/sh
(while [ $# -gt 0 ]; do
	dcraw -c -o 1 -w "$1" | ppmtojpeg > `basename "$1" CR2`jpg
	echo $1
	shift
	done
) | zenity --progress --auto-close --auto-kill --pulsate --text "Converting RAW files to JPEG..."
```
CR2's to 8-bit per channel TIFFs:
```
#!/bin/sh
(while [ $# -gt 0 ]; do
	dcraw -c -o 1 -w -T "$1" > `basename "$1" CR2`8bpc.tiff
	echo $1
	shift
	done
) | zenity --progress --auto-close --auto-kill --pulsate --text "Converting RAW files to 8-bit per channel TIFF..."

```
And CR2's to 16-bit per channel TIFFs, for handling by the serious image processing software like Registax and Iris, or the occasional Krita and Photoshop:
```
#!/bin/sh
(while [ $# -gt 0 ]; do
	dcraw -c -o 1 -w -4 -T "$1" > `basename "$1" CR2`16bpc.tiff
	echo $1
	shift
	done
) | zenity --progress --auto-close --auto-kill --pulsate --text "Converting RAW files to 16-bit per channel TIFF..."
```

---

### Post by VinceVanya on 2007-10-22
Anyone know how to create an action to play a dvd in totem, ideally only visible if clicking on a dvd?  I'm not sure how to make that a condition.

---

### Post by retaliator666 on 2007-11-15
Yes, I would want to know too how to make a Play DVD menu when going to this computer and clicking on the dvd

---

### Post by drubdrub on 2009-03-31
Hey, AlwaysLearning,

Thank you.  My 20D is just making the transition from XP to the Ubuntu box.  This helped a ton.

Gradually moving *everything* off the XP laptop.  Soon, I'll be able to format the HD and get rid of the XP virus.  Load Ubuntu on it.  Huge improvements!

Cheers

---

### Post by tonywhelan on 2009-04-27
> **Chemist2006 said:**
> Unfortunately with this parameters it is possible to send via Thunderbird only one attachment. 
Does anyone know how to configure script so that I will be able to attach multiple files for sending via Thunderbird? For example I want to send 10 photos to my friend with one right click on selected items. I have tried to check in Nautilus Actions "appears if selection has mutliple files and folders", but it doesn't work. Only the first of selected multiple files is attached.
Can anyone help?

Thanx

The Mozilla Knowledge Base article [http://kb.mozillazine.org/Command_line_arguments_(Thunderbird)]("http://kb.mozillazine.org/Command_line_arguments_(Thunderbird)") does not document how to add multiple attachments. Nor does it clearly explain the required use of quote marks in the argument. 

The syntax that I found works (even with filenames containing spaces) is as follows:

thunderbird -compose "attachment='file:///path/filename1,file:///path/filename2,file:///path/filename3'"

Note the double-quotes and the enclosed single quotes, and that the filename delimiter is a comma.

I'm not presently able to spend time considering how/if this syntax can be achieved within nautilus-actions.

If you want a powerful .deb addon that does "send to email" for multiple attachments and also has options for zipping the files, see [http://sourceforge.net/projects/mailpictures/]("http://sourceforge.net/projects/mailpictures/")

---

### Post by defaria on 2009-04-27
> **KillerKiwi said:**
> The sendto extension in breezy only works with evolution :(

The solution **Nautilus Actions**

Install Package
```
sudo apt-get install nautilus-actions
```
or click [nautilus-actions]("apt://nautilus-actions")

you may need to restart nautilus
```
nautilus -q
```

You will find the application under
System->Preferences->Nautilus Application Actions Configuration

Click "Add"
Fill in label - **Send Attachment Email via Thunderbird**
Fill in Path - **mozilla-thunderbird**
Fill in Parameters - **-compose "attachment=%u"**
Select the "Conditions" tab
Fill in Filenames Pattern - *****
Check the "Only Files" options
Click "OK"
Close

Done

Pre configured Nautilus Actions you can import are available from
[http://www.grumz.net/index.php?q=configlist](http://www.grumz.net/index.php?q=configlist)
includes many options such as
    * Merge many PDF files into a single one
    * Test a 7z archive for integrity
    * Create a 7z archive
    * Font installer
    * OptiPNG (Optimize PNG images)
    * thunderbird send to [http://www.grumz.net/?q=node/232](http://www.grumz.net/?q=node/232)

Perhaps I'm dense but I don't see how this works at all. First off after doing System: Preferences: Nautilus Actions and Add I have an edit box for Label but none for Path or Parameters. I see under Profile another Add button so I try that. Now I have path and parameters. On my machine thunderbird is under /usr/bin so I enter /usr/bin/thunderbird for the path and '-compose "attachment=%u"' for the parameters. Under the Conditions tab filenames is already "*" and Only files is already toggled. I then OK and I'm back at the dialog box entitled "Add a New Action". I notice under Profiles there's a new entry called "Profile 1". Odd. I OK that and I see at the Nautilus Actions Dialog box a "Send to Email" item in the list. That's what I put in for the Label. OK. Close that. 

Alrighty then - how do I **use** this new action? Nothing new in the menus. Nothing new in the toolbar. Nothing even in the right click menu! And send to doesn't have anything new in the Send as drop down either. I'm confused!

---

### Post by MarkieB on 2009-04-30
no longer participating in ubuntuforums.org

---

### Post by MattiJ on 2010-04-24
Now when nautilus has dual pane's, How to address the second pane?
Also how to use built in nautilus-action?

---

### Post by Hannie on 2012-04-25
This doesn't work in my Ubuntu Oneiric (Unity). After installing Nautilus-Actions, I can find it in the Dash. The Nautilus-Actions Configuration Tool icon appears, but as soon as I click on it in the Starter it disappears. Do I need to install something else first?

---

### Post by mc4man on 2012-04-25
> **Hannie said:**
> This doesn't work in my Ubuntu Oneiric (Unity). After installing Nautilus-Actions, I can find it in the Dash. The Nautilus-Actions Configuration Tool icon appears, but as soon as I click on it in the Starter it disappears. Do I need to install something else first?

nautilus-actions was never upgraded to work properly in 11.10, you need to either build your own, find a ppa, or use 12.04 where it has.

If not finding a suitable solution maybe post in General, this thread is old & starting to get outdated (certainly for the 3.X N-A versions

---

