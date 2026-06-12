---
title: "[SOLVED] minimal backup and restore"
date: 2008-06-19
forum: Server Platforms
---

### Post by dummzeuch on 2008-06-19
Hi,

I am currently building a server for a small company. Everything so far is working, apart from system backup and restore (user data is backupped separately).

I thought I could do the following:

1. do a daily backup of /etc
2. backup the list of installed packages

for a restore:

1. install ubuntu server from cd
2. update all packages
3. install packages from the list created above
4. restore /etc

Of course I did a test before going life. It seems to work, mostly. What apparently isn't restored are the user accounts, that is, the Linux users are actually restored and after restoring their home directories as well, I could log in fine. The samba users are also restored, but the passwords seem to be missing.

So what did I forget to backup/restore? Or do I really have to do a full backup/restore of the system (minus data partitions)?

twm

---

### Post by tcpip4lyfe on 2008-06-19
I assume you are using rsync?  I believe that the samba password file is in /usr/local/samba/ somewhere.  Check your smb.conf and see what directory it's located in, include it in your rsync and then try it again.

---

### Post by dummzeuch on 2008-06-19
> **tcpip4lyfe said:**
> I assume you are using rsync?  I believe that the samba password file is in /usr/local/samba/ somewhere.  Check your smb.conf and see what directory it's located in, include it in your rsync and then try it again.

I am using dirvish for the backup and tried cp -R for the restore.

smb.conf is located in /etc/samba which is already included in the backup as well as in the restore.

twm

---

### Post by dummzeuch on 2008-06-19
Ok, apparently some of the Samba data is not in /etc/samba, as I expected, but in /var/lib/samba. I guess it is a good idea to not only backup/restore /etc but also /var/lib.

I haven't tried it yet, but will tomorrow.

[edit]

It seems to work. I have included /var/lib/samba in the restore and now at least the users and shares are restored correctly.

I'll still have to figure out whether any other of the /var/lib directories are necessary.

twm

---

