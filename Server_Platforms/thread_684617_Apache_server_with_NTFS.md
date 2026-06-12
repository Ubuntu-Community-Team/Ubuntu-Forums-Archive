---
title: "Apache server with NTFS"
date: 2008-02-01
forum: Server Platforms
---

### Post by monkey56657 on 2008-02-01
Hello. 

I would like to have my apache server setup to load everything from an NTFS partition (Document Root)...

I set this up in the configs as required but find that whenever the NTFS location is chosen the "403 forbidden" is displayed to any user. I have tried to change the owner and the permissions on the NTFS volume but changing them seems to have no effect and they revert to the originals. I have heard that full permission support isnt available on NTFS under ubuntu but I used to have this working. The folder (when on windows) isnt protected in any way. 

Can I run the server as my own user rather than "www-data" ?

Another thing I have a problem with is I have to use "sudo apache2" to start the server as "apache2" alone doesn't work (no errors displayed) which means its actually having to run as root + www-data following that. 

Thanks for your time..

---

### Post by cdenley on 2008-02-01
You're starting apache manually? Only root can bind to port 80. I'm not sure if that will work if you change the port. Normally, you would start apache by running "sudo /etc/init.d/apache2 start".

You should be able to fix the permissions by changing umask and fmask in the mount options. How do you mount the nfts partition?

---

### Post by monkey56657 on 2008-02-03
The partitions were already mounted once ubuntu was installed. 

The umask is current 007 in fstab.

---

### Post by cdenley on 2008-02-03
> 
The umask is current 007 in fstab.

There is your problem. Apache accesses files as user www-data. You either need to give www-data ownership at mount, or change the umask in /etc/fstab so all users have access. A more practical solution would be to use ext3 instead, so that unix permissions can be applied to specific files and directories.

---

### Post by monkey56657 on 2008-02-04
> or change the umask in /etc/fstab so all users have access

What shall I change it to?

I cant really use ext3 as then windows wont have access.

---

### Post by cdenley on 2008-02-04
> What shall I change it to?
002 will give all users read access. 000 will give everyone full access.

> 
I cant really use ext3 as then windows wont have access.

[http://gentoo-wiki.com/Ext3_in_windows](http://gentoo-wiki.com/Ext3_in_windows)

---

### Post by monkey56657 on 2008-02-04
You see I knew I thought I understood it (if that makes sense). I did try umask as 000 once before but it just didnt work at all then!

Well ill try again thanks.

---

### Post by monkey56657 on 2008-02-05
Wow it worked wonderfully this time. Cant believe it :lolflag:

Thanks for the help :popcorn:

---

