---
title: "HELP Many Failed Logins at start up. Cannot login"
date: 2008-05-21
forum: Server Platforms
---

### Post by JameoPotato on 2008-05-21
When the 8.04 server starts up it seems to be going well until it I see numerous processes beginning to fail all because of incorrect logins.
ex, "invalid user 'www-data'" shows up for a lot of things including saying users are "Dovecoat" and "root"

Along with this i cannot login to my regular account anymore. 

UPDATE:
So after doing a bit of googling i discovered that i overwrote a crucial file that store login information... /etc/passwd . 
Just in my defense the reasoning behind me choosing that file was because htpasswd was refusing to write to /etc/vsftpd/passwd... so i decided "Hey lets just move it up a directory" well go figure that one directory up was a crucial file. 

So new question is:
How do I get myself out of this pickle. **It there anyway to recover this file? Would it have been unique to my user? Could I copy and write it from the recovery shell??? Is there a such this as system restore in ubuntu??**

---

### Post by spiderbatdad on 2008-05-21
This post would receive more attention in the Absolute beginner forum. :)

Always make backups of files before overwriting or editing excessively:
```
sudo cp -p -r /etc/passwd /etc/passwd_backup
```

Unfortunately I don't know how to solve this issue yet, but am interested.

On second thought, it is almost a certainty that the system created a backup for you.
Use the live cd and mount your file system:
```
sudo mkdir /media/sda
sudo mount -t ext3 /dev/sda1 
```
Assuming sda1 is your ubuntu partition.
sudo fdisk -l will tell you.
 then delete /etc/passwd and cp the backup (/etc/passwd-) to a new /etc/passwd

```
 sudo cp -p -r /etc/passwd- /etc/passwd 
```

Of course verify the file exists, and is named /etc/passwd-

---

### Post by mdr on 2008-05-22
If your shadow file is there still you can recreate the passwd file using pwunconv I believe.
/etc/shadow
/etc/shadow~

Passwords in the passwd file are updated from the shadow file. Entries which exist in the passwd file but not in the shadow file are left alone. Finally, the shadowed file is removed. 

Check all is ok and then use pwconv to recreate the shadow file.  (Better for security reasons).

Other than that it is the off the installation media.

---

