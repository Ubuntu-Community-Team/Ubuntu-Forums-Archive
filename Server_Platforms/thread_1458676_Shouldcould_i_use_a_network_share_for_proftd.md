---
title: "Should/could i use a network share for proftd"
date: 2010-04-20
forum: Server Platforms
---

### Post by smay84 on 2010-04-20
Hi

I'm in a strange situation where i have a windows host with a Ubuntu Server VM running Proftpd which needs to be able to ftp files to a shared drive on the host.

This is so the webserver (a separate VM) can access the files in the ftp directory. Also so i can take snapshots of the server without the ftpd files. 

So, my question is how can i do this?  Am i able to mount the share somewhere and use that to store my ftp accounts/files?  Is it possible (or is it a stupid idea) to mount the home directory on the share?

Any pointers in the general direction of a solution would be much appreciated.

---

### Post by smay84 on 2010-04-22
I've managed to mount a windows file share in my media directory.  I now want to be able to move my proftpd root location to there.

Can someone just let me know if i'm wasting my time on this.  I've changed DefaultRoot to /media/storage but when i log in over ftp there is nothing in the folder.  If i try to make a directory it says permission denied.

I think i have a vague idea as to why this isn't working, but could do with some pointers.

In the proftpd log it says:
FTP session open
Preparing to chroot to directory '/media/storage'
USER ftpuser: Login successful

---

