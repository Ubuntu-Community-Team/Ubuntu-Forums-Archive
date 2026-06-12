---
title: "mount --bind FTP lost files"
date: 2007-02-16
forum: Server Platforms
---

### Post by kramerkeller on 2007-02-16
Somehow I lost all my ftp files, but I THINK THEY ARE STILL THERE?

So I wanted to allow a web administrator access to multiple files on the server.  I chrooted the webadmin into an ftp folder.  Then I did mount --bind to the folders to which I wanted to allow access.

Everything was working fine, but then I used mount --bind myself and noticed his "links" were not working anymore.  So I thought at first you cannot bind with multiple times to a file.  Then I realized that the computer may have restarted adn I may not have set the computer to remount.

So somewhere in all this none of the files are linking together because I kept trying to fix and made it worse.  the next thing you know I can't see a good amount of files that were in the FTP folder.

However, when i do -df it looks like those files are still taking up space

Is there anyway I just lost a way to point to these files and if so is there anyway to find them again?

---

### Post by kramerkeller on 2007-02-17
I just rebooted and everything is fixed.  Alright, now for the record.  How do I mount a folder so that I can access it via FTP through a home folder, and then how do I make sure that folder stays mounted.  Is that something in mtab or fstab or something?

---

### Post by datablitz7 on 2008-01-26
I have the same problem to overcome... Same question for me.

---

### Post by Vinno on 2008-01-27
[http://www.vinno.net/linux/server/chroot-mount-trick](http://www.vinno.net/linux/server/chroot-mount-trick) :)

---

### Post by datablitz7 on 2008-01-27
Can you mount --bind a mount --bind-ed dir??
ie: mount --bind /var/www/torrentflux/downloads/ /home/user/Torrents
mount --bind /home/user/ /home/user2/Downloads

would the mount work for user2 home?

---

### Post by datablitz7 on 2008-01-28
Vinno i used you way but i cannot get it to stick...
here's my entry in /etc/fstab:

/var/www/torrentflux/downloads/datablitz7       /home/datablitz7/Torrents  ext3  auto,suid,defaults,exec,nodev  0  0


but it gives me /var/www/torrentflux/downloads/datablitz7 is not a block device...

What am I doing wrong?

---

