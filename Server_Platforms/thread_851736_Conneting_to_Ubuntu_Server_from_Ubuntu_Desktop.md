---
title: "Conneting to Ubuntu Server from Ubuntu Desktop"
date: 2008-07-07
forum: Server Platforms
---

### Post by degi76 on 2008-07-07
Hello all.
I am new to Linux and trying to set-up a "simple" linux home network. However, I seem to be running into a few issues.

I have three pcs at the moment. I installed ubuntu server on one of my pcs (and set up four user accounts on this server for family, as well as in Samba). I also have a shared folder for all family members to use.

I am using the other two pcs as "workstation" pcs. One has windows xp on it, the other ubuntu desktop linux. 

On the windows xp workstation pc, while logged in as myself, I am able to go into Network Neighborhood and see all the user folders (in the home directory) I had created on the server, but I am not able to access any of them (not even my own). I can, however, access the shared folder.

On my linux desktop workstation pc, I can't see any of the folders.

My questions:

1) How do I set-up my ubuntu linux desktop pc to access my ubuntu server?  

2) How to I access these files on my Windows XP dsktop?

Thanks again all.

---

### Post by windependence on 2008-07-07
sudo apt-get install samba


-Tim

---

### Post by degi76 on 2008-07-07
> **windependence said:**
> sudo apt-get install samba


-Tim


Thanks Tim.
Installed Samba on my ubuntu workstation pc as well. Does this  pc need any specific config so as to access my server (installing samba does not seem to have helped)? 

Thanks

---

### Post by windependence on 2008-07-07
You'll need to have the same users with the same passwords on your Windoze boxes and your Linux box. Also, you need to add Samba users on the linux box. Again, keep them in sync. There is an option to automatically sync your Linux users and SAMBA users but I forget how I did it. If you google it, there are lots of articles on it. You may also wish to configure some of the cool samba options available. All the configuration is kept in a plain text file.

-Tim

---

