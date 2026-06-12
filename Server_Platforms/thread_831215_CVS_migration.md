---
title: "CVS migration"
date: 2008-06-16
forum: Server Platforms
---

### Post by elektro_komesar on 2008-06-16
Can anyone help me with CVS migration from windows to Ubuntu server? (meaning, I already have users and projects in windows CVS and I have to migrate them to Ubuntu server)
Guidance, step by step...
1. Install cvs (sudo apt-get install cvs)
2. Install cvsserver cvsd (sudo apt-apt install cvsd)
3. Build root (sudo cvsd-buildroot /home/user/cvs)
4. create cvs root (sudo mkdir cvsroot)
5. initialize repository (sudo cvs -d /home/user/cvs/cvsroot init
sudo chown -R cvs:cvs cvsroot)
6. create user/password (sudo cvs-passwd /home/user/cvs/cvsroot +myusername)
7. change the AUTH type (sudo vi /var/lib/cvsd/cvsroot/CVSROOT/config)

I deliberately use /home/user/cvs path...because I didn`t want to use /var/lib/cvsd/.

However..
I have followed all this steps...also I put some documents in repository...and everything is ok when I try to checkout certain document as root user...but when I try with local user (created in step 5) I receive message that I have no access rights. I try to checkout from terminal, from TortoiseCVS (server can be accessed from internet) and same thing...how can I access it using credentials I create in step 6???
So, if someone has experience with migration, it would be nice to describe here...step by step...in detail.
thanks

---

