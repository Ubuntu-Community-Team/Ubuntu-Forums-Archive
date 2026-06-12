---
title: "Ubuntu server tips - summary"
date: 2010-02-28
forum: Server Platforms
---

### Post by junke1990 on 2010-02-28
Summary - Home server tips by Junke1990

1. Partitions
Im going to split up the partitions over mulitple drives

internal first drive:
```
dev	MP	FS	Size
sda1	/boot	ext2 	500mb 
sda2	/	ext4	10gb
sda3	SWAP	SWAP	dubble the amount of RAM
```

Second drive (in my case external HDD)
```
sdb1	/home 	ext4	1TB, full external drive
```


2. Server packages
SSH server with blacklists
Screen for wrapping session
DenyHosts for blocking attacks
Lighttpd for webhosting, PHP and MySQL modules, kinda LLMP in stead of LAMP
Irssi for command-line IRC
Samba for filesharing with Windows Computers
AutoFS so the external drives can be shut off when not used, when needed the drives will be turned on.


```

sudo apt-get -y install openssh-server openssh-blacklist openssh-blacklist-extra
sudo apt-get -y install screen
sudo apt-get -y install denyhosts
sudo apt-get -y install lighttpd php5 mysql-server
sudo apt-get -y install irssi
sudo apt-get -y install samba
sudo apt-get -y install autofs

```


3. Configuration
AutoFS
This will save your harddrives from running all the time while no one is using them.
open /etc/fstab and comment out the line of the home partition by adding a # in front of it
```
$ sudo nano /etc/fstab
```
**#/dev/sdb1       /home           ext4    defaults        0       2**

now create the file auto.home in /etc and add it to auto.master
```
$ sudo nano /etc/auto.home
```
**home    -fstype=ext4,rw,defaults        :/dev/sdb1**

```
$ sudo nano /etc/auto.master
```
**/ /etc/auto.home --timeout=300 --ghost**


SSH server
Making sure only users of the group ssh can connect, easier to manage
```
$ sudo nano /etc/ssh/sshd_config
```
add: **AllowGroups ssh**

to add users to the group ssh
```
$ sudo useradd [username] ssh
```

Samba
Make a directory on your external disk where everybody can share their files and set the permissions
```
$ sudo mkdir /home/shared
$ sudo chmod -R ugo+rwx /home/shared
```

Edit the config /etc/samba/smb.conf
Change the line
```
; security = user
```
to
```
 security = user
```
add the following to the bottom of the file

```

[shared]
  comment = media, video, music and such 
  path = /home/shared
  create mask = 0660
  directory mask = 0771
  write list = @users
  browsable = yes
  writable = yes

[homes]
   comment = Home Directories
   valid users = %S
   writable = yes
   create mask = 0700
   directory mask = 0700
   browsable = no

```

add users to the samba db
```
$ smbpasswd [USERNAME]
```

Denyhosts
Let denyhosts get a list of known attackers.
Open /etc/denyhosts.conf
search for the line SYNC_SERVER and uncomment it (remove the #)
 
Lighttpd - Home Dirs
It is possible to publish files from your homedir.
```
$ mkdir ~/public_html
$ ln -s /etc/lighttpd/conf-available/10-userdir.conf /etc/lighttpd/conf-enabled/10-userdir.conf
```

Lighttpd - Torrentflux
creating a symbolic link from the www directory to the torrentflux files
```
$ sudo ln -s /usr/share/torrentflux/www /var/www/torrentflux 
```

BashRC
Add the following line to your bashrc (nano ~/.bashrc) to make sure you always work in a screen
```
echo $TERMCAP | grep screen > /dev/null || screen -xrRR || screen -D -RR

```

All done! 

Correct me if I'm wrong, otherwise reboot and enjoy!!!
Let me know if something is missing that you think there should be in every server!

---

### Post by n0dix on 2010-02-28
Thanks for take your time and doing this. ;)
Keep sharing!!!

---

### Post by junke1990 on 2010-02-28
Not that much special, but hey, it's a start! I will post more formal and comprehensive manuals later on.

---

