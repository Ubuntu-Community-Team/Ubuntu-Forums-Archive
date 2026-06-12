---
title: "Google Drive Sync on Ubuntu Server"
date: 2016-07-15
forum: Server Platforms
---

### Post by alka5eltzer on 2016-07-15
Hi All,

I'm running Ubuntu Server 12.04.1 as a Fileserver in an Office. I admin it via Webmin and SSH - there is no desktop installed.

On my own  Workstation Desktop, I'm using Ubuntu 16.04 and I use overGrive to sync to my Google Drive for work account (We're a Google Apps for work customer). This works pretty well.

Does anyone know a good way to sync the Fileserver (about 40Gb of files) to a Google apps Drive account - so users can access the Files via Google Drive on web or internally on the office network. This will also be a real time Backup. My directors also want to move away from the Physical Fileserver to the Cloud... so they'r hoping this will ease the transition.

Thanks in advance

---

### Post by howefield on 2016-07-15
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by volkswagner on 2016-07-16
According to [this tutoria]("http://www.howtogeek.com/130380/how-to-use-google-drive-on-linux-2-unofficial-solutions/")l Grive runs from the command line.

Have you tried running it directly on the server?

Although not open source Insync can do more than Grive.

---

