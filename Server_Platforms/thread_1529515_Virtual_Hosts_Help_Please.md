---
title: "Virtual Hosts Help Please"
date: 2010-07-12
forum: Server Platforms
---

### Post by thescubadude on 2010-07-12
Ok, so I am not technically running the server version but am running the desktop version of ubuntu but still using it as my internal webserver.

Currently I am running Jaunty on my existing server and everything is working fine.

Previously I attempted to install Karmic on the server but ran into issues so downgraded to Jaunty and have been running the server with Jaunty ever since.

Today I have a new server so I would like to install 10.04 onto the machine. I now have the time to fiddle a little as the old server is still running everything. I installed 10.04 and installed Apache etc. I am stuck at the Virtual Hosts. I have attempted various options off the net with no luck.

The error I get is the following:

**Forbidden**

 You don't have permission to access / on this server.
  Apache/2.2.12 (Ubuntu) Server at mywebsite.com Port 80

I have attempted all the permissions etc and nothing helps.

I have done the following to setup my virtual hosts (this works on Jacky 9.04) but not on 9.10 or 10.04.

To set up the virtual hosts (do this for each virtual host):

cd /etc/apache2/sites-available
sudo gedit testsite1.ex.conf

Add this to the conf file & save:

<VirtualHost *:80>

ServerName testsite1.ex
DocumentRoot /media/urchin/www/mysitefoldername
<Directory />
Options FollowSymLinks
AllowOverride All
</Directory>
<Directory /media/urchin/www/mysitefoldername>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from all
</Directory>
</VirtualHost>


sudo gedit /etc/hosts

127.0.0.1 localhost
127.0.0.1 webserver
127.0.0.1 testsite1.ex

Enable the new virtual host:

sudo a2ensite testsite1.ex.conf

Reload apache:

sudo /etc/init.d/apache2 reload

Any ideas?

---

### Post by cdenley on 2010-07-12
```

ls -l /media/urchin/www/mysitefoldername
ls -ld /media/urchin/www/mysitefoldername
ls -ld /media/urchin/www
ls -ld /media/urchin
ls -ld /media
ls -ld /

```

---

### Post by thescubadude on 2010-07-12
I am very much a linux/ubuntu beginner...

can you explain where and what I should do with that code?

I am using desktop version of 10.04

---

### Post by cdenley on 2010-07-12
Those are commands. You run them in the terminal. Post the output here. That will verify apache has permission to access whatever file you are attempting to access.

Applications>Accessories>Terminal

Obviously, replace "mysitefoldername" with the actual name of the directory if that isn't.

---

### Post by thescubadude on 2010-07-12
the first command lists all files in the directory.

Then the next two give as below
andrew@andrew-sony:~$ ls -ld /media/urchin/www/urchin-new
drwx------ 1 andrew andrew 8192 2010-07-12 09:54 /media/urchin/www/urchin-new
andrew@andrew-sony:~$ ls -ld /media/urchin/www
drwx------ 1 andrew andrew 8192 2010-06-30 11:11 /media/urchin/www

---

### Post by cdenley on 2010-07-12
> **thescubadude said:**
> the first command lists all files in the directory.

Then the next two give as below
andrew@andrew-sony:~$ ls -ld /media/urchin/www/urchin-new
drwx------ 1 andrew andrew 8192 2010-07-12 09:54 /media/urchin/www/urchin-new
andrew@andrew-sony:~$ ls -ld /media/urchin/www
drwx------ 1 andrew andrew 8192 2010-06-30 11:11 /media/urchin/www

Well, the permissions for the two directories which you did post are incorrect. Apache will not be able to serve any content within those directories. I would assume /media/urchin is a mount point? What filesystem is used for /media/urchin?
```

grep '^[^ ]* /media/urchin' /proc/mounts

```

---

### Post by zabuch on 2010-07-12
> Then the next two give as below
andrew@andrew-sony:~$ ls -ld /media/urchin/www/urchin-new
drwx------ 1 andrew andrew 8192 2010-07-12 09:54  /media/urchin/www/urchin-new
andrew@andrew-sony:~$ ls -ld /media/urchin/www
drwx------ 1 andrew andrew 8192 2010-06-30 11:11 /media/urchin/www
Permissions is your problem - apache does not have the access to the /media/urchin/www directory.
Try if this fixes it:
```
  chmod o+rX -R /media/urchin/www
```This will allow *all* the users on your system to read contents of /media/urchin/www .

---

### Post by cdenley on 2010-07-12
> **zabuch said:**
> Permissions is your problem - apache does not have the access to the /media/urchin/www directory.
Try if this fixes it:
```
  chmod o+rX -R /media/urchin/www
```This will allow *all* the users on your system to read contents of /media/urchin/www .

Unless this directory resides on an NTFS or FAT filesystem. You may also have to change permissions for /media/urchin.

---

### Post by thescubadude on 2010-07-12
it is an external drive with a fat file system. I will try some more tomorrow. 8.30pm and time to take a break

---

### Post by cdenley on 2010-07-12
> **thescubadude said:**
> it is an external drive with a fat file system. I will try some more tomorrow. 8.30pm and time to take a break

I wouldn't recommend hosting a website from a FAT filesystem. It does not support Linux filesystem permissions. If you insist, though, you will have to change the way the filesystem is mounted by adding an entry for it in /etc/fstab.

---

### Post by thescubadude on 2010-07-25
Ok so I'm back on it. The drive is actually NTFS. I thought it had been  converted to fat from ntfs to be used with a mac but that is another  drive.

Still strugglying with the permission errors...

To update my virtual host settings are working if I use them on the  local drive of the linux machine. I am just trying to avoid this as the  harddrive is quite old while the external drive is virtually brand new. The machine is all used only as an internal test machine/webserver for developing php based web applications. It does not serve any content outside of the office.

i have tried all sorts of different chmod to change permissions with no luck.

i have also tried:

grep '^[^ ]* /media/urchin' /proc/mounts 
Any other ideas? It seems bizarre because it works 100% in Ubuntu 9.04  but I have never managed to get it working in 9.10 or now 10.04.

How do I specifically set the permissions for the web user?

---

### Post by cdenley on 2010-07-25
NTFS doesn't have linux permissions, so they are set at mount time.
```

man mount.ntfs

```

---

### Post by thescubadude on 2010-07-25
thanks. I will try this next. Now trying to set up server edition but when I get to virtual hosts again I will try this. 

Now having a blank screen once I choose install now???

---

