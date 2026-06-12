---
title: "Ubuntu 12.04 LTS Samba + Pure-FTPD Setup question"
date: 2014-02-12
forum: Server Platforms
---

### Post by ITGuyChris on 2014-02-12
Hello!

I'm looking for some assistance in setting up pure-ftpd to be able to upload documents\pictures via FTP to a Samba share I have setup so I can access them on a Windows 7 desktop. Although I could use ftp:*serverip* via a web browser and upload\download items from there, I have a specific reason why it needs to be a network share I can access via My Computer inside of the Windows desktop. Unfortunately, configuring Samba is one of the more "extreme" things I have done recently and have no idea how to setup an FTP server using Linux. 

Here's a basic rundown of what I'm trying to accomplish:

user1 needs to upload a photo via ftp to the samba share located at /media/data/photos located on /dev/sdb1, then from inside of their Windows desktop application, upload the photo into said application.


I have tested the ability to read\write\delete items from this samba share, so that isn't the problem. I'm just unfamiliar with FTP servers.

---

### Post by ITGuyChris on 2014-02-14
Well, I have been able to figure this out with some quite extensive searching.


_**[SIZE=4]New Hard Disk Setup[/SIZE]**_

 I'll first start off with creating a second hard drive to use as the "shared" drive:

```
 
fdisk /dev/sdb
- option n
- option p
- option 1
- select defaults for the next 2 prompts
- option w

```

Next we will format the new partition with a file system. In this case, I used the ext4 file system on the new drive labeled sdb1 located in /dev
```

mkfs.ext4 /dev/sdb1

```

Create a mount point for the sdb1 partition
```

mkdir /media/data
```

Now we will edit fstab to auto mount /dev/sdb1 upon boot. I used the nano text editor for this part. You can use which ever text editor you are comfortable with. 
```

nano /etc/fstab

```

Add the following line to the bottom of the fstab config file
```

/dev/sdb1    /media/data    ext4    defaults    0    0

```

Save the fstab config and reboot the server
```

reboot

```

[U][B][SIZE=4]
Samba Setup[/SIZE][/B][/U]

Start off by creating a directory to share using Samba.
```

mkdir -p /media/data/share

```

Now to install Samba!
```

apt-get install samba

```

Make a backup for the Samba configuration file just in case something happens.
```

cp /etc/samba/smb.conf /etc/samba/smb.conf.orig

```

Remove the default smb.conf file
```

rm /etc/samba/smb.conf

```

Create a new blank smb.conf file
```

touch /etc/samba/smb.conf

```

Edit the blank smb.conf file
```

nano /etc/samba/smb.conf

```

I have used the following config for the test environment and unfortunately I do not know all of the options that can be used inside of the smb.conf file
```

[COLOR=#000000][FONT=Arial][global][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    workgroup = workgroup[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    server string = Ubuntu File Server[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    netbios name = $servername[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    security = user[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    map to guest = bad user[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    dns proxy = no[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][Photos][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    path = /media/data/share[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    valid users = @$groupname[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    browsable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    writable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    guest ok = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    read only = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    create mask = 0644[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    directory mask = 0755[/FONT][/COLOR]


```

Once you have saved the new smb.conf file, reboot the services smbd & nmbd
```

restart smbd

restart nmbd

```

Create a new group for the Samba share
```

addgroup $groupname

```

Change group access to the share
```

chgrp -R $groupname /media/data/share

```

Change permissions to the root of the share
```

chmod 777 /media/data/share

```

Add a user account of the share group
```

adduser $username $groupname

```

Finally, create a share password for the user account
```

smbpasswd -a $username

```

You now will be able to access the network share from Windows. 


_**Pure-FTPD Setup**_

Install pure-ftpd
```

apt-get install pure-ftpd

```

Add a virtual user to the ftp server and point it to the directory you want the virtual user to have access to when uploading files to the Samba share
```

pure-pw useradd $username -u $username -g $groupname -d /path/to/samba/share

```

Make the pure-ftpd database
```

pure-pw mkdb

```

Run this command (still trying to figure out what that does)
```

ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/50pure

```

Restart the pure-ftpd service
```

service pure-ftpd restart

```


Now you have an FTP server that can drop files to a Samba share that can be accessed by those who use Windows desktops.

---

