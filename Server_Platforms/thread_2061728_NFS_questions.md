---
title: "NFS questions"
date: 2012-09-23
forum: Server Platforms
---

### Post by SeaKing on 2012-09-23
Hey,

I’m new to NFS and I used the [Ubuntu help page to set one up]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). I just took the "basic" options without any optional things. Now I read some sites and I found out, that I can improve the security by using idmapd (?). In order to use it, the user on the server needs to have the same uid and gid as on the client which I also need to specify in the mount option. (Right so far?)
Now the question is, I also want to use PXE later on, but than there is no real user available to identify on the server, or is it possible to use the uid/gid authentication for specific exports?

---

