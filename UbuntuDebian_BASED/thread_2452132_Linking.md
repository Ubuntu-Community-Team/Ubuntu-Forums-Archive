---
title: "Linking"
date: 2020-10-17
forum: Ubuntu/Debian BASED
---

### Post by Disabled20241022 on 2020-10-17
I'm running PopOS which uses SystemD and i'm a bit of a noob.
I have my 1 harddrive splitted into 2 partitions and i would like to link my second partition which has all of my files into my filesmanager ([https://wiki.gnome.org/action/show/Apps/Files](https://wiki.gnome.org/action/show/Apps/Files)) so that when i click 'Other' it will directly open the other partition but when i do this and i restart my system it doesn't work because it is automaticly unmounted.
So how do i create a permanent link in my file manager to the other partition?

And second question is how do i remove the current Documents folder from my main partition and then also have it looped to the second partition called 'Other' and open up that 'Documents' folder in the file manager?
All through the terminal please.

---

### Post by Disabled20241022 on 2020-10-25
anyone?

---

### Post by The Cog on 2020-10-25
Does this secons partition get mounted anywhere when you boot? 
If so, where does it get mounted? 
If not, how do you mount it?
Can you post the output of
> lsblk -fmap | grep -v snap

---

### Post by Disabled20241022 on 2020-10-25
Sure thing ```
NAME        FSTYPE FSVER LABEL   UUID                                 FSAVAIL FSUSE% MOUNTPOINT            SIZE OWNER GROUP MODE/dev/loop0                                                                                                      root  disk  brw-rw----
/dev/loop1                                                                                                      root  disk  brw-rw----
/dev/loop2                                                                                                      root  disk  brw-rw----
/dev/loop3                                                                                                      root  disk  brw-rw----
/dev/loop4                                                                                                      root  disk  brw-rw----
/dev/loop5                                                                                                      root  disk  brw-rw----
/dev/loop6                                                                                                      root  disk  brw-rw----
/dev/loop7                                                                                                      root  disk  brw-rw----
/dev/sda                                                                                                 465,8G root  disk  brw-rw----
&#9500;&#9472;/dev/sda1 vfat   FAT32         E8FE-765C                             399,5M    20% /boot/efi             500M root  disk  brw-rw----
&#9500;&#9472;/dev/sda2 ext4   1.0   PopOS   6bbf4096-48fa-42c8-a788-6724b4bfd120   85,1G     8% /                     100G root  disk  brw-rw----
&#9492;&#9472;/dev/sda3 ext4   1.0   Overige 878b409f-e397-4323-a3b9-21bb5c1e1489  167,8G     9% /media/erik/Overige   200G root  disk  brw-rw----
/dev/sr0                                                                                                  1024M root  cdrom brw-rw----



```

It does not get mounted, i need to mount it by pressing 'Overige' in my filemanager which is the name of that partition (meaning Others) and then it gets mounted and automaticly it opens the partition in the filemanager.
When i reboot it is unmounted again.

It is mounted at: /dev/sda3

---

### Post by The Cog on 2020-10-26
It might be best to just mount the partition into your home directory when the computer boots. No other users will be able to mount the partition though. If this solution is OK with you, I think this will do the trick:
Create a folder in your home directory for it to be mounted into:
```
mkdir /home/erik/Overige
```
Then add this line to /etc/fstab (e.g. sudo nano /etc/fstab):
```
UUID=878b409f-e397-4323-a3b9-21bb5c1e1489  /home/erik/Overige  ext4  defaults  0  2
```
The above should make the partition mount there when the computer boots, but you can make it mount without booting with:
```
sudo mount -a
```

For the Documents folder, with this solution you could just copy your Documents folder into Overige. Dragging files or folders into or out of Overige will make copies, not move them. But you could drag-copy things and then delete the original, or perhaps use cut and paste in the file manager.

---

### Post by Disabled20241022 on 2020-10-27
Might this also work?
```
LABEL=Overige  /home/erik/Overige  ext4  defaults  0  2 
```

For the folders i actually meant, how do i remove Recent, Starred, Afbeeldingen, Muziek, Video's, Documenten from filemanger using the terminal?
And how do i add the Overige link inside the filesmanagers left list where the above links are? so that i can go there right away.
How do i automaticly have the filesmanager open up Overige instead of Home?

Edit:
Thanks! it works. (only the auto mounting)


My 'Home' folder has these folders:
- Afbeeldingen (pictures)
- Bureaublad (desctop)
- Documenten (documents)
- Downloads
- Muziek (music)
- Openbaar (public)
- Sjablonen (templates)
- Video's
- Overige (the second partition that we just mounted)

How do i delete the current video, music, document location from these folders in Home and have the address changed to the same name folder on the second partition called Overige? (so Home > Documenten but this documenten should be opened on the second partition and the current partition of Home should have those folders deleted as a path but not as a folder that goes to the second partition)

And then also have the same icons from the old Home folders inside the new Home folder (icons)

PopOs (unbuntu) puts screenshots automaticly in Afbeeldingen (pictures in english) when i manually delete this folder it saves the screenshots in Home, i recon that when we do the above (change the location of these folders) they will automaticly be put inside a old but now deleted directory, how do i Safe these screenshots inside the new location on my second partition in there own folder? (documents in the documents folder ec.)

The same happens with libreoffice files, they are saved inside Documenten (documents) but i want to change the default path to Overige (Other. which is the second partition) how?

---

### Post by The Cog on 2020-10-28
I think that's two parts.
1: Move the Documenten folder to the Overige folder. This means your home folder no longer contains a Documenten folder.
2: Make a symbolic link in your home folder pointing to the Overige/Documenten folder:
```
cd     # make sure you are working in your home directory
mv Documenten Overige/Documenten
ln -s Overige/Documenten Documenten
```

---

### Post by Disabled20241022 on 2020-11-08
Doesn't work
I did this for it to work:

Create /home/erik/.config/user-dirs.conf
```
enabled=false
```
**But do i really need this file?**

Change /home/erik/.config/user-dirs.dirs to
```
XDG_DESKTOP_DIR="$HOME/Bureaublad"XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_DOCUMENTS_DIR="/home/erik/Overige/Documenten"
```

Change /home/erik/.config/gtk-3.0/bookmarks to
```
file:///home/erik/Overige Overige
```

Could somebody tell me how i make all of this inside a script to run?

And how do i open the filesmanger in a different (default) directory? (home/erik/Overige)

Edit: i also could not find how to remove 'Recent' and 'Starred', do any of you know how this is done?

---

### Post by Disabled20241022 on 2020-11-17
Does anyone have a clue?

---

### Post by Disabled20241022 on 2020-11-24
Help please......

---

### Post by oldfred on 2020-11-24
I have never changed my .config/user-dirs.dirs.

Very first time I moved all data from my folders in /home to my data partition and then deleted old folder in /home. Tested first with one smaller folder.
I had backup just in case.
And then mounted data partition in /mnt/data (could be anywhere) and linked from data partition folder back into /home. Once that worked I did the rest.
But now scripted it as I do it with every new install and know data partitions in /home are empty.

More details.
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Disabled20241022 on 2020-12-02
> **ayudha said:**
> Doesn't work
I did this for it to work:

Create /home/erik/.config/user-dirs.conf
```
enabled=false
```
**But do i really need this file?**

Change /home/erik/.config/user-dirs.dirs to
```
XDG_DESKTOP_DIR="$HOME/Bureaublad"XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_DOCUMENTS_DIR="/home/erik/Overige/Documenten"
```

Change /home/erik/.config/gtk-3.0/bookmarks to
```
file:///home/erik/Overige Overige
```

Could somebody tell me how i make all of this inside a script to run?

And how do i open the filesmanger in a different (default) directory? (home/erik/Overige)

Edit: i also could not find how to remove 'Recent' and 'Starred', do any of you know how this is done?

But those links don't address this...

---

### Post by oldfred on 2020-12-02
I do not change /home/fred/.config/user-dirs.dirs
Then these still show in file browser.

```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

```
[FONT=monospace][COLOR=#000000]ls -l /mnt  # I have others but this is for linking.[/COLOR]
[FONT=monospace][COLOR=#000000]drwxrwxrwx 17 fred fred 4096 Oct 19  2019 [/COLOR][COLOR=#1818b2]data[/COLOR]
[/FONT][/FONT]
```

Then in /home I have the links to the folders that are in the /mnt/data above.

Example but many (l means it is a link):

```
[FONT=monospace][COLOR=#000000]lrwxrwxrwx 1 fred fred    19 Oct 14 19:37  [/COLOR][COLOR=#54ffff]**Documents**[/COLOR][COLOR=#000000] -> [/COLOR][COLOR=#1818b2]/mnt/data/Documents[/COLOR]
lrwxrwxrwx 1 fred fred    19 Oct 14 19:37  [COLOR=#54ffff]**Downloads**[/COLOR][COLOR=#000000] -> [/COLOR][COLOR=#1818b2]/mnt/data/Downloads[/COLOR]
[/FONT]
```

If you follow the procedure I posted, then it works.

---

### Post by Disabled20241022 on 2020-12-03
Could you explain the meaning of [COLOR=#000000][COLOR=#000000][FONT=monospace]drwxrwxrwx 17 fred fred 4096 Oct 19  2019 [/FONT][/COLOR][/COLOR][COLOR=#1818b2][FONT=monospace]data
[/FONT][/COLOR]

---

### Post by oldfred on 2020-12-03
In my /mnt folder I create /mnt/data.
Then I add a mount of my data partition in fstab.
Details in links I posted above.

---

### Post by Disabled20241022 on 2021-01-24
I seriously can seem to make this work like i want it.

[B]Remove from filesmanager on ubuntu (popos):
[/B]Recent, Starred, Desktop, Afbeeldingen, Documenten, Muziek, Videos (all are in Home, except for Recent and Starred)

**Then add:** (these should be permanent, even on a restart, no manual mounting)Overige (dev/sda3)
Computer (/) but needs to be renamed to Linux

**Also, screenshots are automaticly saved in Afbeeldingen when i remove it screenshots are no longer working.** These should be saved in Downloads instead.


This way i only have:
- Home
- Linux
- Downloads
- Overige

---

### Post by oldfred on 2021-01-24
Not sure what you are trying to do.
When in file browser and default location of home you will see all the default folders plus any you add. You also can add bookmarks to other folders.
Different flavors of Ubuntu use different file browsers, so slightly different ways to configure them. 
Removing folders would require you to edit  ~/.config/user-dirs.dirs, but never seen that done & it may break some apps that expect default locations to save to.

---

### Post by Disabled20241022 on 2021-02-01
What i'm trying to do + a screenshot of where i want it to happen.
[ATTACH=CONFIG]287873[/ATTACH]
> **ayudha said:**
> I seriously can't seem to make this work like i want it. Can you?

[B]Remove from filesmanager on ubuntu (popos):
[/B]Recent, Starred, Desktop, Afbeeldingen, Documenten, Muziek, Videos (all are in Home, except for Recent and Starred)

**Then add:** (these should be permanent, even on a restart, no manual mounting)Overige (dev/sda3)
Computer (/) but needs to be renamed to Linux

**Also, screenshots are automaticly saved in Afbeeldingen when i remove it screenshots are no longer working.** These should be saved in Downloads instead.


This way i only have in filesmanager:
- Home
- Linux
- Downloads
- Overige

---

### Post by oldfred on 2021-02-01
I have Kubuntu and it uses Dolphin.
In Dolphin I bookmarked my / and edited it to be Kubuntu_root.
But I add a lot of bookmarks.
Just noticed Dolphin also has a hide setting.

What file browser are you using? 
But currently only using Dolphin. Use to use Naulitus in Ubuntu, but like Dolphin better. So cannot really help on any others.

---

### Post by Disabled20241022 on 2021-02-01
PopOS comes with Nautilus.

---

### Post by oldfred on 2021-02-01
Do not remember details on Naulitus.
But remember some comments about it was not as "good" as other file browsers. But it has been updated since then.

I would suggest trying Dolphin, but it has a long list of depends for kde &  libqt.... files
You can see that without install.
[FONT=monospace][COLOR=#000000]apt show dolphin[/COLOR]
[/FONT]

---

### Post by Disabled20241022 on 2021-07-02
Still trying to create a permanent link of my partition in filesmanger (on PopOS/Ubuntu), any help would be much appreciated.

---

### Post by vanadium on 2021-07-02
Hold "Ctrl+Shift" then drag a folder to a new location. When released, a symbolic link will be created. For your daily work, a symbolic link feels and acts like a regular folder. Symbolic links can also be created using a terminal command, e.g. "ln -s /mnt/data/Documents ~/Documents" would create a link "Documents" in your home folder that actually refers to a folder "Documents" on a separate partition mounted on the folder "/mnt/data".

The user does not need to know where the separate partition is mounted. Only the system administrator is concerned about that. A click on "Documents" brings the user seamlessly to the separate partition.

---

### Post by Disabled20241022 on 2021-07-03
This doesn' t really do what i wanted but i figured it out:

```
sudo lsblk -f
sudo nano /etc/fstab
UUID=YOURUID /media/YOURNAME/YOURFILE ext4 noatime 0 1
CTRL+O CRTL+X
Computer > media > YOURNAME > drag the FILE to your menu in your filesmanger
```

But i did not find a way to do this into the terminal.

---

### Post by tea for one on 2021-07-06
It looks like you want to add a bookmark of a partition to the left pane of Nautilus?

Open Nautilus > Other locations > Select desired partition > Click down arrow at right of partition name > Add to bookmarks

When the bookmark is added to the left pane, you can right click to remove or rename.

The partition must be automatically mounted when you log in - gnome-disk-utility will do this for you.

---

