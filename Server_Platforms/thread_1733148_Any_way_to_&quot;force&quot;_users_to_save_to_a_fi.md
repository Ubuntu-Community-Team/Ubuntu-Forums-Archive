---
title: "Any way to &quot;force&quot; users to save to a file server?"
date: 2011-04-18
forum: Server Platforms
---

### Post by Learning Linux 2011 on 2011-04-18
Hi, 

If there are users in a network who have desktop Linux (any variety), is there a way to configure their computers to "require" them to save documents to the network?  

Like for example, redirecting their /Home folders to a network file server or not allowing them to save files to their local hard drives?

---

### Post by Aposp on 2011-04-19
i believe you can mount their home directories over the network. basic linux structure :)

---

### Post by varunendra on 2011-04-19
It is possible to mount /home on a network folder using NFS (Network File System). See here: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Specific details on the same page:-

**How to setup NFS Server:** [https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS%20Server](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS%20Server)
[B]
How to setup NFS Client :[/B] [https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS%20Client](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS%20Client)

**Mount at Startup (so that /home could be mounted on NFS) :** [https://help.ubuntu.com/community/SettingUpNFSHowTo#Mount%20at%20startup](https://help.ubuntu.com/community/SettingUpNFSHowTo#Mount%20at%20startup)

However, you may have to fiddle around with the different accounts and their permissions. Try this, and in case of any problems, please post back or start a new thread as suitable. (Please post a link here if you try this and start some new thread for help)

---

