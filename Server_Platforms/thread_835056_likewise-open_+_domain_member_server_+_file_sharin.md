---
title: "likewise-open + domain member server + file sharing on Hardy"
date: 2008-06-20
forum: Server Platforms
---

### Post by abenmao on 2008-06-20
I'm new to linux and trying to use Ubuntu 8.04 server as a domain file server. but I got a file sharing permission issue after setting up the linux box. What I have done is as follows:

1) Install Ubuntu 8.04 Server on a spare PC
2) create a dedicated ext3 partition for file sharing and mount it to /samba
3) tasksel "Samba File Server" and "Print Server" only
4) add acl support for /samba in /etc/fstab
5) install likewise-open with the following commands
   sudo apt-get install likewise-open
   sudo domainjoin-cli join csgraphics.local administrator
   sudo update-rc.d likewise-open defaults
6) touch up /etc/samba/lwiauthd.conf
   added:
        winbind use default domain = yes
7) after rebooting, I'm able to use the administrator user of csgraphics.local to login to Ubuntu and SUDO is working fine
8) create a shared fold in /samba
   sudo mkdir /samba/shares/data
   cd /samba/shares
   sudo chgrp "Domain Users" data
   chmod 755 data
9) insert the following lines to /etc/samba/lwiauthd.conf
   winbind enum users = yes
   winbind enum groups = yes
10) add the follwoing lines to /etc/samba/smb.conf
   [data]
     path = /samba/shares/data
     nt acl support = yes
     browseable = yes
     writeable = yes
     public = yes
     read only = no
     create mask = 0775
     directory mask = 0775
     force create mode = 0775
     force directory mode = 0775
     force security mode = 0775
     guest ok = no
     inherit permissions = yes


Problem:
  from a window 2k3 DC,
     create files or folders in \\ubuntus\data     permission denied

Please help. many thanks for all the posts

permissions show from the windows box
[IMG]http://www.csgraphics-world.com/image/permission.jpg[/IMG]

---

### Post by Xerp on 2008-06-26
Hi :)

Take a look here for info on Likewise Open and Samba:

[http://archives.likewisesoftware.com/~gcarter/drafts/Likewise-SambaGuide.pdf](http://archives.likewisesoftware.com/~gcarter/drafts/Likewise-SambaGuide.pdf)

Works for the Enterprise and Open editions.

---

### Post by Themicles on 2008-06-27
> **Xerp said:**
> Hi :)

Take a look here for info on Likewise Open and Samba:

[http://archives.likewisesoftware.com/~gcarter/drafts/Likewise-SambaGuide.pdf](http://archives.likewisesoftware.com/~gcarter/drafts/Likewise-SambaGuide.pdf)

Works for the Enterprise and Open editions.
Except that there doesn't appear to be a centeris folder under /usr with likewise-open. At least there isn't on my recent install...

What would I do about the symbolic link step?

EDIT:
Nevermind, I am extremely blind and missed the likewise-open folder.

---

### Post by Themicles on 2008-06-27
Okay, followed the instructions and everything seemed to be going okay until I ran wbinfo -t.

The results are as follows:
checking the trust secret via RPC calls failed
error code was NT_STATUS_INVALID_HANDLE (0xc0000008)
Could not check secret

I followed every step to the letter except adapting the paths.

Suggestions?

EDIT:
Okay, restarted samba and winbind again and it started working. *shrugs* Not sure why it failed the first time.

---

### Post by abenmao on 2008-06-28
> **Xerp said:**
> Hi :)

Take a look here for info on Likewise Open and Samba:

[http://archives.likewisesoftware.com/~gcarter/drafts/Likewise-SambaGuide.pdf](http://archives.likewisesoftware.com/~gcarter/drafts/Likewise-SambaGuide.pdf)

Works for the Enterprise and Open editions.

thanks, I will test it and see if it works for me

---

### Post by inselaffe on 2008-07-09
> **Themicles said:**
> 

What would I do about the symbolic link step?

EDIT:
Nevermind, I am extremely blind and missed the likewise-open folder.

Where did you find liwcompat_v2.so and lwicompat_v4.so to link to? In /usr/lib/likewise-open/idmap there is only lwopen.so.

---

### Post by joe.davis on 2008-07-11
> **inselaffe said:**
> Where did you find liwcompat_v2.so and lwicompat_v4.so to link to? In /usr/lib/likewise-open/idmap there is only lwopen.so.
I can't find the liwcompat_v2.so and lwicompat_v4.so files either. Does anyone know where they would be located?

---

### Post by mem on 2008-07-11
read my post here.

[http://ubuntuforums.org/showthread.php?p=5348109#post5348109](http://ubuntuforums.org/showthread.php?p=5348109#post5348109)

short story: version in repos is crippled. install using official installer.

longer story: dont use this. it's not so bad doing it the 'long' way and you dont have to depend on this software.

---

### Post by Themicles on 2008-07-12
> **mem said:**
> read my post here.

[http://ubuntuforums.org/showthread.php?p=5348109#post5348109](http://ubuntuforums.org/showthread.php?p=5348109#post5348109)

short story: version in repos is crippled. install using official installer.

longer story: dont use this. it's not so bad doing it the 'long' way and you dont have to depend on this software.
I've done it both ways now, and far prefer Likewise-open.

The symlink you're creating is being created in the likewise-open folder, linking to the actual files in the other.

Now I have run into a new problem of my own. Server has been up for 18 days and appears to have magically lost link with active directory on the domain controllers. First noticed when an admin on the network no longer had sudo, and then after rebooting the Linux server, domain accounts cannot log in...

---

### Post by inselaffe on 2008-07-14
> **mem said:**
> longer story: dont use this. it's not so bad doing it the 'long' way and you dont have to depend on this software.

Which "long way" did you take? I've seen quite a few guides to this and they are all subtly different.

---

### Post by Themicles on 2008-07-14
> **Themicles said:**
> Now I have run into a new problem of my own. Server has been up for 18 days and appears to have magically lost link with active directory on the domain controllers. First noticed when an admin on the network no longer had sudo, and then after rebooting the Linux server, domain accounts cannot log in...

To update on this, the problem looks like it was on the domain controller's end (I sometimes notice similar when XP machines on the network can't log into network shares). It started working again on it's own without further poking of the Linux box.

---

### Post by billgarcia on 2009-06-12
> **mem said:**
> read my post here.

[http://ubuntuforums.org/showthread.php?p=5348109#post5348109](http://ubuntuforums.org/showthread.php?p=5348109#post5348109)

short story: version in repos is crippled. install using official installer.

longer story: dont use this. it's not so bad doing it the 'long' way and you dont have to depend on this software.

Could you post more info on the steps you took? I've worked verbatim through those guides, and by wbinfo -t 's still fail miserably. :'(

---

