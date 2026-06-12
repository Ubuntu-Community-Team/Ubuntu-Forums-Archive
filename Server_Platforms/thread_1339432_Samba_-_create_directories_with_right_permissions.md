---
title: "Samba - create directories with right permissions"
date: 2009-11-27
forum: Server Platforms
---

### Post by samcoles on 2009-11-27
Hi,

I've set up a samba server on a computer running debian under the stairs and mounted it on my ubuntu desktop on the PC in my room by putting the mount command in /etc/fstab, the sambashare folder contains my music right now and is working. The sambashare is chown'd to the user that logins to the samba server and chmod'd rwx to the user. It is at /sambashare on the debian computer.

I can copy files to it, however, if I try to drag a folder containing say a bunch of image files to it, then it creates the directory but this new directory does not have write permissions for the user so there is then an error trying to copy the files into the newly created directory. I can of course just chmod this from the debian computer but that's not the point, is it?

What I want is for all directories and files created in the sambashare from my PC upstairs to be chown'd by the correct user and chmod'd correctly... I can post my config file if need be.

Any help much appreciated, be gentle, I am new to this linux lark. Thanks.

---

