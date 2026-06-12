---
title: "How To: Disk Full? - Check Your Trash"
date: 2008-08-23
forum: Tutorials
---

### Post by drs305 on 2008-08-23
[COLOR="MAROON"]**[SIZE="4"][CENTER]*Trash Problems and Solutions**[/CENTER][/SIZE]**[/COLOR]
* This guide was originally prepared under the title: *Disk Full? - Check Your Trash Bin(s)*. I wrote a subsequent guide dealing specifically with lost 'free' space and how to restore it. That guide can be found at: [Disk Space Problems & Solutions]("http://ubuntuforums.org/showthread.php?t=1122670")

**[COLOR="DarkGreen"][SIZE="3"]In a Rush and Sure It's a Trash Problem? Go Directly to #6 ...[/SIZE][/COLOR]**

**[COLOR="Navy"][SIZE="3"]1. Error Messages - Why You Are Here?[/SIZE][/COLOR] **
*"There is not enough room on the disk to save ..."* Perhaps you received an error message. Maybe you have tried but cannot delete the contents of the Trash bin. Perhaps you looked at your system files and realized that you were running out of disk space. Emptying the trash has been a tradition throughout the world since long before computers were invented. Over time we sometimes forget to do perform this important task. 

With computer trash, you have to not only remember to delete, you must know ***[COLOR="DarkRed"]how[/COLOR]*** to do it. If you cannot explain why you are running out of hard drive space, it may be because you haven't emptied the trash - properly, often enough, or perhaps both! Read on.

**[COLOR="Navy"][SIZE="3"]2. Shrinking Free Space - Common Causes [/SIZE][/COLOR]**
[LIST]
[*]Undeleted trash.
[*]If you believe the cause of your problem is not a trash issue but your free space has unexpectedly decreased, please go to [Disk Space Problems & Solutions]("http://ubuntuforums.org/showthread.php?t=1122670"). 
[/LIST]

**[COLOR="Navy"][SIZE="3"]3. Checking Your Partition[/SIZE][/COLOR] **
Here are some of the many ways to check your free space. Each has its advantages. Use the one or combination you like the best.
[LIST]
[*]**[COLOR="DarkRed"][B][SIZE="1"]df -Th | sort[/SIZE]**[/COLOR][/B] (Terminal)
```

/dev/sda1     ext3     23G  9.6G   12G  46% /
/dev/sda2     ext3     34G  2.1G   30G   7% /home
/dev/sdg2  fuseblk    965M  5.4M  960M   1% /media/test
Filesystem    Type    Size   Used   Avail   Use%   Mounted on

```
Note: "sort" will order the partitions alphabetically. The "T" switch shows the file type - you can omit it if desired. If used, ntfs partitions will show type: "fuseblk".
 

[*]**[COLOR="DarkRed"][B][SIZE="1"]Gnome-Device-Manager[/SIZE]**[/COLOR][/B] (GUI)
System, Administration, System Monitor (gnome-system-manager) 
```

Device      Dir     Type   Total     Free      Available   Used     %
/dev/sda2   /home   ext3   33.1GiB   31.1GiB   29.4GiB     2.0GiB   6%

```


[*]**[COLOR="DarkRed"][B][SIZE="1"]Disk Usage Analyzer / aka Baobab[/SIZE]**[/COLOR][/B] (GUI)
Applications, Accessories, Disk Usage Analyzer.
This is a graphical app that displays hard drives and partitions.
While DUA is a valid tool, it often brings up questions about its use. Here are a couple of things to keep in mind:
[LIST]
[*] One common question is why DUA seems to show twice as much space as the partition contains. By default DUA It displays the .gvfs (gnome virtual file system) folder contents. To get an accurate picture of the actual/physical contents, uncheck ".gvfs" via Edit, Preferences.
[*] The top directory will *always* show 100% full. The percentages of all the folders adds up to 100%. It does not mean there is no space left on the drive/partition.
[/LIST]


