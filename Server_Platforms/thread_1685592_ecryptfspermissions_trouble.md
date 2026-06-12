---
title: "ecryptfs/permissions trouble"
date: 2011-02-10
forum: Server Platforms
---

### Post by cherry su on 2011-02-10
Ever since I accidentally rebooted my machine, I haven't been able to mount my encrypted home directory and know exactly the cause. I have this machine set up as my WebDAV file server, and to be able to use my home directory as the directory that is mounted, I set the www-data:www-data as the owner of my home directory (really dumb move, I know). How do I get ecryptfs-mount-private to use my password to authenticate with the keyring and login as another user (www-data) to mount my home directory, if possible? Thanks!

---

### Post by cherry su on 2011-03-09
So looking at /var/log/syslog i see an error that says:

Error attempting to add filename encryption key to user session keyring; rc = [1]

after I attempt to manually mount it as outlined in [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering) Your Data Manually

/var/log/user.log gives the same error message. Any advice?

---

### Post by cherry su on 2011-03-09
Problem solved! This thread helped immensely: [http://ubuntuforums.org/showthread.php?t=1592825&page=2](http://ubuntuforums.org/showthread.php?t=1592825&page=2)

---

