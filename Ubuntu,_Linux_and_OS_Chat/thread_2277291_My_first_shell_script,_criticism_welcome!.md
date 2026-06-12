---
title: "My first shell script, criticism welcome!"
date: 2015-05-07
forum: Ubuntu, Linux and OS Chat
---

### Post by livin2chill on 2015-05-07
[COLOR=#000000][INDENT]Hello Ubuntu forums! ):P
I am new to Ubuntu, and so far have done several things I am quite proud of:

[LIST]
[*]Made an apache webserver with my own html (before a week ago I had never touched it)
[*]Made a stratum mining server +titcoin node
[/LIST]

And my latest project is making a shell script to backup my ENTIRE (that’s right) hard drive to a huge external one. Getting to the point, I know there’s quite a bit I could improve on, and I would like your opinion on it: 

Code:
[SIZE=1]#!/bin/bash
[/SIZE][SIZE=1]read -n1 -p “Would you like to back up your system? Uno for Si, and Dos for No.” input[/SIZE]
[SIZE=1]echo[/SIZE]
[SIZE=1]case $input in[/SIZE]
[SIZE=1]  1)  fdisk -l;[/SIZE]
[SIZE=1]      echo;[/SIZE]
[SIZE=1]      read -p “Please enter the name of your backup disk that was displayed in the fdisk window: ” disk ;[/SIZE]
[SIZE=1]      echo;[/SIZE]
[SIZE=1]      echo “Backups now in progress! Please be aware that backups are saved to a Backups directory which this script creates, and backups are tarred and labelled by date!”;[/SIZE]
[SIZE=1]      echo “THIS WILL TAKE A VERY VERY LONG TIME IF YOU HAVE A LARGE FILESYSTEM! PLEASE BE PATIENT!!!”;[/SIZE]
[SIZE=1]      cd /;[/SIZE]
[SIZE=1]      sudo mkdir -p /mnt/$disk && sudo mount /dev/$disk /mnt/$disk && sudo mkdir -p /mnt/$disk/Backups && sudo tar -cp $(date +%Y%m%d).tar --directory=/ --exclude=proc --exclude=sys --exclude=dev/pts --exclude=backups . && sudo cp $(date +%Y%m%d-%H).tar /mnt/$disk/Backups;[/SIZE]
[SIZE=1]      echo “Okay, all done! To restore your system, you will have to untar and manually do it yourself. If you have any issues, email [email]harmius@icloud.com[/email]!”;;  [/SIZE]
[SIZE=1]   2) echo “Then why are you running this script?”;;[/SIZE]
[SIZE=1]  *) echo “I'm sorry, but I can’t do that…”[/SIZE]

[SIZE=1]esac[/SIZE]
Honestly, I have no idea what I am doing. Any suggestions?[/INDENT]


[/COLOR]

---

### Post by papibe on 2015-05-07
**Thread closed**. Duplicated thread here: [http://ubuntuforums.org/showthread.php?t=2277286](http://ubuntuforums.org/showthread.php?t=2277286)

Please do not post duplicates. Besides diluting the community effort, it is very difficult to provide any consistent help.

Please continue the conversation on the other thread.

Regards.

---