[*]**[COLOR="DarkRed"][B][SIZE="1"]Find Large Files[/SIZE]**[/COLOR][/B] 
If you think you might have one or more large files taking up space, you can search for large files with the following commands. If you want to decrease the search file size, replace 'G' (gigabyte) with 'M' (MB). An initial installation will not have files larger than 500MB on the partition. Examples: 
```

sudo find / -name '*' -size +1G
sudo find / -name '*' -size +500M

```
[/LIST]
 

**[COLOR="Navy"][SIZE="3"]4. Trash Characteristics[/SIZE][/COLOR] **
Under normal circumstances, only files/folders deleted with the terminal "rm" command or via the Shift-Del key combination in file browsers such as nautilus or thunar are immediately erased - freeing up disk space. The rest go to a trash bin, where deleted materials remain until the bin(s) are emptied.

The Trash folders are hidden. If using the "ls" command in the command line, you must include the "-a" switch (ls -a). In nautilus or other file browsers, you must have "view hidden files" enabled (nautilus = Ctrl-H).

There are two folders within the Trash bin - "info" and "files".
[LIST]
[*]*info*: The "info" folder contains information regarding the files contained in the "files" folder. Each deleted file has an entry in the "info" folder, containing the deletion date and path. 
[*]*files*: This folder contains the actual deleted files.
[/LIST]

**[COLOR="Navy"][SIZE="3"]5. Why Must I Delete Trash?[/SIZE][/COLOR] **
***[COLOR="DarkRed"]Until the trash bins are emptied, deleted items continue to take up disk space just as a normal files do. The space containing these deleted items cannot be used as long as the deleted files reside in Trash bin(s).[/COLOR]***

If you want proof, find a suitably large file and make a copy of it. Using any of the methods above, review the free and used disk space and then delete the file via a file browser or right click/remove in a file browser. Recheck the results. You will notice the used and free space have not changed. The reason is because the deleted files in a Trash bin are still intact - they have only been moved to a different folder.

**[COLOR="Navy"][SIZE="3"]6. Okay, Where Are the Trash Files?[/SIZE][/COLOR] **
Here is where these files normally reside.

[LIST]
[*]**~/.local/share/Trash**   User's Trash (hardy and later)  
[*]**~/.Trash**         User's Trash (pre-hardy)  
[*]**/root/.local/share/Trash**             System Trash (hardy and later)  
[*]**/root/.Trash**                         System Trash (pre-hardy):  
[*]**/.local/share/.Trash-1000**            NTFS/FAT32/etc: Trash deleted in these partitions is placed in a Trash bin named in accordance with the user deleting the file, e.g. -1000, 1002, -0, etc  
[/LIST]
In a file browser, typing "trash:/" in the location window will take you to the user's  *trash* folder. 

All system trash, regardless of where it resides, by default contains the name "Trash". Here is a command that will greatly simplify your task. It seeks out all folders on your system that contain either "trash" or "Trash" while eliminating other files such as "trashapplet". It must be run with root privileges since it will be searching the system files. It does not require root privileges to be run on your home partition. It searches your entire system, so it may take a few minutes. Note: Since it finds *any* folder named *Trash*, it might find other non-system trash folders as well (such as an Evolution trash folder). 

```
[SIZE="4"][COLOR="DarkRed"]**sudo find / -type d -name *Trash* **[/COLOR][/SIZE]
```
[LIST]
Here is an example run on my computer:
```

~/Desktop: sudo find / -type d -iname *Trash* | grep Trash
/media/data/.Trash-1000
~/.local/share/Trash
/home/.Trash-0
/root/.local/share/Trash

```
[/LIST]

