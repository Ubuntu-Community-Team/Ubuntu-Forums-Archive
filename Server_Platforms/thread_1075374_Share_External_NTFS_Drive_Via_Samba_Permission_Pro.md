---
title: "Share External NTFS Drive Via Samba Permission Problem"
date: 2009-02-20
forum: Server Platforms
---

### Post by -tom-64 on 2009-02-20
Hi Everyone,

I am interested in sharing an external drive via samba which is installed on my ubuntu server 8.04.2.

I have read a few other threads to find out if it was possible and it seems that there have been a few problems. If I can get this to work with your help, I will write out how to do it, so others can easily find out what to do.

Threads related:

[http://ubuntuforums.org/showthread.php?p=6447686](http://ubuntuforums.org/showthread.php?p=6447686)
[http://ubuntuforums.org/showthread.php?t=332310](http://ubuntuforums.org/showthread.php?t=332310)
[http://ubuntuforums.org/showthread.php?t=1023084](http://ubuntuforums.org/showthread.php?t=1023084)

So far I have:

Formatted the external drive (USB) as NTFS

Installed the ntfs-3g by doing apt-get install ntfs-3g

Now I can access the drive at /media/usb/

I have made share in samba by adding the following:

[netbackup]
	comment = Network Backup Share
	path = /media/usb/
	read only = No
	guest ok = Yes

Running a testparm reveals all is correct.

I can now access the share on my mac at dc01-ubuntu\netbackup 

I have a file called test.txt in the drive which I created on the server. 

The problem I have, is with permissions! I can open the drive, view the files inside, open the txt file, but cannot edit the file and save it.

What do I need to change? Is it just a alteration to the smb.conf file?

Thanks ahead for the help,

Tom

---

### Post by HermanAB on 2009-02-20
Samba is a PITA.  NFS is a *lot* easier to get to work.

However, that being said, try setting the permissions on the drive to 777.

Cheers,

Herman

---

