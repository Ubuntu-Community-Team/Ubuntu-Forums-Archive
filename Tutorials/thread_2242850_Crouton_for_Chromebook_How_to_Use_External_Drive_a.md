---
title: "Crouton for Chromebook: How to Use External Drive as Semi-Permanent Storage"
date: 2014-09-04
forum: Tutorials
---

### Post by barnett-andrew on 2014-09-04
Hey guys/gals,
As a new Linux user, one of my immediate goals was to use a 64GB SD card to increase the usable storage on my HP Chromebook 14 from the measly 16GB the internal SSD provides. I installed Ubuntu Trusty (Tahir) using Crouton. After much trial and error, this is the process that worked for me. It's likely not the most elegant solution, so if any more experienced users have tips on how to smooth the process, feel free to add them here. I do not have a USB drive handy but I believe this process would work with any form of external storage and not just an SD card.


All references to the user account folders are renamed “you” for purposes of this guide.


**[SIZE=3]Necessary Programs:[/SIZE]**
Keep in mind that this can probably be done using the terminal if you're comfortable using it.
1.GParted (or some other partition manager)
2.Kuser (or some way to manage groups)


Note: This guide assumes the only permanent storage you will be using besides the internal SSD is an SD card. /dev/sda refers to the internal SSD while /dev/sdb refers to the first mounted external storage (this continues with /dev/sdc and so on...)


**[SIZE=4]Step 1:[/SIZE]**
Format the SD card/external drive as ext4. GParted is very intuitive. Be careful to format the correct drive (you change it in the upper right hand corner of the screen). Log out of Crouton and completely restart the computer from Chrome OS.


[IMG]http://i60.tinypic.com/16k2r9z.png[/IMG]


[SIZE=4]**Step 2:**[/SIZE] 
Log back in to Crouton and change your group settings. Open KUser, click on the groups tab, and add a new group. For my purposes, I created a group with the same name as my username. Add your current user (the one you plan on using) to the group. Log out of Crouton and completely restart the computer from Chrome OS.

Note: Upon start, KUser may pop up an error message: “Error opening/etc/shadow for reading.” This is fine. Continue anyways.


[IMG]http://i59.tinypic.com/2dtztc5.png[/IMG]


**[SIZE=4]Step 3:[/SIZE]**
Open your file manager and navigate to /mnt/
Create a new folder called “external”


Do not restart again until step 5 is complete.


[IMG]http://i59.tinypic.com/2uz5nyp.png[/IMG]


**[SIZE=4]Step 4:[/SIZE]**
Ensure Show Hidden Files is enabled in your file manager. Making a file hidden is very easy in Ubuntu and, for this purpose, we will do so. Navigate to /home/*you*/.config/autostart/ and create a new text file.


Paste in the following text, being sure to change “you” to your username:


```
[DesktopEntry]
Type=Application
Exec=sh "/home/*you*/.sdcard/sd-start.sh"
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_IN]=SDStart
Name=SDStart
Comment[en_IN]=
Comment=

```

Save it with the name "sdstart.desktop"

Do not log out or restart your Chromebook between this step and the next.


[IMG]http://i58.tinypic.com/2yw5u78.png[/IMG]


[SIZE=4]**Step 5:**[/SIZE]
Navigate to /home/*you*/ and create a folder with the name .sdcard
Inside this folder, create a new text file.
Paste in the following text, being sure to change “you” to your username:


```
sudo umount /dev/sdb1
sleep1
sudo chown -R *you*:*you* /mnt/external
sleep2
sudo mount /dev/sdb1 /mnt/external

```

Save it with the name sd-start.sh

Log off and restart your Chromebook completely.


[IMG]http://i57.tinypic.com/2hn3u5e.png[/IMG]


Upon next login (and all future logins), your external drive should immediately mount under /mnt/external. This is handy as now all programs can access it and files stored have full read/write permission. You can check that it was successfully mounted by opening terminal and typing in ```
mount | grep sdb1

```

[IMG]http://i57.tinypic.com/34qu3jo.png[/IMG]


[SIZE=3]**Caveats:**[/SIZE]
If you log out of Crouton and put Chrome OS in sleep mode before the SDcard finishes unmounting, the computer will remount it under /dev/sdc upon next login. There are two ways to fix it: The first is simply to restart the computer completely. The second is to physically pop the SD card out while in Chrome OS, then pop it back in and log back into Ubuntu.

---

### Post by connor-jolley1980 on 2015-01-30
Does the file system have to be ext4?

I have a 128GB SD and gparted simply will not format it it to ext4, I have to break the operation, eject the SDC then format it is FAT 32 :(

---

### Post by jacob61 on 2015-03-12
I fixed this by doing it as the superuser. 

I just created an account to say this and ask you if you ever figured it out, connor-jolley1980. I don't know how to do code yet but here's what you can do:

sudo gparted

I think that's what did it for me.

Anyway, barnett-andrew, this didn't work for me. I do not know why.

---

