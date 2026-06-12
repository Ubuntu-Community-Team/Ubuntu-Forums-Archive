---
title: "Chrooted SSH/SFTP - Files ownership/permissions"
date: 2009-02-10
forum: Server Platforms
---

### Post by DeepThoughts on 2009-02-10
I've recently set up a home server using Ubuntu Server 8.10 and so far this works really good. LAMP, Samba and OpenSSH all up and running as they should. Using the builtin chroot-functionality of OpenSSH I've enabled chrooted SFTP for family and friends (this was dead easy, thanks OpenSSH!).

My issue is more of an annoyance than issue, when a user uploads that file is owned by that user (which makes managing the files a little bit "harder" but not impossible). So my question is: Is there away to force the uploaded files to be owned by another user (preferably mine :P )? What I'm looking for is something like Sambas "force user", if that doesn't exist can I set some funky permissions on the upload folder that would help me in this? The folder is mounted using "mount --bind" if this helps or complicates things. Or is it possible to create some kind of script that runs every night?

Any ideas on how to get rid of this annoyance is appreciated.

---

### Post by cdenley on 2009-02-10
You can either use ACL's, or you can create a script in /etc/cron.daily to change permissions on files.
[http://ubuntuforums.org/showthread.php?p=5918610](http://ubuntuforums.org/showthread.php?p=5918610)

You could probably also change the umask to make files the user creates world readable or writable.

---

### Post by DeepThoughts on 2009-02-10
> **cdenley said:**
> You can either use ACL's, or you can create a script in /etc/cron.daily to change permissions on files.
[http://ubuntuforums.org/showthread.php?p=5918610](http://ubuntuforums.org/showthread.php?p=5918610)

You could probably also change the umask to make files the user creates world readable or writable.

Thank you! I chose the ACL-path and so far it's working as I want it. Many thanks for pointing me in that direction.

---

### Post by narcisgarcia on 2010-10-10
Here my guide to configure better clients and servers:

[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(special care of users and permissions)

---

### Post by narcisgarcia on 2012-10-30
A domain name has changed for Lapipaplena. Please update the link for:
[http://wiki.gilug.org/index.php/How_to_mount_SFTP_accesses](http://wiki.gilug.org/index.php/How_to_mount_SFTP_accesses)

---

