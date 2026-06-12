---
title: "pxebooting server with sriov enabled ports"
date: 2014-12-30
forum: Server Platforms
---

### Post by Akilesh on 2014-12-30
I am trying to setup pxeboot with kickstart for a few servers. I have done this many times before and am pretty sure of the procedure. This time around I have a strange problem. The boot halts with the message 'random: nonblocking pool is initialized' It stays there for a long time and then proceeds. 

I recognized that I started having this issue after adding sriov enabled nic to the server. Can anyone explain what is happening on the system and how I can avoid the long wait.

---

### Post by Akilesh on 2014-12-31
Guys anyone can at least point me in the right direction? The server gets dhcp address, the pxe files are recieved over tftp, the kickstart file is downloaded, The Release file is downloaded and then it stops.

---

