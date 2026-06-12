---
title: "Backing up Ubuntu Server but from a client that's connected to the server"
date: 2017-07-25
forum: Server Platforms
---

### Post by mizoooo94 on 2017-07-25
I'm trying to back up my Ubuntu Server that has all my files, it's around 9 Tb. I know there are many threads out there saying how to backup Ubuntu Server. But the issue here is i'm not connected to the server directly i'm connected to another Ubuntu client using putty (on a windows machine) and that client is connected to the server. There is no GUI only a terminal (obviously). I'm trying to backup the file in any of the 2 formats: .img and .tar.gz or whatever is suitable i just need to make sure i have a backup before anything happens to the files on the server.

here is a df command of all the drives on the client i'm currently on

```
xxxx@yyyy:~$ df -h
Filesystem             Size  Used Avail Use% Mounted on
udev                    16G  8.0K   16G   1% /dev
tmpfs                  3.2G  572K  3.2G   1% /run
/dev/dm-0           1.8T  304G  1.4T  18% /
none                   4.0K     0  4.0K   0% /sys/fs/cgroup
none                   5.0M  4.0K  5.0M   1% /run/lock
none                    16G     0   16G   0% /run/shm
none                  100M     0  100M   0% /run/user
/dev/sda2           237M  183M   42M  82% /boot
/dev/sda1           512M  3.4M  509M   1% /boot/efi
//10.0.X.8/aaa     5.5T  4.7T  786G  86% /mnt/okai
//10.0.X.174/bbb  8.2T  7.6T  572G  94% /mnt/the
/dev/sdb1            2.8T   61G  2.7T   3% /mnt/sdb
```

and I wanna backup the server //10.0.X.174/bbb

i tried using the TAR command but failed miserably (ended backing up the / from the client's drive and nothing from the server) and failed as well with the dd command (system didn't allow me to perform any backups and kept giving me error's)

I'm trying to back the server up to /dev/sdb1 (I mounted it to be able to access it but I can unmount it if needed)
i know that sdb1 is less in size but i'm gonna get another drive when im ready to backup !!

Everything out there is either about backing up normal Ubuntu machine with GUI or backing up terminal but from the server itself not from a client that's connected to the server. :(

I appreciate taking sometime to help.

Please I need help ASAP.

---

### Post by SeijiSensei on 2017-07-25
You can use rsync over the network.  For instance, on the client you could run
```

cd /path/to/some/backup/directory
sudo rsync -av 10.0.X.174/ .

```
would copy all the files on 10.0.X.174 to the backup directory.  The server needs to support SSH connections, but it sounds like it's set up that way already.

There are permission issues involved, of course.  Since the root account is disabled on Ubuntu, you should probably use [shared keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").  The code I gave above assumes that root will be running the process on both ends.  To do that in Ubuntu, you would need to create a key pair as root on the client (storing the results in /root/.ssh), then add the public key to the file /root/.ssh/authorized_keys on the server.  Once this is set up properly, you will not be prompted for passwords.

Before going too far down this road, I'd read some of the guides on using rsync for backup like this one: [https://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/](https://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/)

The manual page for rsync is very extensive but perhaps a bit dense.  You can read it by typing "man rsync" at a terminal prompt.

There are some things you don't want to include in a backup like /proc which is a filesystem created anew at each boot.  I use the "--exclude-files=/path/to/list" option in rsync to specify "globs" for files I don't want to back up.  Here the contents of my list:

```

*backup*
*.iso
*.avi
*.mkv
*.mp*
*spam/*
*cache*
*thumbnails*
proc/
sys/
run/
dev/
local/share
.VirtualBox
VirtualBox

```

That excludes things like video and audio files which I have multiple copies of, the temporary file systems like /proc and /sys, and VirtualBox virtual machines which are huge.

---

### Post by mizoooo94 on 2017-07-25
I tried it but i get this error:
and I have no idea which directory 10.0.X.174 is in, like i dunu what to put before 10.0.X.174

I'm a no0b here X_X srry

" $ rsync -av 10.0.X.174/
sending incremental file list
rsync: change_dir "/home/stowadmin//10.0.X.174" failed: No such file or directory (2)"

---

### Post by mizoooo94 on 2017-07-25
sorry i kinda replied under the post, I was trying to post it here

---

### Post by mizoooo94 on 2017-07-25
> **SeijiSensei said:**
> There are permission issues involved, of course.  Since the root account is disabled on Ubuntu, you should probably use [shared keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").  The code I gave above assumes that root will be running the process on both ends.  To do that in Ubuntu, you would need to create a key pair as root on the client (storing the results in /root/.ssh), then add the public key to the file /root/.ssh/authorized_keys on the server.  Once this is set up properly, you will not be prompted for passwords.


Dw i have sudo privileges and i can use sudo but it gave me an error cause it doesn't know where 10.0.X.174 is !
and neither Do i, like whats the full address /X/X/X/10.0.X.174 ?

---

### Post by SeijiSensei on 2017-07-25
```
rsync: change_dir "/home/stowadmin//10.0.X.174" failed: No such file or directory (2)" 
```
Sounds to me like there is no /home/stowadmin directory on the client.

Don't write the backup to a home directory.  Put it someplace owned by root like /var/backup.

Sudo privileges aren't enough to enable transfers to work.  You have to be able to connect as the root user on the source machine.  Ubuntu doesn't allow the root user to have a password by default, so you have to use the shared-keys method I described above.

This is a somewhat complicated project, so don't expect things to work correctly the first time out.

---

### Post by mizoooo94 on 2017-07-26
How about if i get access directly to the server will things be easier ? 
like i would use the normal rsync command or dd or TAR ? or will there still be more complications ?

---

### Post by mastablasta on 2017-07-26
> **mizoooo94 said:**
> How about if i get access directly to the server will things be easier ? 
like i would use the normal rsync command or dd or TAR ? or will there still be more complications ?

that would be my suggestion and the easy option. 

direct server access then use rsync. or if you have direct access and oyu dont' need an automated backup to be setup, you can just use filezilla or winscp to move the data files via a nice GUI. just use the SSH key and the sFTP method to connect to server.

---

### Post by mizoooo94 on 2017-08-06
I ended up installing a Ubuntu Desktop GUI on the server and tried using Gparted but didn't work so I ended up using Clonezilla and it all worked out fine :D

Thanks again Guys Appreciate it :D

---