**[COLOR="Navy"][SIZE="3"]7. How Do I Delete Trash and Free Up Space?[/SIZE][/COLOR] **
[LIST]
[*][SIZE="2"]The Safe Way: File Browser with Administrative Powers[/SIZE]
[LIST]
[*]**[COLOR="DarkRed"][SIZE="1"]gksudo nautilus[/SIZE][/COLOR]** (Terminal)
[LIST]
[*]Do not use "sudo". Sudo is meant to be used for terminal commands and processes. This command, even though run in terminal, will open a gui application. "gksudo" is the appropriate command.
[*]You can start nautilus with the folder path ( *gksudo nautilus ~/.local/share/Trash* ) It is necessary to navigate to each Trash folder to delete it's contents.
[*]Note: If *gksudo nautilus* does not work, forum member *SATXan* reports in Post #31 that the following command might work: *gksudo dbus-launch nautilus*
[*]Use Shft-Delete to delete individual folders/files. Confirm the "permanent delete" message. If you just hit the Delete key, the folders/files will be deleted and moved to the .... Trash/files folder! If you delete the parent *Trash* folder, this is not necessary. A simple press of the Delete key will remove the Trash folder and subfolders.
[*]You may delete the entire Trash folder. It will be created the next time an item is deleted.
[*]Nautilus also can delete trash directly, bypassing the Trash bin.
[LIST]
[*]Edit > Preferences > Behavior tab > Trash 
[*]Include a right click option which allows a delete command which bypasses Trash 
[/LIST]
[/LIST]
[/LIST]

 
[*][SIZE="2"]The Efficient Way: Command Line[/SIZE] (with "chown" when required)
[LIST]
[*]**[COLOR="DarkRed"][SIZE="1"]Using the Terminal.[/SIZE][/COLOR]** By using commands in terminal you can quickly delete all user-owned Trash folders. Using the command line combines ease of use with a bit of risk. 

**[COLOR="Red"]You must ensure you have correctly input the command. Files deleted with the "rm" command are generally NOT recoverable![/COLOR]**
 

[*]**To delete *your* Trash contents in your home folder:**
```
**[COLOR="DarkRed"]rm -rf ~/.local/share/Trash/*[/COLOR]** 

```

[*]**To delete *root's* Trash contents in your home folder**:
Sometimes root trash ends up in your local Trash bin. You cannot delete this without administrative powers. To accomplish the task, use "sudo" to change ownership of the Trash folder contents to the user, then delete the folder as above:
```
[COLOR="DarkRed"][B]
sudo chown -R *username* ~/.local/share/Trash
rm -rf ~/.local/share/Trash/*[/COLOR][/B] 

```
 
[*]**To delete *root's* Trash contents in root's Trash bin:**
I recommend using nautilus or another file browser, opened with root privileges, to accomplish this task. Using the command line to delete system Trash is safe *only if* the command is entered properly. A mistake could possibly erase system files and render the system unusable.  

There are commands which will directly delete root trash using "sudo rm -rf" but I will not reproduce them here. A safer method is again to change the ownership to yourself and then delete the Trash. Of course, if you enter the wrong commands twice you can still destroy your system...

We will again use "sudo" to change ownership of the Trash folder contents to the user and then delete the folder as previously:

```
[B][COLOR="DarkRed"]
sudo chown -R *yourusername* /root/.local/share/Trash/
rm -rf ~/.local/share/Trash[/COLOR][/B] 

```

[/LIST]
[/LIST]
 
**[COLOR="Navy"][SIZE="3"]8. How to Make Trash Bins on NTFS / VFAT Partitions[/SIZE][/COLOR] **
A trash bin may automatically be created on NTFS and vfat partitions. It will be named by the UID of the user who deletes the trash - for example, .Trash-1000. Note that these are hidden folders (they begin with a . ) 

If you wish to create a trash bin in a non-Linux partition:
[LIST]
[*]In fstab, add "uid=<uid number>,gid=<gid number> to the partition options.
Example for a user with the UID of 1000 on a partition mounted at /media/myfiles (Note you can check with the "id" command in a terminal):
> UUID=8797e97ew8790q87e907q  /media/myfiles  ntfs  auto,users,umask=027,utf8,uid=1000,gid=1000  0  0 
[*]Create the trash folder in the specified partition. Example on a partition mounted as /media/myfiles:
```
mkdir /media/myfiles/.Trash-1000
```
[*]Reboot or umount/mount the specified partition.
[/LIST]


