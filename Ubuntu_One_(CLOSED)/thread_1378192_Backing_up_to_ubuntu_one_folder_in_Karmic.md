---
title: "Backing up to ubuntu one folder in Karmic"
date: 2010-01-11
forum: Ubuntu One (CLOSED)
---

### Post by minerbog on 2010-01-11
Hi All,

I have just installed the simple backup program from the repo's. I have targeted this to backup to my Ubuntu one folder. It chugs away backing up stuff and when I check the local Ubuntu one folder with sudo, all files are backed up nicely and every things great.

However, when I check Ubuntu one on line, it has created the folder of the backup but not the files?

Now I'm not sure how the cloud works yet but my theory is that because the backup is created and owned by root, the cloud doesn't like it. Is this the case or am I way off??

Regards.

---

### Post by thebear78 on 2010-01-12
Ubuntu One is probably still reviewing the contents of the folders before it syncs them online. If it is still taking a while, use the support resources like filing a bug chatting with the team on IRC (#ubuntuone on freenode). Here's a link to a complete list of the support resources:
[https://one.ubuntu.com/support/](https://one.ubuntu.com/support/)

---

### Post by redmistpete on 2010-01-12
> **minerbog said:**
> Hi All,

I have just installed the simple backup program from the repo's. I have targeted this to backup to my Ubuntu one folder. It chugs away backing up stuff and when I check the local Ubuntu one folder with sudo, all files are backed up nicely and every things great.

However, when I check Ubuntu one on line, it has created the folder of the backup but not the files?

Now I'm not sure how the cloud works yet but my theory is that because the backup is created and owned by root, the cloud doesn't like it. Is this the case or am I way off??

Regards.

It's my understanding that all files placed in the Ubuntu One folder are moved to a virtual drive (2GB by default), hosted on the internet. All authorised and synced computers can access this drive and access the files. My point being that Ubuntu one can act as a back-up for your files, held on the net and independent of any computer. You shouldn't need to back up the files as the "clouds" aren't really stored on your computer ;) In answer, to back up the actual files to a drive other than the cloud, I would suggest moving the files out of the Ubuntu One folder in case they are just headers for the "Cloud's" files.

---

### Post by minerbog on 2010-01-13
> **redmistpete said:**
> It's my understanding that all files placed in the Ubuntu One folder are moved to a virtual drive (2GB by default), hosted on the internet. All authorised and synced computers can access this drive and access the files. My point being that Ubuntu one can act as a back-up for your files, held on the net and independent of any computer. You shouldn't need to back up the files as the "clouds" aren't really stored on your computer ;) 

Yes I understand this but the reason I was looking at backing up my files to the cloud where these:

1) Not sure on the cloud security so I was going to encrypt the tar ball backup.

2) I was going to backup automatically important files in my home folder that otherwise wouldn't be in the Ubuntu one sync folder.

---

### Post by minerbog on 2010-01-13
Changed my plan. I'm now using encfs and fuse to encrypt a folder to the Ubuntu one folder. This in turn syncs with the cloud.

---

