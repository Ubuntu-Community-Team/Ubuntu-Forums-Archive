---
title: "ERROR: Encrypted private directory is not setup properly"
date: 2010-02-23
forum: Security
---

### Post by ushills on 2010-02-23
I have a problem creating a user with an encrypted home folder, when I create a new user all seems to go well.

```
ubuntu@ubuntu:~$ sudo adduser --encrypt-home encrypt
Adding user `encrypt' ...
Adding new group `encrypt' (1002) ...
Adding new user `encrypt' (1002) with group `encrypt' ...
Creating home directory `/home/encrypt' ...
Setting up encryption ...

************************************************************************
YOU SHOULD RECORD YOUR MOUNT PASSPHRASE AND STORE IT IN A SAFE LOCATION.
  ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.
************************************************************************


Done configuring.

Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for encrypt
Enter the new value, or press ENTER for the default
	Full Name []: Encrypted User
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] Y
ubuntu@ubuntu:~$ sudo login encrypt
Password: 
Linux ubuntu 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

encrypt@ubuntu:~$ ls
Access-Your-Private-Data.desktop  README.txt

```

All appears to go well, but when I try to mount the Private /home folder I get the following error.

```
encrypt@ubuntu:~$ ecryptfs-mount-private 
ERROR: Encrypted private directory is not setup properly
encrypt@ubuntu:~$ 

```

I cannot get around this at all and it happens everytime.

---

### Post by ben2talk on 2010-05-02
Seems this never worked - I had an encrypted Home, but now I don't have access - and it seems it was never set up right, though Ubuntu used it normally until now... so several things accumulated over the past year (a lot of work....) are now scrambled and inaccessible :(

<snip> Ubuntu - not happy about this!!!

Makes it seem worth spending a little extra for a shiny Macbook Pro doesn't it? :)

---

### Post by roomey on 2011-06-22
[http://ubuntuforums.org/showthread.php?t=1661060](http://ubuntuforums.org/showthread.php?t=1661060)

Does this help at all?
I had a problem creating encrypted user directories when I had a strict umask. Had to change umask to 022 to fix

---

