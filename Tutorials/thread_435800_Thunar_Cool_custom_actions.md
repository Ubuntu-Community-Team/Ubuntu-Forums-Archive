---
title: "Thunar: Cool custom actions"
date: 2007-05-07
forum: Tutorials
---

### Post by lapsey on 2007-05-07
The information in this thread has been moved to [https://help.ubuntu.com/community/ThunarCustomActions](https://help.ubuntu.com/community/ThunarCustomActions)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012432](http://ubuntuforums.org/showthread.php?t=2012432)

Thread closed.


If you like thunar, you will probably love custom actions. These are user-defined commands that act upon selected files in thunar. Either on its own, or combined with a simple dialog app such as Zenity, these can be very powerful and useful indeed.

Thunar > Edit > Configure custom actions will take you to the dialog for creating and organising your custom actions. However, because this is GUI-oriented, the easiest way to install someone else's custom action is through a bash command.


**Remove...**
Command: *rm -r*
Description: Removes the selected file(s) from the disk, bypassing any local Recycle bin. Useful when in samba shares. Requires confirmation for reasons of safety.
Requires: zenity
Installation:```

CONTENT='<action><icon>stock_delete</icon><name>Remove...</name><command>zenity --question --title=&quot;Remove...&quot; --window-icon=&quot;/usr/share/icons/Tango/16x16/actions/edit-delete.png&quot; --text=&quot;Do you wish to permanently\nremove the selected file(s)?&quot; ; if [ $? = 0 ] ; then rm -r %F ; fi</command><description>Permanently remove the selected file(s)</description><patterns>*</patterns><directories/><audio-files/><image-files/><other-files/><text-files/><video-files/></action>'
cat $HOME/.config/Thunar/uca.xml >> newtmp
sed 's/<\/actions>//' <newtmp >newfile
echo $CONTENT >> newfile
mv $HOME/.config/Thunar/uca.xml $HOME/.config/Thunar/uca.xml.bak
mv newfile $HOME/.config/Thunar/uca.xml
rm newtmp

```

**Create Symlink**
Command: *ln -s*
Description: Creates an absolute symbolic link to the selected file in the same folder, which can then be moved or renamed as desired. `man ln` for more info 
Requires:
Installation:```

CONTENT='<action><icon>emblem-symbolic-link</icon><name>Create Symlink</name><command>ln -s %f %n.symlink</command><description>Creates a symbolic link to the selected object</description><patterns>*</patterns><directories/><audio-files/><image-files/><other-files/><text-files/><video-files/></action>'
cat $HOME/.config/Thunar/uca.xml >> newtmp
sed 's/<\/actions>//' <newtmp >newfile
echo $CONTENT >> newfile
mv $HOME/.config/Thunar/uca.xml $HOME/.config/Thunar/uca.xml.bak
mv newfile $HOME/.config/Thunar/uca.xml
rm newtmp

```

The above, and other custom actions can be found at [http://thunar.xfce.org/pwiki/documentation/custom_actions](http://thunar.xfce.org/pwiki/documentation/custom_actions) , but it is by no means an exhaustive list.

If you have any custom actions of your own, please check out '~/config/Thunar/uca.xml' and post them here! Similar format appreciated

---

### Post by mali2297 on 2008-04-24
I will contribute to this old thread with a few of my own custom actions. The first one is a variant of the *Remove...* action above but uses Xdialog instead of Zenity (to avoid gnome dependencies).

Name: Permanently remove...
Description: Permanently remove selected files
Command: Xdialog --title "Remove..." --yesno "Do you wish to permanently remove \n %N?" 10 45 && rm -r %F
File pattern: *
Appears if selection contains: any files
Requires: Xdialog
[PHP]
<action><icon></icon><name>Permanently remove...</name><command>Xdialog --title &quot;Remove...&quot; --yesno &quot;Do you wish to permanently remove \n %N?&quot; 10 45 &amp;&amp; rm -r %F</command><description>Permanently remove selected files</description><patterns>*</patterns><directories/><audio-files/><image-files/><other-files/><text-files/><video-files/></action>
[/PHP]

Name: Join
Description: Join selected text files
Command: cat %F > joined.txt
File pattern: *
Appears if selection contains: text files
[PHP]
<action><icon></icon><name>Join</name><command>cat %F &gt; joined.txt</command><description>Join selected text files</description><patterns>*</patterns><text-files/></action>
[/PHP]

Name: View
Description: View selected images in a slideshow
Command: feh %F
File pattern: *
Appears if selection contains: image files
Requires: feh
[php]
<action><icon></icon><name>View</name><command>feh %F</command><description>View selected images in a slideshow</description><patterns>*</patterns><image-files/></action>
[/php]

Name: Play 15 seconds
Description: Play a 15 seconds clip of a media file
Command: mplayer %f -really-quiet -endpos 15
File pattern: *
Appears if selection contains: audio files, video files
Requires: mplayer
[php]
<action><icon></icon><name>Play 15 seconds</name><command>mplayer %f -really-quiet -endpos 15</command><description>Play a 15 seconds clip of a media file</description><patterns>*</patterns><audio-files/><video-files/></action>
[/php]

---

### Post by adamlau on 2009-01-07
Copy Current Path [using xclip]
```
echo -n %f | xclip -selection "clipboard"
```

Open Terminal Here [using urxvt client]
```
urxvtc -cd %f
```

Extract Archive Here [using Squeeze]
```
squeeze -x . %N
```

Extract Passworded Archive [using Xarchiver]
```
xarchiver -e %N
```

Estimate Space Usage [using zenity, including grand total]
```
du -chs --apparent-size %N | zenity --text-info
```

Create Archive Here [using Squeeze]
```
squeeze -n %N
```

Sign Using GnuPG [terminal password entry]
```
terminal -e "gpg -a -u [user] -b %f"
```

Encrypt Using GnuPG
```
terminal -e "gpg -e -r [recipient] %f"
```

Decrypt GnuPG File [appending .decrypted to the decrypted filename]
```
terminal -e "gpg -o %n.decrypted -d %f"
```

Shred & Delete File(s) [using zenity]
```
zenity --question;if [$? = 0];then shred -fuz %F;fi
```

---

### Post by mali2297 on 2009-01-07
Name: Add to Ipod
Description: Add songs to Ipod
Command: gnupod_addsong.pl %F | Xdialog --title "GNUpod - Add song" --no-cancel --tailbox - 24 64
File pattern: *.mp3;*.m4a;*.mp4
Appears if selection contains: audio files, video files
Requires: gnupod, Xdialog
[PHP]
<action><icon></icon><name>Add to Ipod</name><command>gnupod_addsong.pl %F | Xdialog --title &quot;GNUpod - Add song&quot; --no-cancel --tailbox - 24 64</command><description>Add songs to Ipod</description><patterns>*.mp3;*.m4a;*.mp4</patterns><audio-files/><video-files/></action>
[/PHP]

---

### Post by nabilalk on 2010-01-29
Here are some useful custom actions that I have come across in my Ubuntu travels, enjoy ;-)

Name: **Open Folder as Root**
Description: Opens the current folder with root permissions
Command: **gksu thunar %f**
File pattern: *
Appears if selection contains: Directories
***[COLOR="Red"]*Caution with the root access[/COLOR]***

Name: **Open Text as Root**
Description: Opens selected text file with root permissions
Command: **gksu gedit %f**
File pattern: *
Appears if selection contains: Text Files
*I use _gedit_ as my text editor, but you can substitute gedit for any text editor you wish.
[COLOR="red"]****Caution with the root access***[/COLOR]

Name: **Search including hidden files/folders**
Description: Searches entire file system
Command: **catfish --fileman=thunar --hidden --path=%f**
File pattern: *
Appears if selection contains: Check all 
*I use _catfish_ as my search app, but you can substitute catfish for any search app that you like.

- first two courtesy of *Tayfun Duran*: 
[http://www.pubbs.net/ubuntu/200911/6921/](http://www.pubbs.net/ubuntu/200911/6921/)

---

### Post by silverkeeper on 2010-01-29
here are mine

**Open as root** (in your default program)
command: **gksudo exo-open %F**
patterns: * | all

**Mount iso**
command: **gksudo mount -o loop -t iso9660 %f /mnt**
patterns: *.iso | other files

**Copy Dropbox public link** (appears everywhere but works only in your Dropbox public folder :/ *is there any way to make it visible only in Dropbox folder ?*)
command: **echo -n %f | sed 's/\/home\/you\/Dropbox\/Public/http:\/\/dl\.dropbox\.com\/u\/123456/' | xclip -selection clipboard** *you'll need to replace "you" and "123456", of course*
patterns: * | all except folders

---

### Post by nabilalk on 2010-02-05
> **silverkeeper said:**
> 

**Copy Dropbox public link** (appears everywhere but works only in your Dropbox public folder :/ *is there any way to make it visible only in Dropbox folder ?*)
command: **echo -n %f | sed 's/\/home\/you\/Dropbox\/Public/http:\/\/dl\.dropbox\.com\/u\/123456/' | xclip -selection clipboard** *you'll need to replace "you" and "123456", of course*
patterns: * | all except folders

What do you replace "123456" with? And is u your username?

---

### Post by JDFIght on 2010-05-23
Just installed XFCE on my powerbook g4 debian system today - Now it's my default session and I will never go back!  

Anyway - Here's my first thunar custom action - 

I can't live without this!

Name: **Convert to AVI**
Description: ffmpeg Conversion
Command: xfce4-terminal -x ffmpeg -i %f -b 798k -ab 128k %f.avi
Pattern:  All Video Files

Since I am a ppc linux user with no real flash alternative, .flv video files sometimes playback with ugly green artifacts or choppy framerate - using this action to convert to .avi with ffmpeg fixes these issues!

---

### Post by Jose Catre-Vandis on 2010-08-08
This is more of a beautification than anything else. I copy files around a lot. my basic custom action didn't show me any progress, and zenity progress doesn't pick up cp and mv commands to show progress. Finally figured out how to at least get a pulsating progress bar going whilst the file/s are being copied or moved:


The main command
> (for I in $(seq 2); do echo $I; sleep 1; done; cp %F "/destination/folder") | zenity --progress --pulsate --auto-close

Choose your file types accordingly

---

### Post by historyb on 2010-08-19
> **Jose Catre-Vandis said:**
> This is more of a beautification than anything else. I copy files around a lot. my basic custom action didn't show me any progress, and zenity progress doesn't pick up cp and mv commands to show progress. Finally figured out how to at least get a pulsating progress bar going whilst the file/s are being copied or moved:


The main command


Choose your file types accordingly

I just tried and it didn't let me copy but showed a progress bar

---

### Post by switchrodeo720 on 2011-02-06
I'm a new user to Thunar, but I like Thunar custom actions better than Nautilus scripts. 

This script opens up TheTVDB.com page for the tv show file selected. 

```
#!/bin/bash

# set the variable to your browser executable path
browser='google-chrome'

TITLE_PARSE () {
        sed -r 's/\.S[0-9]{2}E[0-9]{2}.*//Ig;s/\.[0-9]{4}.*//g'
}

SPACE2PLUS () {
        sed 's/\./+/g'
}

SERIESID () {
        grep "seriesid" | head -n 1 | sed 's/<seriesid>//g;s/<\/seriesid>//g'
}

file=$1
title=$(echo "$file" | TITLE_PARSE | SPACE2PLUS)
seriesid=$(curl -s "http://www.thetvdb.com/api/GetSeries.php?seriesname=$title" | SERIESID)
if [ -z "$seriesid" ]
then
        title2=$(echo "$title" | sed 's/\+/ /g')
        zenity --error --text="TheTVDB.com has no records for $title2."
        exit 1
fi
$browser "http://thetvdb.com/?tab=series&id=$seriesid" > /dev/null

```

I have also attached this file to this post.

Call this script by creating a custom action, like so:
```
tvdb.lookup.sh %n
```

This script will work on the two (IMHO) most common tv show file naming patterns. Below are examples:

TV.Show.Title.S02E11.avi
-or-
TV.Show.Title.2011.02.06.avi

---

### Post by breek on 2011-10-17
i've edited a bit the script by lapsey (the [remove...](http://ubuntuforums.org/showpost.php?p=2608548&postcount=1)) in order to have a message if something goes wrong while the system is removing files.
so, it still deletes files (avoiding the trash bin), it still ask confirmation but if it can't delete a file it shows an error message.
here is the command to paste in the "create action" window

```

zenity --question --title="Remove..." --window-icon="/usr/share/icons/Tango/16x16/actions/edit-delete.png" --text="Do you wish to permanently\nremove the selected files?" ; if [ $? = 0 ] ; then rm -r %F || { zenity --error --text="an error occurred!\ncheck if you are\nallowed to remove\nthe selected files"; }; fi

```

note: command improved [here](http://ubuntuforums.org/showpost.php?p=11404726&postcount=19)

---

### Post by breek on 2011-10-17
one of the thing i don't like in thunar is that the user can change file permissions only one file at a time.
so here we are...

[IMG]http://img442.imageshack.us/img442/2188/rwx.png[/IMG]

this action let the user change file permissions of one or multiple files at the same time and, if something goes wrong while executing the chmod command, it displays an error message.
here is the command to paste in the "create action" window:
```

ans=$(zenity  --height=350 --list  --text "change files permissions" --checklist  --column "pick" --column "options" TRUE "user-read" TRUE "user-write" FALSE "user-exec" FALSE "group-read" FALSE "group-write" FALSE "group-exec" FALSE "all-read" FALSE "all-write" FALSE "all-exec" --separator=":"); if [ "$ans" != "" ]; then searchuserread="user-read"; searchuserwrite="user-write"; searchuserexec="user-exec"; user1="0" ; user2="0" ; user3="0" ; searchgroupread="group-read"; searchgroupwrite="group-write"; searchgroupexec="group-exec"; group1="0" ; group2="0" ; group3="0" ; searchallread="all-read"; searchallwrite="all-write"; searchallexec="all-exec"; all1="0" ; all2="0" ; all3="0" ; case $ans in  *"$searchuserread"*) user1="4" ;; esac ; case $ans in  *"$searchuserwrite"*) user2="2" ;; esac ; case $ans in  *"$searchuserexec"*) user3="1" ;; esac ; case $ans in  *"$searchgroupread"*) group1="4" ;; esac ; case $ans in  *"$searchgroupwrite"*) group2="2" ;; esac ; case $ans in  *"$searchgroupexec"*) group3="1" ;; esac ; case $ans in  *"$searchallread"*) all1="4" ;; esac ; case $ans in  *"$searchallwrite"*) all2="2" ;; esac ; case $ans in  *"$searchallexec"*) all3="1" ;; esac ; u=$(($user1 + $user2 + $user3)) ; g=$(($group1 + $group2 + $group3)) ; a=$(($all1 + $all2 + $all3)) ; result="$u$g$a" ; chmod $result %F || { zenity --error --text="an error occurred!\ncheck if you are allowed\nto change permissions\nof the selected files"; } ; fi

```
**note:** by default the script always starts with only "user read" and "user write" bits selected; if you are changing folder permission be sure to check the "exec" bit (as in unix standards)

---

### Post by MonolithImmortal on 2011-10-18
Cool, thanks guys. Bookmarked for later, this will be useful for my archbang install.

---

### Post by Flymo on 2011-10-18
Thanks, folks - some useful and interesting posts.

---

### Post by scania_gti on 2011-10-19
How add a custom action "copy to Ubuntu one folder"? (or any other folder)

Try command 
cp %F /home/myname/Ubuntu One      - not work, but 
cp %F /home/myname/Video               - work great.
Try to set permisions to Ubuntu One folder, but thunar say "can't set permisions for symbolic link".
Solved:
Create a folder, add custom action from thunar:
```
cp %F /home/myname/myfolder
```
and type in terminal
```
u1sdtool --create-folder=/home/myname/myfolder
```
and done :)
Now i can with right click send files to Ubuntu One :)

---

### Post by breek on 2011-10-20
i think the first command doesn't work because of the space between Ubuntu and One; try
cp %F "/home/myname/Ubuntu One"

---

### Post by scania_gti on 2011-10-20
> **breek said:**
> ... of the space between Ubuntu and One...
Original folder name - with space, and when i rename folder - program that renamed see as new folder ;)
And doesn't work with folder, created in original "Ubuntu One" folder.
Maybe because that space... :(

---

### Post by breek on 2011-10-28
i made a little change in [the script used to delete files](http://ubuntuforums.org/showpost.php?p=11359697&postcount=12); now it display the names of the files you are going to delete.

```

files="%N" ; filescleaned=$(echo "$files" | sed "s/&/\\\&amp;/g") ; filesformatted=$(echo "$filescleaned" | sed "s/' '/'\\\n'/g") ; zenity --question --title="Remove..." --window-icon="/usr/share/icons/Tango/16x16/actions/edit-delete.png" --width=400 --text="Do you wish to permanently\nremove these files?\n\n$filesformatted" ; if [ $? = 0 ] ; then rm -r %F || { zenity --error --text="an error occurred!\ncheck if you are\nallowed to remove\nthe selected files"; }; fi

```
note: if you are deleting lots and lots of files the list may be incomplete as may not fit the window (it depends on your screen resolution)

---

### Post by bdalzell on 2011-11-12
Trying to make a custom command to rotate and image 90 degrees.

jpegtran -rot 90 %F>%f-90.jpeg

This works for a single image but I cannot figure out how to make it work on a selected set of images.

When you highlight a group of images the first rotated one comes out with 0 size and then nothing else happens
of course I have to rename the rotated images afterwards as they come out with the full filename embedded in the new name. have not figured out a way around that either, yet

---

### Post by bdalzell on 2011-11-12
This one works on groups of files but messes up the file names

convert -rotate 90 %F %F-90.jpeg

so files starting out named 
image1.jpg, image2.jpg, image3.jpg, image4.jpg, image5.jpg

end up being called , 
image5.jpg-90-0.jpeg
image5.jpg-90-1.jpeg
image5.jpg-90-2.jpeg
image5.jpg-90-3.jpeg
image5.jpg-90-4.jpeg

obviously I need more guidance on wildcard usage

---

### Post by scania_gti on 2012-02-15
Thunar custom action for move files from subfolders to parent (curent) folder:
```
find . -mindepth 2 -type f -exec mv "{}" . \;
```
And delete all empty folders in curent folder:
```
find . -type d -empty -delete
```
Great for work with photos or extracted zip's :)

---

### Post by Digger109 on 2012-05-02
Great post....I've "sequestered" a bunch of the custom actions mentioned here.

Here's one to add...it encrypts/decrypts using bcrypt.  There are a few "gates" along the way....

```
zenity --info  --title="Impending Bcrypt Operation" --window-icon="/usr/share/pixmaps/keybox.png" --text="There is a bcrypt operation impending.  Watch inside the File Manager window to verify that said operation is successful." ; : ; while [ "$?" = "0" ] ; do xterm -e bcrypt %F ; sleep 2 ; zenity --question --title="Success?" --window-icon="/usr/share/pixmaps/keybox.png" --text="Was the bcrypt operation successful?" ; if [ "$?" = "0" ] ; then exit ; fi ; zenity --question --title="Try again?" --window-icon="/usr/share/pixmaps/keybox.png" --text="Would you like to try again?" ; if [ "$?" != "0" ] ; then exit ; fi ; done
```You'll need to change the icon names, most likely.

IHTHS!

---

### Post by Jose Catre-Vandis on 2012-05-07
A quick one, grab info about your media file (music/video) with ffmpeg:
```
ffmpeg -i %f  2>&1 | grep -e Stream -e Duration -e Input | zenity --width=800 --height=240 --text-info --title %n
```

---

### Post by LewisTM on 2012-06-08
**Edit ACLs and User Extended attributes**
Needs the eiciel package
Custom command:
```
eiciel %f
```
Works with all modern Linux filesystems running on kernels >3.0

This is great not only for more access control but also for adding custom **NOTES** to files. They are conserved with move and copy commands (at least with Thunar). Add the -AX switch for rsync copy/backup commands. Combine with emblems to flag files that have custom notes.

Awesome!

---

### Post by Jose Catre-Vandis on 2012-06-09
> **LewisTM said:**
> **Edit ACLs and User Extended attributes**
Needs the eiciel package
Custom command:
```
eiciel %f
```
Works with all modern Linux filesystems running on kernels >3.0

This is great not only for more access control but also for adding custom **NOTES** to files. They are conserved with move and copy commands (at least with Thunar). Add the -AX switch for rsync copy/backup commands. Combine with emblems to flag files that have custom notes.

Awesome!

Install eiciel with --no-install-recommends to avoid loads of cruft ;)

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/ThunarCustomActions](https://help.ubuntu.com/community/ThunarCustomActions)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012432](http://ubuntuforums.org/showthread.php?t=2012432)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

