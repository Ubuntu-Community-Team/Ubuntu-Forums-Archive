---
title: "Dropbox Folder"
date: 2018-11-30
forum: Server Platforms
---

### Post by bujums on 2018-11-30
I have Ubuntu Server 18.04 with Dropbox Business on it.  My Dropbox folders are of course located in the users home file  but my data for Dropbox is not located there as I have it on a raid array so I have symlinks in the Dropbox folder.  I also have samba install and sharing those same files.  This is not ideal for Dropbox. they don't like the symlinks and they don't like shared on the network files.  This situation is messing the Shared Files permissions.  I want to try a few things anyway and see if I can get it to work.  (Dropbox used to work fine on my CentOS 6 system with almost the same set up but we did not have the Business we just had a single user.

Question.  
   Would it be better to move the location of the Home file over the the Raid array, so it would look like this [ shares/home/user/ ] instead of [ /home/user/ ]  or can I just move the Dropbox folders to the [ /shares/ ] and then place the data in the the Dropbox folder?  I would of course have to modify the Dropbox config file to point to the new location.

Thanks
     Leslie

---

### Post by bujums on 2018-11-30
I have Ubuntu Server 18.04 with Dropbox Business on it.  My Dropbox folders are of course located in the users home file  but my data for Dropbox is not located there as I have it on a raid array so I have symlinks in the Dropbox folder.  I also have samba install and sharing those same files.  This is not ideal for Dropbox. they don't like the symlinks and they don't like shared on the network files.  This situation is messing the Shared Files permissions.  I want to try a few things anyway and see if I can get it to work.  (Dropbox used to work fine on my CentOS 6 system with almost the same set up but we did not have the Business we just had a single user.

Question.  
   Would it be better to move the location of the Home file over the the Raid array, so it would look like this [ /shares/home/user/ ] instead of [ /home/user/ ]  or can I just move the Dropbox folders to the [ /shares/ ] and then place the data in the the Dropbox folder?  I would of course have to modify the Dropbox config file to point to the new location.

Thanks
     Leslie

---

### Post by oldfred on 2018-11-30
Merged duplicate threads, do not create duplicates as we are volunteers and need to know what is posted to avoid duplicate or confusing instructions.

---

