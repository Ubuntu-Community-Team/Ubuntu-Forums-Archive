---
title: "how to exactly duplicate a system on another box"
date: 2008-05-10
forum: Server Platforms
---

### Post by nephish on 2008-05-10
Hey there all, 

I have a server at work. It is a website server. 
We have another computer that i want to make a backup in case our server catches on fire or something. It kinda took a bit to get the main stuff up and configured, so to avoid having to do all of that again... Is it possible to make an exact copy of our system onto another computers hardrive ? Thanks for any tips

---

### Post by cdtech on 2008-05-11
You could use rsync (thats what I use for my web server). I develop my site using my laptop and sync the results to the server. I run a backup script every night to backup my entire server using an external backup medium. All you would need to do is set up rsync to sync both drives at a particular time of the day. The sync will only update changed files on your backup drive.

This is a small script I use to sync my web server, I do it manually. You can set it up to run through roots cron or you could rewrite the whole thing. Just an idea for you to consider.

```
#!/bin/bash

# ----------------------------------------------------------------------
# I wrote this script to sync my laptop with my server. If I did any
# configuring on my laptop I could sync to the server using the 
# flag -u to upload the changes to the server and if I logged in via the 
# internet to do any configuring, I would just use my laptop to download
# the changes to my laptop using the -d flag.
# ----------------------------------------------------------------------

# ------------------------------------------------------------
# rsync options:
# ------------------------------------------------------------

# -r              : recursive
# -t              : preserve time
# -l              : symlinks as symlinks
# -p              : preserve permissions
# -v              : verbose
# -e /usr/bin/ssh : remote shell [ssh]
# -z              : compress data
# -n              : used for testing (used on it's own -n)
# --delete-after  : delete missing files on receiver
#                   after transfer complete
# --progress      : display progress

# ------------------------------------------------------------
# variables:
# ------------------------------------------------------------

#
# NOTE:
# if you change the variables, be sure to leave the trailing slashes on the
# dirup and the dirdown (rsync needs these) and the var “directory” has none.
#

options="-rtlpvz -e /usr/bin/ssh --delete-after --progress"
dirup="/var/www/"
dirdown="/var/www/wordpress/"
directory="/var/www/wordpress"
server="yourservername.com"
pn=`basename "$0"`
ver="ver 1.2"

usage ()
{
   echo "-----------------------------------------------------------------"
   echo >&2 "${pn} - sync web server from my laptop using rsync, ${ver}"
   echo "----------------------------------------------------------------""
            usage : ${pn} [-u] [-d]
           -u  upload files to web server
           -d  download files from server"
    exit 1
}

# getopt; used to validate arguments
set -- `getopt ud "$@"` || usage
[ $# -lt 1 ] && usage

# ------------------------------------------------------------
# main routine:
# ------------------------------------------------------------

        if [ "$1" = "-d" ]; then
           echo "----------- downloading web files ---------------"
           rsync ${options} ${server}:${dirdown} ${directory}
           echo "----------- download complete -------------"
        elif [ "$1" = "-u" ]; then
           echo "----------- uploading web files -----------------"
           rsync ${options} ${directory} ${server}:${dirup}
           echo "----------- upload complete ---------------"
        else
        usage;
        fi
```

---

### Post by Aearenda on 2008-05-11
If the target computer is similar to the source computer, you can simply copy the partitions across, using partimage, or even dd. The fastest way would be to temprarily add the target drives to the source computer and boot from a live CD.

---

### Post by ironwolfe on 2008-05-11
> **nephish said:**
> Hey there all, 

I have a server at work. It is a website server. 
We have another computer that i want to make a backup in case our server catches on fire or something. It kinda took a bit to get the main stuff up and configured, so to avoid having to do all of that again... Is it possible to make an exact copy of our system onto another computers hardrive ? Thanks for any tips

The key is to keep permissions and the like.  I use rsync as well, but not with a script unless you want to automate it.

I use the rsync with the -a option which "archives" the filesystem.  you will need to mount the drives, so good to do it with a live cd.

You could use copy with -Rdvxp options enabled - use "man cp" to figure it out.  It is similar to rsync -a.

Another way would be to make an image of the entire partion(s).  I have heard clonezilla is good:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

I use the commercial software acronis true image for my drive images to a network drive.

good luck.

---

### Post by tgalati4 on 2008-05-11
If you can add a second drive to the primary machine:

>sudo cp /dev/sda /dev/sdb

You don't even need to format the second drive, but make sure it is the same size or larger.

Boot from the second drive to make sure you have a valid image, then place the drive in  your backup server then boot it as well to test integrity.

---

### Post by nephish on 2008-05-11
thanks for all the help gents, i like the idea of copying the drives, but it will have to be done across a network inside our LAN. The computers both have the same usernames and such, i think dd would be great. The only deal is that both computers are RAID 5 with 5 hard drives. But, to the OS, they look like one drive. They are both Dell servers, but the hardware is not identical. Please let me know if this changes things.
and again. thanks all for the input

