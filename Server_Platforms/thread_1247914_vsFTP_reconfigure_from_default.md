---
title: "vsFTP reconfigure from default"
date: 2009-08-23
forum: Server Platforms
---

### Post by patll on 2009-08-23
I'm a newbie and have been reading and configuring(messing things up further) the default vsftp config with no luck.

I'm able to login using cuteftp pro from a M$ xp box over an internal network, so it appears to be working, but having trouble configuring further and now it won't let me in.

Trying to:
1. give an off site tech/programmer permission to install and configure a www app. - can't navigate out of " /" (is what shows up on cuteftp) which is /srv/ftp
2. copy files - don't have permission it says
3. are there instructions (which I couldn't find) on how to set vsftp as you would see at a hosted site, defaulted to www with permissions setup to upload apps, web sites, etc., this seems really arcane and complex(I thought it shouldn't be so complicated, maybe a wrong assumption).

I have some limited experience and assumptions from using hosted servers where it gives you access to the www and above, which is what I'm trying to do.

one help site suggested changing the default by using:
To change your ftp root directory, as root, edit /etc/vsftpd/vsftpd.conf and add the following line:

local_root=/opt  (changing /opt  to /www or var/www
  ... and restarting vsftp, which didn't work

2. when trying to copy files to the default ftp, permissions denied. The ftp was set up as suggested using anonymous and I could log in, just not copy.

Thanks, any help is appreciated.

---

### Post by hessiess on 2009-08-23
use sftp instead and create a new system user with the home dir set to /var/www/, then log in using sftp and that user. If you are alowing multiple people to use your server, you should also set it up as a shared hosting server, i.e. do not have every user logging in with the same user and assessing the same files, preferably also run php(if you are using it) as a fastcgi app to get it running as the user that owns the site and not the Apache user. then you can chmod the individual web roots to 700 preventing other users viewing the files.

---

### Post by patll on 2009-08-23
> **hessiess said:**
> 1. use sftp instead and create a new system user with the home dir set to /var/www/, then log in using sftp and that user. 2. If you are alowing multiple people to use your server, you should also set it up as a shared hosting server, 3. i.e. do not have every user logging in with the same user and assessing the same files, preferably also run php(if you are using it) as a fastcgi app to get it running as the user that owns the site and not the Apache user. 4. then you can chmod the individual web roots to 700 preventing other users viewing the files.

Thanks for the reply
So I understand you. 
1. Dump/Uninstall the vsftp and install sftp instead.  And is that because sftp is easier, etc.?
2. Setting up the "shared hosting server" is within sftp or within ubuntu?
3. "also run php(if you are using it) as a fastcgi app" if you could point to where that would be explained in more detail? It's setup as a LAMP server.
4. How... web roots?
Sorry, as said I'm a newbie so any help with further tutorials, so I don't have to search for hours and piecing together various help posts.

Thanks

---

### Post by cariboo on 2009-08-23
If you have openssh-server installed, you don't need to do anything else, as sftp is part of the openssh-server package. Most ftp clients can also use sftp to transfer files.

Create a user and password for the offsite person and make him a member of the the www-data group. he sould be then able to copy files to /var/www.

Edit: after your offsite person is finished, remember to delete the user.

---

