---
title: "Recovering ecryptfs data"
date: 2018-05-12
forum: Security
---

### Post by Quarkrad on 2018-05-12
Scenario.  I have **/home** ecrypted and know the password - using rysnc have backed up **/home** to another hd (I'm using the default ecryptfs).  PC is now stolen and a new one is rebuilt with a clean version of ubuntu 16.04.  I have seen lots of methods using live CD but I do not have original pc (it is stolen) - but I do have the backup of **/home** on my HD.  How do I decrypt **/home** on my HD so I can transfer it to my new pc?  (note.  backup HD is in another ubuntu machine - in this scenario assume not using anything like ssh to transfer original rsync backup - lets say it was done manually).

---

### Post by TheFu on 2018-05-12
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Automatically](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Automatically) should be helpful.

The use of ssh or not doesn't matter. rsync pushes bytes around and doesn't modify those bytes along the way.

---

