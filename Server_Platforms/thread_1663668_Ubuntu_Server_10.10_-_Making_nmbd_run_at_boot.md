---
title: "Ubuntu Server 10.10 - Making nmbd run at boot"
date: 2011-01-09
forum: Server Platforms
---

### Post by TheTFo on 2011-01-09
Hello,

I cannot, for the life of me, get nmbd to run at boot on Ubuntu Server 10.10.  On all other variations I've run, it's just automatically running.  Total noob here, but how does one go about this?

---

### Post by TheTFo on 2011-01-10
Found my solution shortly after posting, it seems to be an issue in samba distributed on the CD.  So I did:

sudo apt-get remove samba
sudo apt-get remove samba-common-bin
sudo apt-get install samba

And everything worked OK.  Read about it through a bug report.

---

### Post by sj1410 on 2011-01-10
Great!!!

Thanks for posting. your answer would help others.

---