**[COLOR="Navy"][SIZE="3"]9. A Few Tips About Trash[/SIZE][/COLOR] **
[LIST]
[*]If your user Trash icon is not displayed on the Desktop, try this. Change the value to "false" to hide it.
```
[COLOR="DarkRed"]**gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"**[/COLOR]

```
[*]If the .Trash-1000 (or user's uid if different) folder exists in ntfs/fat32 partitions the contents should be displayed in the user's Desktop Trash bin.
[/LIST]



[COLOR="MAROON"]***[SIZE="2"]Other Useful Trash-Related Links:[/SIZE]***[/COLOR]
[SIZE="1"][HOWTO: Cleaning up all those unnecessary junk files]("http://ubuntuforums.org/showthread.php?t=140920&highlight=trash")
[DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
[HOWTO: Automatically regulate the size and age of your Trash folder]("http://ubuntuforums.org/showthread.php?t=698649&highlight=trash")
[A send-to-trash command for the shell. ]("http://ubuntuforums.org/showthread.php?t=124137&highlight=trash")[/SIZE]aa

---

### Post by Joeb454 on 2008-08-23
Moved to Tutorials & Tips.

Nice how-to :D

---

### Post by WRDN on 2008-08-28
A good How To. You need to alter the first location in section 6:

> /home/username/.share/local/Trash User's Trash (hardy and later)

This should be changed to:

> /home/username/.local/share/Trash

Alternatively, you may consider using "~/" when deleting file(s) in the home directory. This makes the command more portable and it can be copied and pasted. In some of the commands you posted, the user must enter their own username. This is not required.

Other than that, good job :)

---

### Post by drs305 on 2008-08-28
> **WRDN said:**
> A good How To. You need to alter the first location in section 6:
/home/username/.share/local/Trash User's Trash (hardy and later) 

This should be changed to:
/home/username/.local/share/Trash 


Alternatively, you may consider using "~/" when deleting file(s) in the home directory. This makes the command more portable and it can be copied and pasted. In some of the commands you posted, the user must enter their own username. This is not required.

Other than that, good job :)

I hate dyslexia -- thanks. 

