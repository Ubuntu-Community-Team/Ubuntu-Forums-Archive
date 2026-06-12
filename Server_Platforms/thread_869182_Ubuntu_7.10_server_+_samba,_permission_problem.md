---
title: "Ubuntu 7.10 server + samba, permission problem"
date: 2008-07-24
forum: Server Platforms
---

### Post by zeezam on 2008-07-24
Hello!
Tried to installed my first server with [u[Ubuntu 7.10 and 'samba file sharing'[/u]. I wanted a NAS server with full permission share so any user can access it.

I followed this tutorial; [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

My problem start appear directly when I try connecting to my server with user and password box. After I created a user called 'home' I succed to login and see the share but I can't acces the share. I thought I didn't have to login with this setup?

**Look below on my setup**

*Here is my setup*

/etc/hosts
[HTML]

127.0.0.1       localhost
192.168.0.5 nas

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/HTML]

some fdisk info: fdisk -l
[HTML]
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56feed17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1314    10554673+  83  Linux
/dev/sda2           18699       18959     2096482+  82  Linux swap / Solaris
/dev/sda3            1315       18698   139636980    7  HPFS/NTFS
[/HTML]

/etc/fstab
[HTML]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=01a300d6-5fb4-4317-bd21-2ee487696d75 /               ext3    defaults,erro$
# /dev/sda3
UUID=40A7110C2E8F18E1 /media/sda3     ntfs    defaults,umask=007,gid=46 0      $
# /dev/sda2
UUID=9ab70b63-4b4c-4657-aede-acf9d1c0f7b8 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda3       /media/store  ntfs defaults 0 0
[/HTML]

/etc/samba/smb.conf
[HTML]
[media]
comment = Public folder
path = /media/store
public = yes
writeable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
guest ok = yes
[/HTML]

[img]http://static.pici.se/pictures/WsfCfrEnf.gif[/img]

[img]http://static.pici.se/pictures/gERJwYqjD.gif[/img]

The last picture is the permission failed message. It's on Swedish so it's pretty useless here maybe :)

[img]http://static.pici.se/pictures/NyoaDUcTX.gif[/img]

Any tips for me to get it work? Really appreciate answers.

Cheers

zeezam

---

### Post by zeezam on 2008-07-28
Here is the log:

[2008/07/24 14:43:52, 0] smbd/service.c:make_connection(1191)
  amd64 (192.168.0.2) couldn't find service hda public hard dis
[2008/07/24 14:43:52, 0] smbd/service.c:make_connection(1191)
  amd64 (192.168.0.2) couldn't find service hda public hard dis
[2008/07/24 14:43:52, 0] smbd/service.c:make_connection(1191)
  amd64 (192.168.0.2) couldn't find service hda public hard dis
[2008/07/24 14:43:52, 0] smbd/service.c:make_connection(1191)
  amd64 (192.168.0.2) couldn't find service hda public hard dis
[2008/07/24 14:46:53, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/07/24 14:46:53, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/07/24 14:59:53, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/07/24 14:59:53, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/07/24 15:04:36, 0] smbd/service.c:make_connection(1191)
  amd64 (192.168.0.2) couldn't find service hda public hard dis
[2008/07/24 15:04:36, 0] smbd/service.c:make_connection(1191)

---

### Post by amenszer on 2008-07-29
What are the read/write permissions and ownership for the /media/store directory (I guess in this case it's only a mount point)?

---

### Post by redraiderbum on 2008-07-29
I just reinstalled my server OS last night and set everything the same way.  When I tried to access the share I got a similar error.  It was the problem amenszer is referring to; the folder permissions and the samba permissions can be different.  If the folder permissions are restricted then you may not be able to access the share even if the samba permissions are correct.  If you don't know your way around the command line, to fix it I would do this command:

sudo chmod 777 /media/store

Hope this helps.

---

### Post by zeezam on 2008-07-30
> **amenszer said:**
> What are the read/write permissions and ownership for the /media/store directory (I guess in this case it's only a mount point)?

Yes, it is a mount point but I did make a **chmod 777 /media/store**


root@nas:/home/administrator# ls -la /media/store
total 8
drwxrwx--- 1 root plugdev 4096 2008-07-26 03:27 .
drwxrwxrwx 5 root root    4096 2008-07-24 11:23 ..
drwxrwx--- 1 root plugdev    0 2008-07-26 03:27 test
root@nas:/home/administrator# 

In the fstab I also mounted with ntfs-3g so it should be read and write?

I can now acces the NAS server but not the share. Making _some_ progress :)

Here is my smb.conf now:

> # Samba config file created using SWAT
# from 213.132.124.3 (213.132.124.3)
# Date: 2008/07/30 02:50:29

[global]
	workgroup = MSHOME
	server string = %h server (My NAS)
	security = SHARE
	encrypt passwords = No
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = No
	create mask = 0700
	guest ok = Yes
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	guest ok = Yes

[media]
	path = /media/store
	admin users = root
	force user = nobody
	force group = nogroup
	read only = No
	acl check permissions = No
	create mask = 0777
	force create mode = 0777
	force security mode = 0777
	directory mask = 0777
	force directory mode = 0777
	force directory security mode = 0777
	guest only = Yes
	guest ok = Yes
	case sensitive = No
	short preserve case = No
	hide dot files = No
	blocking locks = No
	locking = No
	posix locking = No
	volume = /dev/sda3
	fstype = NTFS-3g
	set directory = Yes

Thanks

---

### Post by zeezam on 2008-07-31
It seems to be the permission for the partition. Tried with chmod 77, chmod a+rw etc.

Still no permission for "everybody".


drwxrwx--- 1 root plugdev 4096 2008-07-31 06:07 store
administrator@nas:~$

---

