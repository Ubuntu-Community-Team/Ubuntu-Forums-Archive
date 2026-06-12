---
title: "Server share , cant access new files"
date: 2009-06-17
forum: Server Platforms
---

### Post by GlebeCS on 2009-06-17
Hi All,

I have a spare drive in my 9.04 server that I have shared, including guest access etc for all users, this is to share pictures etc (home network), initially I found that I could not create any files from a remote machine so in the terminal on the server I ran: sudo chmod -R 777 /media/Backup

I then set rsync from my ubuntu client machine to copy across all my pictures, these are in approx 5 folders, rsync copied the folders and then failed with permission errors to copy any images, I checked the drive and the folders were all accessible by root only.

So back to the server and run sudo chmod -R 777 /media/Backup again.

Running rsync again copied all the images, BUT i then cannot view them from any machine, so yet again sudo chmod -R 777 /media/Backup on the server made them all visible.

The problem is that I do not want to have to CHMOD every time a new image is added (this is regular, as all images from my imac and ubuntu machines are backed up nightly with rsync)

Is there an easy fix for this?

Thanks, Andy

---

### Post by GlebeCS on 2009-06-19
BUMP, nobody have any ideas?

---

### Post by Vegan on 2009-06-19
Have you added a share to your /etc/samba/smb.conf to manage the share? Post the file here so we can take a look.

---

