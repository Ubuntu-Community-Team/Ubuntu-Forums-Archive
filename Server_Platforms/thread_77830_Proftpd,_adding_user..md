---
title: "Proftpd, adding user."
date: 2005-10-17
forum: Server Platforms
---

### Post by Aven on 2005-10-17
Alright, I followed the tutorial: [http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611)

Reeeeeeeally helpful.

I am able to create a user and everything, however.. the password is never valid. And I've added multiple users with different passwords and they still don't work.

Isn't this the correct method? 

I put:

sudo useradd Aven -p password -d /home/directory -s /bin/false

then logged in with:
username: Aven
Password: password

isn't that how it's supposed to be done? if so, it always says "wrong password"

Any help would be apprectiated.

---

### Post by mcewen98 on 2005-10-17
I use vsftpd, but for the ftp user I set their shell to /bin/sh

I'm not sure if it matters, but they do not belong to the ssh user group (I dont' think it does because I Just tried it with and without).  This denys them from being able to ssh to the machine, but they can still authenticate with ftp.

Then, in the vsftpd.conf file there is a setting to lock users to their home directories: 

chroot_local_user=YES

You can even create a list of users to not be locked to their home directory.  I'm not sure if there is something similar with proftpd or not.

EDIT: You must also edit /etc/ssh/sshd_config and add DenyUsers ftpuser to the bottom of the file to deny ssh access

---

### Post by majikstreet on 2005-10-17
Here is my experience:
I set up an Ubuntu server *with no X*. I tried to SSH in, and I always got wrong password. I had a 7 page thread trying to get it working. Then I discovered that inmy password, which is upper case and includes the uppercase letters C and E, those letters were LOWERCASE because I set themon a PC with no X.
(I use CAPS-LOCK for my uppercase letters)
There may be MORE letters like that, but for all I know, using caps-lock with C and E, they turn out lowercase on a machine with no X.

HTH,
majikstreet

---

### Post by Sheep Me on 2005-10-21
[QUOTE=Aven]sudo useradd Aven -p password -d /home/directory -s /bin/false[/QUOTE]I had the same problem with vsftpd. As it turns out, useradd expects an encrypted password. Have a look in the manual of useradd. I couldn't find out how to make an encrypted password, so I changed the password from System > Administration > Users and Groups (in GNOME), and it worked.

---

