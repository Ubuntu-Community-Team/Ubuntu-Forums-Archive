---
title: "Rsync Backup Permissions problem"
date: 2010-12-04
forum: Server Platforms
---

### Post by ductiletoaster on 2010-12-04
I wrote a script to wake up my windows machine and do an rsync backup of some of my files. I wanted to make this command a accessible through local bin so i made it executable. However the problem is that when i copies files is copies them with root permissions and i can edit or delete them. 

How can i set the files so they transfer with the proper permissions for my Ubuntu user? 

```
#!/bin/bash
# Description: This script first wakes up the client machine and syncs the appropiate folders. 
# Finally the script shuts down the client if it was off to begin with.

if [ "$(whoami)" != "root" ]; then
        echo "Permission Denied" 
        exit 1
fi

# Default Variables
IP_ADDRESS="192.168.1.180"
MAC_ADDRESS="AA:BB:CC:DD:EE:FF"
MOUNT_SHARE="/mnt/windowshare"

ping -c3 $IP_ADDRESS
if [ $? -ne 0 ]; then
        wakeonlan $MAC_ADDRESS # Wakes Windows Client
        client_status=0 # Sets the computers status to was OFF
        sleep 120 # Waits 2 mins for the computer to boot
else
        client_status=1 # Sets the computers status to was ON
fi

smbmount //$IP_ADDRESS/D$ $MOUNT_SHARE -o username=user,password=pass # Mounts Windows Share

# Synchronizes All direcotries between both computers
rsync -ruz --delete --progress --exclude-from=/home/brian/.rsync/exclude $MOUNT_SHARE/Development/* /home/brian/Development/
#rsync -ruz --delete --progress --exclude-from=/home/brian/.rsync/exclude $MOUNT_SHARE/Downloads/* /home/brian/Downloads/ 
rsync -ruz --delete --progress --exclude-from=/home/brian/.rsync/exclude $MOUNT_SHARE/Documents/* /home/brian/Documents/
rsync -ruz --delete --progress --exclude-from=/home/brian/.rsync/exclude $MOUNT_SHARE/Music/* /home/brian/Music/
rsync -ruz --delete --progress --exclude-from=/home/brian/.rsync/exclude $MOUNT_SHARE/Pictures/* /home/brian/Pictures/
#rsync -ruz --delete --progress --exclude-from=/home/brian/.rsync/exclude $MOUNT_SHARE/Videos/* /home/brian/Videos/ 
rsync -ruz --delete --progress --exclude-from=/home/brian/.rsync/exclude $MOUNT_SHARE/Public/* /home/brian/Public/

umount //$IP_ADDRESS/D$ # Unmounts Windows Share

if [ $client_status -eq 0 ]; then
        net rpc SHUTDOWN -I $IP_ADDRESS -U user%pass # Shutsdown Windows Client
fi

```

---

### Post by CharlesA on 2010-12-04
Windows permissions and Linux permissions do not mesh well. You could try to mount the share as your user, but I'm not quite sure how that is done.

I do a similar thing, except I have to going to opposite way - Telling Windows to sync a folder to a Samba share on my server.

What version of Windows do you have on that machine?

---

### Post by ductiletoaster on 2010-12-04
Sorry it took me so long to reply. On my server im running Ubuntu 10.04 and the client (one being backed up) is Windows 7.

Normally i would later do a recursive chmod.... but  i hate doing this because its "dangerous" so I try to avoid it

---

### Post by CharlesA on 2010-12-04
If it's just data, you can do a chmod -R, but make sure you are in the correct directory first.

The way I have mine set up is this:
Robocopy from local drive to network folder and then that folder is rsynced to server's backup.

---

### Post by ductiletoaster on 2010-12-04
many times the rsync just copies data however there are times where a directory will be backedup too. but im going to look into mounting the windows share as my user... honestly its not a huge deal. If i want to edit the files or what not i just have to chmod. 

Though i was thinking that the share gets mounted to
/mnt/windowshare

which is in a directory that is owned my root.... so could i either 
a) move the mount point somewhere where my user has access 
or 
b) give my user permissions to that /mnt/windowshare.

The only reason i had it at in the mnt folder and made the script executable was in case I ever added another user it would be easily accessible to that user too...

---

### Post by CharlesA on 2010-12-04
Gotcha. :)

---

### Post by ductiletoaster on 2010-12-05
Ok so I found that rsync has the ability to chmod on the fly.... but im trying to figure out how would i give my user permissions if the program is running as root

---

### Post by CharlesA on 2010-12-05
> **ductiletoaster said:**
> Ok so I found that rsync has the ability to chmod on the fly.... but im trying to figure out how would i give my user permissions if the program is running as root
I use rsync --archive to preserve permissions, owner and group, but as far as I know, that would only work if you are copying from a file system that supports linux permissions.

---

### Post by ductiletoaster on 2010-12-05
Thanks for your help.... I kinda figured out what to do... Just playing around with it. chown allows me to set the permissions of group and user so i can do that.

Next I have to give read write permissions 

Im hoping i set it up so rsync can do it on the fly instead of having to recursively do it after copying.

---

