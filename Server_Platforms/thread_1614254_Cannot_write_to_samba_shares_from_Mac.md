---
title: "Cannot write to samba shares from Mac"
date: 2010-11-05
forum: Server Platforms
---

### Post by neufena on 2010-11-05
This is (I suspect) a Mac OS issue but they've given no help (or replies!) on Mac forums so I'll ask here.

I've just got a Mac and I can connect to shares on my Ubuntu (10.04) server, read files and create directories but I cannot write. I get this error:

"The operation cannot be completed because you do not have sufficient privileges for some of the items."

I can connect from the command line with smbclinet and write fine. I have tried several different users on both the Mac (cannot write) and Ubuntu clients (can write).

Is this something to do with the ._filename files that finder creates?  Or is there something wrong with the way I've set up my server?  This is the first time I've used it with a Mac client.

Thanks,

---

### Post by alienprdkt on 2010-11-05
I was having this issue last night... what worked for me is make sure you give the correct permissions to all folders for me is was 

sudo smbpasswd -a <username> 

make sure it is a system username, then

chown username:username /smb-share

chmod -R u+r+w,go-w /smb-share	

change the permissions of the directory /smb-share and all its contents to add read + write access for the user, and deny write access to all others 
[http://en.wikipedia.org/wiki/Chmod]("http://en.wikipedia.org/wiki/Chmod") - towards the bottom where it says "Command line examples"

my problem was giving permission -R (copy directories recursively) 

hope that helps...

---

### Post by Morbius1 on 2010-11-05
If that doesn't resolve the issue post the output of the following commands on the server so we can see how you are set up:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by neufena on 2010-11-06
I have (maybe) something that'll help.  I set up 2 test shares on the main drive, the other shares are all on an external fat32 drive.  The shares on the main drive work fine.

net userinfo returns nothing

testparm -s returns

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[htdocs]"
Unknown parameter encountered: "valid user"
Ignoring unknown parameter "valid user"
Processing section "[videos]"
Processing section "[mp3s]"
Processing section "[pictures]"
Processing section "[shares]"
Processing section "[flacs]"
Processing section "[test1]"
Unknown parameter encountered: "valid user"
Ignoring unknown parameter "valid user"
Processing section "[test2]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = Server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	create mask = 0644

[htdocs]
	comment = Web Server
	path = /mnt/maxtor/htdocs
	read only = No
	locking = No
	posix locking = No

[videos]
	comment = Videos
	path = /mnt/maxtor/Videos
	read only = No
	guest ok = Yes

[mp3s]
	comment = Music
	path = /mnt/maxtor/Mp3s
	read only = No
	guest ok = Yes

[pictures]
	comment = Pictures
	path = /mnt/maxtor/Pictures
	read only = No
	guest ok = Yes

[shares]
	comment = Shares
	path = /mnt/maxtor/Shares
	read only = No
	guest ok = Yes

[flacs]
	comment = Flacs
	path = /mnt/maxtor/Flac
	read only = No
	guest ok = Yes

[test1]
	comment = Testing Login
	path = /srv/test
	read only = No
	locking = No
	posix locking = No

[test2]
	comment = Testing Guest
	path = /srv/test
	read only = No
	guest ok = Yes


Any ideas?

---

### Post by arnavk007 on 2010-11-06
> **neufena said:**
> I have (maybe) something that'll help.  I set up 2 test shares on the main drive, the other shares are all on an external fat32 drive.  The shares on the main drive work fine.

net userinfo returns nothing

testparm -s returns

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[htdocs]"
Unknown parameter encountered: "valid user"
Ignoring unknown parameter "valid user"
Processing section "[videos]"
Processing section "[mp3s]"
Processing section "[pictures]"
Processing section "[shares]"
Processing section "[flacs]"
Processing section "[test1]"
Unknown parameter encountered: "valid user"
Ignoring unknown parameter "valid user"
Processing section "[test2]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = Server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	create mask = 0644

[htdocs]
	comment = Web Server
	path = /mnt/maxtor/htdocs
	read only = No
	locking = No
	posix locking = No

[videos]
	comment = Videos
	path = /mnt/maxtor/Videos
	read only = No
	guest ok = Yes

[mp3s]
	comment = Music
	path = /mnt/maxtor/Mp3s
	read only = No
	guest ok = Yes

[pictures]
	comment = Pictures
	path = /mnt/maxtor/Pictures
	read only = No
	guest ok = Yes

[shares]
	comment = Shares
	path = /mnt/maxtor/Shares
	read only = No
	guest ok = Yes

[flacs]
	comment = Flacs
	path = /mnt/maxtor/Flac
	read only = No
	guest ok = Yes

[test1]
	comment = Testing Login
	path = /srv/test
	read only = No
	locking = No
	posix locking = No

[test2]
	comment = Testing Guest
	path = /srv/test
	read only = No
	guest ok = Yes


Any ideas?
You have nothing which says writable = yes
morbius does he need to modify his smb.conf
also you have no users set up I think
maybe that could be a problem

---

### Post by neufena on 2010-11-06
I have 2 users set up and everything works fine from my laptop when booted into Ubuntu or Windows (with either user).  It's just from Mac OS X that I have the problems

To my knowledge you only need one of Read Only = No or Writable = Yes

---

### Post by arnavk007 on 2010-11-06
oh if it is working with other clients.
i am puzzled
you may use nfs with the macs

---

### Post by Morbius1 on 2010-11-06
First you might want to fix the error message from testparm:
> Unknown parameter encountered: "valid user"
Ignoring unknown parameter "valid user"It's not "valid user" it's "valid users" - with an "s" at the end. You know how picky Linux can be :wink:

You might want to post the output of the following command so we can see how ownership and permissions are set up on the target directories:
```
ls -al /mnt/maxtor
```Also since the mountpoint location is in /mnt you might want to post the line in fstab that you used to mount /mnt/maxtor.

---

### Post by neufena on 2010-11-06
OK, here's the result of ls -al /mnt/maxtor


drwxrwxrwx 13 root root 16384 1970-01-01 01:00 .
drwxr-xr-x  4 root root  4096 2010-10-20 19:31 ..
drwxrwxrwx 12 root root 16384 2010-11-04 20:18 Dropbox
drwxrwxrwx  3 root root 16384 2010-10-14 17:19 .dropbox-neufena
drwxrwxrwx  6 root root 16384 2010-11-05 14:39 Flac
-rwxrwxrwx  1 root root    62 2010-10-30 12:52 .hidden
drwxrwxrwx 42 root root 16384 2010-11-05 00:46 htdocs
drwxrwxrwx 13 root root 16384 2010-11-04 10:14 Mp3s
drwxrwxrwx  2 root root 16384 2010-10-12 14:04 Pictures
drwxrwxrwx 15 root root 16384 2010-11-06 11:19 Shares
drwxrwxrwx  5 root root 16384 2010-10-03 20:06 .Trash-1000
drwxrwxrwx  3 root root 16384 2010-09-15 16:44 .Trashes
-rwxrwxrwx  1 root root  4096 2010-09-15 16:44 ._.Trashes
drwxrwxrwx  7 root root 16384 2010-11-04 09:28 Videos

The fstab line that mounts this drive is

UUID=46DD-841A          /mnt/maxtor     vfat    user,auto,umask=000,dmask=000,fmask=000        0       0

As you can see it's a FAT32 drive, I want to try converting it to ext3/4 as I only use it with my server these days but haven't got another drive to copy the files to while I do that!!

Since I can copy files from the mac using smbclient on the command line I think it's something to do with Finder.  I know it creates annoying ._filename files with extended mac attributes for each file, could it be that (for some reason) filenames starting ._ are not allowed on fat32?

fixed the valid users line. Thanks

---

### Post by Morbius1 on 2010-11-06
I'll be darned ( family forum you know ).

I don't have an fat32 partition on this box but I do have an ntfs partition and the mac can access and edit ( write ) to anything it wants on that shared partition.  What I never realized before your post is that only by chance did I set up the mount point of the ntfs partition and the share in such a way that it's the only way the mac can write.

I use a different method of samba sharing called usershares but the principle is the same using classic shares which you are using. I tested it out in VBox so I think it might just work:

Modify the fstab line and add one more option ( uid=1000 ) so that you take possession away from root:
```
UUID=46DD-841A          /mnt/maxtor     vfat    uid=1000,user,auto,umask=000,dmask=000,fmask=000        0       0
```uid=1000 should be you but just in case run the following command to make sure:
```
id
```Now unmount the maxtor partition:
```
sudo umount /mnt/maxtor
```Then run the following to check for errors an mount things again:
```
sudo mount -a
```Take one share ... say the [shares] share and add one line so that looks like this:
> [shares]
    comment = Shares
    path = /mnt/maxtor/Shares
    read only = No
    guest ok = Yes
[COLOR=Blue]**     force user = neufena**[/COLOR]
[COLOR=Blue][I]Change neufena to your actual Ubuntu login user name. It should be the one that corresponds to the uid=1000 parameter in fstab.

[/I][COLOR=Black]Save the file and restart samba:
[/COLOR][/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```

---

### Post by neufena on 2010-11-10
Thanks Morbius1, that's fixed it all.

---