---

### Post by Aearenda on 2008-05-11
Ubuntu is much more forgiving of differences between hardware than Windows. However, I don't know how RAID affects this - if in hardware, and I guess it is from your description, it should be ok. I have previously copied drives with Linux software RAID partitions in them successfully.

If not doing exact partition copies, beware copying /boot/grub/menu.lst and /etc/fstab, which have partition UUIDs in them. Non-exact copies may have different UUIDs. You may have to reinstall GRUB after copying.

I think I would go for a complete image copy to start with, but and then use rsync to keep them in step.

---

### Post by Aearenda on 2008-05-11
DO NOT DO WHAT THE (now removed) LAST POST SAYS! It is malicious. 

mkfs.ext3 is for making a new ext3 filesystem in a partition. It erases whatever was there before.

---

### Post by nephish on 2008-05-11
Thanks for the alert and watching my back. I did not see the post, but it would have set off some flags. I have been using linux for about 6 years, and Ubuntu for the past two. I know what the mkfs does. Geez, why would someone do that?  
anyway... Yes the Raid is in the hardware. It configures itself on boot and spins up the drives and whatnot before grub even starts. So , i take it this is good news. I would prefer a direct copy of the drive over the network, then use rsync to keep it up to date. Actually, after the copy, only the  /var/www will be needed to be backed up. I have a script that i put together to have the database update the backup database. So, as long as i use the right solution for the disk copy, i should be good to go.

Again, thanks.

---

### Post by Aearenda on 2008-05-11
No worries! It turns out there's a thread about the malicious poster here: [http://ubuntuforums.org/showthread.php?t=789998](http://ubuntuforums.org/showthread.php?t=789998).

---

### Post by windependence on 2008-05-11
dd would be my choice to do the image and then rsync to keep it current. Here is an absolutely fantastic resource for dd, even cloning disks with different sizes.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

-Tim

---

### Post by ironwolfe on 2008-05-13
> **nephish said:**
> Thanks for the alert and watching my back. I did not see the post, but it would have set off some flags. I have been using linux for about 6 years, and Ubuntu for the past two. I know what the mkfs does. Geez, why would someone do that?  
anyway... Yes the Raid is in the hardware. It configures itself on boot and spins up the drives and whatnot before grub even starts. So , i take it this is good news. I would prefer a direct copy of the drive over the network, then use rsync to keep it up to date. Actually, after the copy, only the  /var/www will be needed to be backed up. I have a script that i put together to have the database update the backup database. So, as long as i use the right solution for the disk copy, i should be good to go.

Again, thanks.

Since linux mounts hardware as a folder in the filesystem - there is little worry about how it will handle it.  Like another poster mentioned, you may want to set up the fstab and grub for UUID.  You will have to get the UUID for the new filesystem (the one you copied to).  Use the following commands after you make your new filesystem:

```
sudo fdisk -l 
```
this will list all the /dev partitions
```
sudo vol_id -u /dev/'partition of interest'
```
this will give you your new UUID's
copy this into your fstab and grub files
```
gksudo gedit /etc/fstab
```
change the UUID to the new one - if it is using the old /dev/sda1 for example, comment that line out with a # hash.  copy the line (without the #) and change the /dev/sda1 to UUID='your new UUID'
```
gksudo gedit /boot/grub/menu.lst
```
add the new UUID to the root=UUID='new UUID'

I hope this helps.

---

### Post by nephish on 2008-05-13
yes indeed this does help, granted, i need to do  a bit of research to know what UUID means, but that's ok, i just needed a place to start.
thanks again

---

### Post by licensedorchid on 2008-05-13
Assuming the hardware is the same, I would go with dd, piped to netcat.
On the old server
```
 dd if=/dev/sda bs=512 | nc SERVERIP 9999
```
on the new server
```
 nc -v -p 9999 -l | dd of=/dev/sda
```
First, do the new machine part, and then the old. You will need to boot the new box with some kind of livecd, like knoppix. (I don't know if the ubuntu cds have netcat and dd on them)

---

### Post by windependence on 2008-05-13
> **licensedorchid said:**
> Assuming the hardware is the same, I would go with dd, piped to netcat.
On the old server
```
 dd if=/dev/sda bs=512 | nc SERVERIP 9999
```
on the new server
```
 nc -v -p 9999 -l | dd of=/dev/sda
```
First, do the new machine part, and then the old. You will need to boot the new box with some kind of livecd, like knoppix. (I don't know if the ubuntu cds have netcat and dd on them)

He'll get faster performance if he sets the block size to 4096 instead of 512

```
 dd if=/dev/sda bs=4096 | nc SERVERIP 9999
```

-Tim

---

### Post by licensedorchid on 2008-05-13
Good point. And, possibly, even better performance if he pipes it through a compression utility.
For the record, bs is the block size that netcat cuts the image into before it is sent. If the block size is the max size of the payload in a tcp packet, then there is less wasted space, more efficiency, ergo faster sppeds!

---

