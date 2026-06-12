---
title: "web publishing - noob question"
date: 2009-10-28
forum: Server Platforms
---

### Post by uDavis on 2009-10-28
When people have one web server and 4 different publishers how is ubuntu set up to service the ftp clients for these 4 authors?

Would you give them access all to /var/www/dir1... dir4 and then CHMOD the dir1...dir4 dirctories?

Or do you put their web sites into their home directories.

The result I am looking for is web sites that respond to

[http://website1.com/dir1/](http://website1.com/dir1/)
[http://website1.com/dir2/](http://website1.com/dir2/)
[http://website1.com/dir3/](http://website1.com/dir3/)
[http://website1.com/dir4/](http://website1.com/dir4/)

Should dir1 be /var/www/dir1 or /home/username/dir1?  

thanks

---

### Post by elvinatom on 2009-10-28
I need someone to verify this, but I believe that you can chroot the ftp paths depending on who's logged into the ftp server.  You could then have them not even see the other authors sites when using ftp.

---

### Post by Lars Noodén on 2009-10-29
(BTW: I'm becoming very curious about the apparent resurgence of interest in using the FTP protocol in an unsafe way.  It should have died out in 2000 for all uses except some read-only downloads.  )

dir1 should be /var/www/dir1 

Make a group for each team.  Make dir1 writeable by team1, dir2 by team2, etc.

Then make sure you have openssh-server installed.  Configure sshd so that each team gets chrooted to their directory.

```

Subsystem sftp internal-sftp

Match Group team1
   ChrootDirectory /var/www/dir1
   AllowTCPForwarding no
   X11Forwarding no
   ForceCommand internal-sftp

Match Group team2
   ChrootDirectory /var/www/dir2
   AllowTCPForwarding no
   X11Forwarding no
   ForceCommand internal-sftp

Match Group team3
   ChrootDirectory /var/www/dir3
   AllowTCPForwarding no
   X11Forwarding no
   ForceCommand internal-sftp

Match Group team4
   ChrootDirectory /var/www/dir4
   AllowTCPForwarding no
   X11Forwarding no
   ForceCommand internal-sftp

```

Then they can all connect using sftp and have access to that they should have access to.  If you need a gui client for sftp, then either filezilla can use sftp or you can use sshfs with the regular file manager.

---

