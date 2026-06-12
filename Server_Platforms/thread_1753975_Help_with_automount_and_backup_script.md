---
title: "Help with automount and backup script"
date: 2011-05-09
forum: Server Platforms
---

### Post by cryptrat on 2011-05-09
I am trying to set up a file server.
 
I have been working on writing a script that would auto mount and backup files to at this time just a usb drive.
 
I have a working udev rule to start the script. It loads the script and it runs alright, but it is very crude as I am a novice at this still.
 
I am trying to see if I could get any suggestions on cleaning the script up.
 
#!/bin/bash
sleep 5
if grep -q '/usbdrive' '/proc/mounts'
then
while grep -q '/usbdrive' '/proc/mounts'
do
sleep 5
cd /usbdrive
ls
sleep 5
sudo rsync -av --progress --log-file=/sync.log /files /usbdrive
sleep 10
sudo /bin/umount /usbdrive -l
sleep 30
sudo /bin/mount UUID=CC41-3A37
done
 
I know it is very crude but it seems to work and as long as the usb drive is connected it will sync every 50-60 seconds, and the 30 sec on the end is so I can pull the drive after its done and unmounted.
 
I am very open to any suggestions on cleaning this up at all.

---

### Post by JonRohan on 2011-05-09
I couldn't tell you how to tidy the script up. However, I figured this could be a good mention for rsnapshot. :). 

If the script works I'm not sure if you'd want to change it much. I would be cautious of mounting a usb drive so often though. Maybe rsnapshot to a local backup disk and do a backup of that every 24 hours or so?

---