I debated how to designate the home folder, but since you bring it up here and new users can read that **/home/*username * is equivalent to ~/**  I've gone back and simplified things.



[SIZE=3]Other Acknowledgements:[/SIZE] 

Martje_001: Thank you for your input. I have added a note in Section 6.

---

### Post by Martje_001 on 2008-08-29
It should be noted that #6 not always returns Trash folder. Like mine:
```
/home/martijn/Downloads/.Trash-1000
/home/martijn/.local/share/Trash
--> /home/martijn/.evolution/mail/imap/martijxxxx@xxxxx@imap.xxxx.com:993/folders/Trash <--
/home/martijn/Documenten/.Trash-1000

```

---

### Post by Crafty Kisses on 2008-08-29
Nice, really smooth and well explained. :)

---

### Post by dukebytes on 2008-12-08
Great how to and thanks!!

Duke

---

### Post by SeanHodges on 2008-12-15
Excellent HOWTO, very informative.

Noticed a typo in section 5 ("Why Must I Delete Trash?"):

"Reheck the results"

Should be "Recheck"


Thanks!

---

### Post by PeeZz on 2009-01-03
Thanks!! (I would thank you with the button, but it's gone :) )

This helped me a lot:
> **drs305 said:**
> 
[LIST]
[*]**[COLOR=DarkRed][B][SIZE=1]Check Your Log Files[/SIZE]**[/COLOR][/B] Take a look in /var/log and subfolders and see if an excessive number of small log files are being generated. You can run the following to see the size of each subfolder:
```

du -h /var/log

```If you find a particularly large log file and you don't want to delete it, you can remove its contents while keeping the file structure intact with the following command (hat tip to *lensman3*:
```

cp /dev/null /var/log/[COLOR=DarkRed]log_filename[/COLOR].log

```
[/LIST]


---

### Post by drs305 on 2009-01-03
> **PeeZz said:**
> Thanks!! (I would thank you with the button, but it's gone :) )  This helped me a lot:

I appreciate your note. Normally I read the responses but don't comment unless there is a question or I need to update the original post. But since you mentioned it, the 'thanks' button times out after so many days/months (I dont't know the number) and thus becomes unavailable.

---

### Post by PeeZz on 2009-01-04
Well it seems I can thank you now ;)

---

### Post by Martje_001 on 2009-01-04
I think you forgot to login :P

---

### Post by heindsight on 2009-01-11
> **drs305 said:**
> 
```
[SIZE="5"][COLOR="DarkRed"]**sudo find / -type d -iname *Trash* | grep Trash**[/COLOR][/SIZE]
```
[LIST]
Here is an example run on my computer:
```

~/Desktop: sudo find / -type d -iname *Trash* | grep Trash
/media/data/.Trash-1000
~/.local/share/Trash
/home/.Trash-0
/root/.local/share/Trash

```
[/LIST]


Is there a particular reason for searching case-insensitively and then piping the output through 'grep Trash' (which is case-sensitive)? Surely you could achieve exactly the same result by just doing:
```
find / -type d -name "*Trash*"
```

---

### Post by drs305 on 2009-01-11
You are correct. As I originally wrote it the trash bins were being renamed/relocated and I wanted to make sure I found anything related to trash, whatever the spelling (thus the case insensitivity). However, the grep wasn't eliminated from an earlier 'formula'. I'll update the command although I will keep the -iname. Thank you for pointing this out.

---

### Post by heindsight on 2009-01-11
> **drs305 said:**
> I'll update the command although I will keep the -iname.

If you keep the iname, you might want to add a warning that this will also find directories that do not contain trash, such as gconf entries for the trash applet under ~/.gconf/... and
```

/usr/share/gnome/help/trashapplet
/usr/share/omf/trashapplet

```

---

### Post by drs305 on 2009-01-11
> **heindsight said:**
> If you keep the iname, you might want to add a warning that this will also find directories that do not contain trash, such as gconf entries for the trash applet under ~/.gconf/... and
```

/usr/share/gnome/help/trashapplet
/usr/share/omf/trashapplet

```

Since users following this post will probably be relatively inexperienced and the trash folders continue to be named 'Trash', I'll concede the point.

---

### Post by inspired on 2009-02-03
Thanks for this.
Very helpful and much appreciated.
:popcorn:

---

### Post by shane2peru on 2009-02-05
> **drs305 said:**
> 
[*]**[COLOR="DarkRed"][B][SIZE="1"]Find Large Files[/SIZE]**[/COLOR][/B] 
If you think you might have one or more large files taking up space, you can search for large files with the following commands. If you want to decrease the search file size, replace 'G' (gigabyte) with 'M' (MB). An initial installation will not have files larger than 500MB on the partition. Examples: 
```

sudo find / -name '*' -size +1G
sudo find / -name '*' -size +500M

```
[/LIST]
 


Thanks!!!  This piece of info was extremely valuable!  Excellent guide.

Shane

---

### Post by drs305 on 2009-02-05
You are welcome Shane. This post was originally just about finding and deleting Trash. Over time it expanded to include other methods of researching problems concerning disk space.

I am in the process of writing a new tutorial on solving disk space issues and will trim this post back to just trash issues. So feedback on techniques that work (or don't) are most helpful.

---

### Post by Ian Clark on 2009-05-18
1. gksudo then going to the trash folder shows no files in my trash, but when clicking the trash icon there are still two folders listed as being in my trash.
2. sudo empty-trash returns no errors, but the two folders are still in my trash.

Any suggestions?  Screenshots attached.

---

### Post by Vimmander on 2010-08-15
By running:
```
sudo find / -type d -name "*Trash*"
```or
```
sudo find / -type d -iname *Trash* | grep Trash
```or
```
sudo find / -type d -iname *Trash*
```I get nothing.  The only thing that happens is that I get the prompt back (the me@wherever:~$ thing)

What's up with that?  I've no need to clean up these Trash folders now, but it's cool to find stuff anyway :)

---

### Post by drs305 on 2010-08-15
> **GrogTheDreamer said:**
> What's up with that?  I've no need to clean up these Trash folders now, but it's cool to find stuff anyway :)

I don't know. Even if you don't have Trash folders my search using the last command comes up with several *trashapplet* hits. You could replace **Trash** with the name of a filename you know exists just to see if the command works on other names.

---

### Post by sundays211 on 2010-09-17
for some reason every time I try to delete the files in /home/.trash-0 as root they just re-appear when using the file manager. by using the terminal it works fine, but not using the GUI. also, why does this trash folder contain files that I deleted ages ago, and I also emptied them from my trash (or so I thought).

---

### Post by drs305 on 2010-09-17
> **sundays211 said:**
> for some reason every time I try to delete the files in /home/.trash-0 as root they just re-appear when using the file manager. by using the terminal it works fine, but not using the GUI. also, why does this trash folder contain files that I deleted ages ago, and I also emptied them from my trash (or so I thought).

To permanently remove trash from the trash bin folders Nautilus you have to use SHIFT-DEL instead of just DEL. When you press just the DEL key, the files are deleted but then return to the same location a few moments later. Whether this is by design or not I don't know. When you use the SHIFT-DEL method, the files are removed permanently. 

There is an option in Nautilus under Edit > Preferences which includes adding a DEL option which bypasses the Trash bin. If you are using that and the files still end up in the Trash, it could be a bug and you should probably see if it's been reported in Launchpad.

For the second question, emptying the Trash bin used to only include the trash in the Ubuntu/linux trash bin (~/.local/share/Trash and, as root, /root/.local/share/Trash ). This trash bin contains deleted files from your linux partition(s) and did not include trash from other filesystems (FAT, NTFS, etc), which are stored in separate folders (such as .Trash-0). I thought that the newer releases of Ubuntu had provisions for this or there was a workaround but can't say for sure without doing some research.

---

### Post by sundays211 on 2010-09-17
thanks
SHIFT-DEL permanently removes the files. and now that I think about it, all those files appear  to be from my "data" drive, which is not permanently mounted.
anyways, your guide was a lot of help. I was very close to re-installing everything because my /home partion was nearly full of these files.

---

### Post by theronb on 2010-10-03
Thanks! Very easy to follow - not only solved my problem but I learned a lot.

---

### Post by meanmrmustard on 2011-12-21
Excellent guide, thanks much.

After following relevant topics here and recovering about 4% of /, I discovered that files I had deleted were still taking up space despite not being accessible.
Thanks to some mailing list help, I ran "sudo lsof / grep '(deleted)'"
and found over 20G of recoverable space.
Once I knew the problem I simply killed the process IDs for each file and / was back to 20% use.

---

### Post by drs305 on 2011-12-21
> **meanmrmustard said:**
> Excellent guide, thanks much.

After following relevant topics here and recovering about 4% of /, I discovered that files I had deleted were still taking up space despite not being accessible.
Thanks to some mailing list help, I ran "sudo lsof / grep '(deleted)'"
and found over 20G of recoverable space.
Once I knew the problem I simply killed the process IDs for each file and / was back to 20% use.

Thanks for sharing the command.  :-)

If you would elaborate a bit perhaps I could add it to the original post. 

Didn't using SHIFT-DEL in a root browser work to permanently remove the files, or were they not visible even in the browser? 

Also, although I don't type the complete command here lest someone makes a mistake and erases their entire OS, did you try the 'rm' command as root to remove files from root's trash bin (/root/.local/share/Trash)?

Finally, once you used the lsof command, how exactly did you use the results to remove files which weren't removed via other methods. 

Thanks again for posting.

---

### Post by meanmrmustard on 2011-12-22
> **drs305 said:**
> Thanks for sharing the command.  :-)

If you would elaborate a bit perhaps I could add it to the original post. 

Didn't using SHIFT-DEL in a root browser work to permanently remove the files, or were they not visible even in the browser? 

Also, although I don't type the complete command here lest someone makes a mistake and erases their entire OS, did you try the 'rm' command as root to remove files from root's trash bin (/root/.local/share/Trash)?

Finally, once you used the lsof command, how exactly did you use the results to remove files which weren't removed via other methods. 

Thanks again for posting.

First, I'm sorry, I mis-typed the command.
It is actually "sudo lsof / | grep deleted" which is non-destructive and only searches "/" to find any files marked "(deleted)".


For whatever reason these files, although deleted, were still claiming space on the root partition.

The "sudo df -h /" command showed / as being 26G
but running "sudo du -xhs /" showed the actual size, around 5G.

According to my helper, this showed that, "most likely" there were deleted files still occupying space.
I think it may also have been important that other partitions (all but / and /home)were unmounted before running all commands.

These files were not visible using nautilus or vim as root.

I was told that all I needed to do was to kill each program to reclaim the space.
I did this by running "top" then entering "k" followed by each PID - which was shown in the second column of the result of the "lsof..." command, the first column shows the program name.

I just ran it again to show an example of the output:
chromium- 21460       curt  558u   REG    8,1     4104  687586 /var/tmp/etilqs_UZLJE6m0NTfoQj1 (deleted)

Only guessing but I believe the files in /var would have disappeared had I simply re-booted.

The command found over 20G of files in /tmp, /usr/share/applications, /var/tmp and /var/lib.
I have no understanding of how these files were created or why they remained after being deleted.
Maybe someone can enlighten me.

Root's trash was removed using <shift> <delete>... and no, I didn't try "rm" to remove them.

Another helper suggested installing ncdu (Ncurses Disk Usage, more info at [http://dev/yorhel.nl/ncdu](http://dev/yorhel.nl/ncdu)) which gives more accurate info in an easy to read format.
The command "sudo ncdu -x /" showed the contents of the / partition - the switch "-x" limits the search, in this case to "/" only.

Hope my explanation was clear.

---

### Post by drs305 on 2011-12-22
> **meanmrmustard said:**
> 
Hope my explanation was clear.

Yes, thanks. I'll digest them when I have a bit of time. 

Happy Holidays.

---

### Post by SATXan on 2012-01-13
Thanks for creating and maintaining this resource.

I recently ended up with some files in root Trash that stubbornly would not be removed.  They were placed there due to a stupid noob trick I managed using Clonezilla wherein I used root as a target for a backup (yeah, seemed like a good idea at the time :P)  This wasn't much more than annoying until I decided to move the system to a (small) SSD.  Now that 20+GB was a big deal.

I followed all the instructions here but the root Trash just would not delete.

I finally found a link that suggested a tweak to the command line for nautilus:

```
gksudo dbus-launch nautilus
```This allowed me to delete the offending files in Trash, never to be seen again.

I'd give attribution to where I found this tidbit, but I lost the URL in the flurry of searches and curses I was spewing at the time... :(

I don't pretend to truly understand why this worked in my circumstance, but maybe it would be helpful to others who've exhausted the other options.

Thanks.

---

### Post by drs305 on 2012-01-13
SATXan,

Thanks for sharing this and welcome to the Ubuntu Forums. :-)

In recent versions of Ubuntu running Nautilus as root is sometimes problematic. Installing nautilus-gksu normally allows troublefree opening of folders as root by right clicking, but often users aren't aware of the nautilus-gksu package.

I'll add your command in the original post. Thanks for the contribution!

---

### Post by liangliming on 2013-05-23
I am a new to linux and met the no space problem this eveing. Its very helpful for me to solve it!

---

### Post by drs305 on 2013-05-24
> **liangliming said:**
> I am a new to linux and met the no space problem this eveing. Its very helpful for me to solve it!

I'm glad this old thread still has some value.

Welcome to the Ubuntu Forums *liangliming*.  :-)

---

