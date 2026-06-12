---
title: "Connect to server?"
date: 2010-01-02
forum: Server Platforms
---

### Post by dinuzz on 2010-01-02
Hey there
What is the best option to connect ubuntu desktop to my ubuntu server? I have samba running on it to make my windows notebooks connect to it. But I also heard of WEBDAV, is that an option?
- what is the common practice to connect ubuntu desktops to the server so users can store their personal files on it? I have each username also available on the server and home directories are created for each single user on the network.
thanks - cheers

---

### Post by Gourgi on 2010-01-02
if you already have samba running then your ubuntu users can connect to the server using samba shares as well.
they can also use sshfs to connect or ftp or even webdav but samba is the most logical option to me since it is already running

---

