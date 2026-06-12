---
title: "ntfs and samaba"
date: 2011-06-30
forum: Server Platforms
---

### Post by thetopcat2010 on 2011-06-30
[SIZE=3][FONT=Calibri]I am very new to Linux and it has taken me a while to get to grips with understanding how things work.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I have Unbuntu 2.32.1 Build date 14/4/11[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have Samba Installed[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I also have 8 Sata drives all with NTFS most of them have a lot of data on them.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]All my drives were used on an old windows 7 system, and now I wish to have them in a server setup.[/FONT][/SIZE]
 
My clients are all windows users apart from 1 witch is an Unbuntu desktop user.
 
The problem I have is access rights or permissions none of the clients can gain access to my NTFS shares.
 
I am using a GUI on my server (Gnome) as I am not very clued up with command lines in Unbuntu just yet.
 
Please could someone offer me some help in sorting out my network sharing.
 
Many Thanks IAN

---

### Post by Morbius1 on 2011-06-30
Some questions:

* Do you have these NTFS partitions mounted at boot?

If you do can we see how they are mounted:
```
cat /etc/fstab
```
* Have you already tried to share them?
```
net usershare info --long
```
```
testparm -s
```

---

### Post by sahabcse on 2011-06-30
Paste the o/p of etc/exports file

---

### Post by Morbius1 on 2011-06-30
> **sahabcse said:**
> Paste the o/p of etc/exports file
It's quite possible that I'm misreading the original post but I think this is a Samba question not an NFS question.

---

### Post by thetopcat2010 on 2011-06-30
I am very very new at all this..
 
Paste the o/p of etc/exports file  can u explaine where these files are and ill happy pste them.
 
As for mounting them on boot, Im lost how do I do that 
 
Thanks for all your help

---

### Post by Morbius1 on 2011-06-30
Open up a terminal and type:
```
cat /etc/fstab
```Then just select Edit > Select All
Then Edit > Copy
Then Paste to your next post

Follow the same procedure for the next commands:
```
net usershare info --long
``````
testparm -s
```

---

### Post by thetopcat2010 on 2011-06-30
> **Morbius1 said:**
> It's quite possible that I'm misreading the original post but I think this is a Samba question not an NFS question.
 
 
Possible but I can share folders on the desktop ok but cant share ntfs volumes so thats why I belived it is an ntfs and samba problem

---

### Post by Morbius1 on 2011-06-30
> **thetopcat2010 said:**
> Possible but I can share folders on the desktop ok but cant share ntfs volumes so thats why I belived it is an ntfs and samba problem
NFS is not NTFS - 2 different things.

---

### Post by thetopcat2010 on 2011-06-30
> **Morbius1 said:**
> Open up a terminal and type:
```
cat /etc/fstab
```Then just select Edit > Select All
Then Edit > Copy
Then Paste to your next post

Follow the same procedure for the next commands:
```
net usershare info --long
``````
testparm -s
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/Server-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a040ceea-d7c0-4e25-a198-23dec1755caf /boot           ext2    defaults        0       2
/dev/mapper/Server-swap_1 none            swap    sw              0       0

root@Server:/etc/samba# 
root@Server:/etc/samba# net usershare info --long
root@Server:/etc/samba# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    panic action = /usr/share/samba/panic-action %d

[public]
    comment = public_files
    path = /media/Movies
    read only = No
    create mask = 0765
    guest ok = Yes

---

### Post by Morbius1 on 2011-06-30
That is not the standard smb.conf. We're going to have to fix that. Please tell me you're not running your server as root. One more piece of information please:

```
ls -al /media/Movies
```

---

### Post by thetopcat2010 on 2011-06-30
> **Morbius1 said:**
> That is not the standard smb.conf. We're going to have to fix that. Please tell me you're not running your server as root. One more piece of information please:

```
ls -al /media/Movies
```


root@Server:/etc/samba# ls -al /media/movies
ls: cannot access /media/movies: No such file or directory

I was connected to root to enable me to edit the smb.conf file

I do have the default file as well I was trying to find solutions on the web so that is why its not default

if you wish I can put back the original file first

---

### Post by Morbius1 on 2011-06-30
Caps matter in Linux. 
 Do this instead:
```
ls -al /media
```

---

### Post by mastablasta on 2011-06-30
Also (and a bit unrelated) you can copy and paste the commands in terminal. Just saying so you don't make more typos.

---

### Post by thetopcat2010 on 2011-06-30
root@Server:/etc/samba# ls -al /media
total 16
drwxr-xr-x  4 root          root    4096 2011-06-29 12:16 .
drwxr-xr-x 21 root          root    4096 2011-06-28 21:42 ..
drwxr-xr-x  2 root          root    4096 2011-06-28 21:41 cdrom
drwxr-x---  5 administrator lpadmin 4096 2011-06-28 23:32 Movies


ok sorry about the typo

---

### Post by Morbius1 on 2011-06-30
This one's my fault. I assumed /media/Movies was an ntfs partition but clearly it cannot be. 

This is going to take a while and I'll be out for the rest of the morning so let me leave you with a few things:

[1] Make the following change to smb.conf:
Add the following line to the [global] section:
```
map to guest = Bad User
```Then restart samba:
```
sudo service smbd restart
```[2] Change permissions of the the shared folder to allow guest access:
```
sudo chmod 0777 /media/Movies
```If you want to share NTFS partitions it's best to have them automount so we need the output of these commands:
```
sudo blkid -c /dev/null
``````
mount
```When I get back I can provide a template for you to use that will enable you to edit fstab so that they mount with the permissions necessary to allow sharing across the network.

---

### Post by thetopcat2010 on 2011-06-30
> **Morbius1 said:**
> This one's my fault. I assumed /media/Movies was an ntfs partition but clearly it cannot be. 

This is going to take a while and I'll be out for the rest of the morning so let me leave you with a few things:

[1] Make the following change to smb.conf:
Add the following line to the [global] section:
```
map to guest = Bad User
```Then restart samba:
```
sudo service smbd restart
```[2] Change permissions of the the shared folder to allow guest access:
```
sudo chmod 0777 /media/Movies
```If you want to share NTFS partitions it's best to have them automount so we need the output of these commands:
```
sudo blkid -c /dev/null
``````
mount
```When I get back I can provide a template for you to use that will enable you to edit fstab so that they mount with the permissions necessary to allow sharing across the network.

Ok thanks I have edited the conf file and below is the output  of the rest of your last reply

root@Server:/etc/samba# sudo service smbd restart

smbd start/running, process 7935

root@Server:/etc/samba# sudo chmod 0777 /media/Movies

root@Server:/etc/samba# sudo blkid -c /dev/null

/dev/sda1: UUID="a040ceea-d7c0-4e25-a198-23dec1755caf" TYPE="ext2" 
/dev/sda5: UUID="bhyzC2-DMg6-eCyx-Luif-dCEE-wfYS-ZpojTH" TYPE="LVM2_member" 
/dev/sdb1: LABEL="Comedy & Sitcoms & Drama" UUID="5244DB1344DAF8A5" TYPE="ntfs" 
/dev/sdc1: LABEL="System Backups" UUID="EE7C7AD07C7A92D7" TYPE="ntfs" 
/dev/sdd1: LABEL="Family & Movies" UUID="9AE0037AE0035BBF" TYPE="ntfs" 
/dev/sde1: LABEL="Movies" UUID="02adf22c-1fb6-4b68-99f1-dafc96dc6aad" TYPE="ext4" 
/dev/sdf1: LABEL="Music" UUID="04F0C142F0C13AA6" TYPE="ntfs" 
/dev/sdg1: LABEL="Extras" UUID="BEA6ECF3A6ECAD59" TYPE="ntfs" 
/dev/sdh1: LABEL="Recorded TV" UUID="ECA40C12A40BDDC8" TYPE="ntfs" 
/dev/sdh2: LABEL="Users" UUID="965016AB501691DB" TYPE="ntfs" 
/dev/sdi1: LABEL="SCIFI" UUID="BE2C13132C12C675" TYPE="ntfs" 
/dev/mapper/Server-root: UUID="81bc52a2-c405-4730-bf1d-97c4854f4495" TYPE="ext4" 
/dev/mapper/Server-swap_1: UUID="a0e6e409-0a5d-480f-862e-bc1ffc7cacad" TYPE="swap" 

root@Server:/etc/samba# mount

/dev/mapper/Server-root on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sde1 on /media/Movies type ext4 (rw,nosuid,nodev,uhelper=udisks,commit=0,commit=0,commit=0,commit=0)

---

### Post by Morbius1 on 2011-06-30
I'll go through the steps to mount one ntfs partition. I will use this partition as an example:
> /dev/sdh1: LABEL="Recorded TV" UUID="ECA40C12A40BDDC8" TYPE="ntfs" **[1] Create a permanent mount point for the partition:**
```
sudo mkdir /mnt/RecTV
```[COLOR=Blue]*Make your life simpler and don't use spaces in anything Linux*[/COLOR]

**[2] Edit fstab as root:**
```
gksu gedit /etc/fstab
```**[3] Add the following line to the end of fstab:**
```
UUID=ECA40C12A40BDDC8 /mnt/RecTV ntfs defaults,nls=utf8,umask=000 0 0
```**[4] Save fstab, exit gedit, and back in the terminal run the following command which will test for errors and mount the new ntfs partition:**
```
sudo mount -a
```If all that works just use the same procedure to mount all the other ntfs partitions making sure that each mount point is different but still in /mnt and that their UUID numbers are specific to that partition.

Now I really have to go :wink:

---

### Post by thetopcat2010 on 2011-06-30
WOW thanks that worked, now im going to look at the rest of my hard disks hope all goes ok, thanks for all your help will send u a message to keep you informed how it goes.
 
hmm cant seem to get the others to work. The line UUID=ECA40C12A40BDDC8 /mnt/RecTV ntfs defaults,nls=utf8,umask=000 0 0 
I understand ECA40C12A40BDDC8 /mnt/RecTV changes with every drive but as for the remander of the line does that stay static or change ?
Many Thanks
 
Ian (UK)

---

### Post by Morbius1 on 2011-06-30
The options list stays the same. SO for example this one:
> /dev/sdb1: LABEL="Comedy & Sitcoms & Drama" UUID="5244DB1344DAF8A5" TYPE="ntfs" It would be something like this:
```
sudo mkdir /mnt/ComSitDram
``````
UUID=5244DB1344DAF8A5 /mnt/ComSitDram ntfs defaults,nls=utf8,umask=000 0 0 
``````
sudo mount -a
```

---

### Post by thetopcat2010 on 2011-06-30
> **Morbius1 said:**
> The options list stays the same. SO for example this one:
It would be something like this:
```
sudo mkdir /mnt/ComSitDram
``````
UUID=5244DB1344DAF8A5 /mnt/ComSitDram ntfs defaults,nls=utf8,umask=000 0 0 
``````
sudo mount -a
```
 
 
I am having a problem I have lost the above drive from "Computer" cant see the drive at all
here is my fstab file I followed what u said above, could u please point to where I have messed up
 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/mapper/Server-root / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation
UUID=a040ceea-d7c0-4e25-a198-23dec1755caf /boot ext2 defaults 0 2
/dev/mapper/Server-swap_1 none swap sw 0 0
UUID=ECA40C12A40BDDC8 /mnt/RecTV ntfs defaults,nls=utf8,umask=000 0 0
UUID=BEA6ECF3A6ECAD59 /mnt/Extras ntfs defaults,nls=utf8,umask=000 0 0
UUID=5244DB1344DAF8A5 /mnt/ComSitDram ntfs defaults,nls=utf8,umask=000 0 0
 
Just to confuse matters the only drive that shares ok is Movies  
 
Many Thanks 
IAN

---

### Post by Morbius1 on 2011-06-30
There's nothing wrong with those last 3 lines. If you ran "sudo mount -a" and no errors were reported then you are good to go. 

In "Computer" go to File System > mnt > ComSitDram and verify that it has the data that it should have.

---

### Post by arrrghhh on 2011-06-30
> **thetopcat2010 said:**
> I am having a problem I have lost the above drive from "Computer" cant see the drive at all
here is my fstab file I followed what u said above, could u please point to where I have messed up

Just to confuse matters the only drive that shares ok is Movies

> **Morbius1 said:**
> There's nothing wrong with those last 3 lines. If you ran "sudo mount -a" and no errors were reported then you are good to go. 

In "Computer" go to File System > mnt > ComSitDram and verify that it has the data that it should have.

Morbius1 is prioritizing things for you thetopcat2010.

Basically you need to get all the drives mounted in Linux before Linux can share them out!  So assuming you have all the drives mounted (verify as he has stated above) then the next step is to add them all into samba (smb.conf).

Based on your testparm output, the only mountpoint you have in samba is the Movies drive.

So you need to add all of these new mountpoints into samba so they're viewable.  Let us know if you have issues pursuing that.

---

### Post by thetopcat2010 on 2011-06-30
ahh great yes it is there, I do appologise.  I have got them shareing by using the draw in the <file system> <ComSitDram> and sharing that.
So I would like to say a BIG thanks for all your help, just one quick question is that the best way to share them by using there draw in the MNT folder ?
 
Thanks
IAN

---

### Post by Morbius1 on 2011-06-30
> just one quick question is that the best way to share them by using there draw in the MNT folder
I do not know what that means - "the draw".

DO you mean Right click on a folder and then Sharing Options?

---

### Post by thetopcat2010 on 2011-06-30
> **Morbius1 said:**
> I do not know what that means - "the draw".
 
DO you mean Right click on a folder and then Sharing Options?
 
Sorry its an old term I mean Folder

---

### Post by arrrghhh on 2011-06-30
> **thetopcat2010 said:**
> Sorry its an old term I mean Folder

Since you already have gnome, and you're used to a GUI, that probably is the easiest way to share the folders.

I had issues with smb.conf myself, and ended up using webmin to configure it.  To each their own.

---

### Post by Morbius1 on 2011-06-30
Still don't know what you mean.

If your question is about my choice of the mount point location /mnt, then you can share any folder anywhere. I used /mnt to begin with because your original post talked about 8 ntfs drives. I figured there may be multiple partitions on each drive so I put the mount point in /mnt or else your desktop would be covered with mount icons.

If you mount something in /media or in your /home/$USER folder then a mount icon will appear on the desktop. If you put it anywhere else it will not. Something like /mnt seemed like a logical choice.

---

### Post by arrrghhh on 2011-06-30
> **Morbius1 said:**
> Still don't know what you mean.

If your question is about my choice of the mount point location /mnt, then you can share any folder anywhere. I used /mnt to begin with because your original post talked about 8 ntfs drives. I figured there may be multiple partitions on each drive so I put the mount point in /mnt or else your desktop would be covered with mount icons.

**If you mount something in /media or in your /home/$USER folder then a mount icon will appear on the desktop.** If you put it anywhere else it will not. Something like /mnt seemed like a logical choice.

I did not know that.  I kinda assumed anything mounted would appear on the desktop, learn something new every day.

No thanks button here, but thanks :p.

---

### Post by thetopcat2010 on 2011-06-30
Ok Thanks Guys.
 
Have a great Day Im off to get my server working like I hoped it would.
 
Take care.
 
 
Ian (UK)

---

