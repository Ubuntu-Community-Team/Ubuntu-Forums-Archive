---
title: "EMC CX4 storage, cluster and 9 ubuntu servers"
date: 2010-05-14
forum: Server Platforms
---

### Post by miszko on 2010-05-14
I'm new and I want to say hello ;)

Sorry for my English, it's not my mother language ;)

Here what I have got:
- 9x dell servers with 2 x FibreChannel ports
- 1x EMC CX4 storage (24 TB free space)

Servers are runing on Ubuntu Server Edition 9.1.

9 servers are connected via FC ports to storage.
Each server can see the same partition on storage (can write and read). But when I save file from server1 the rest of servers can't see this file or if they see, cant read (I/O error) and vice versa. 

Easier: If I'm operating from one server on storage, I can write and read, but when I want to access to this file from other server I can't.

The solutions is make cluster with cluster file systems (example OCFS2 or GFS2 are cluster's FS.). But I can't find any good solutions how to configure servers. 

Any ideas or links to good how-to's?

Thanks for any help!

---

### Post by emcserver on 2010-11-13
We can help you about EMC If you are troubling you can visit our site for help we have all info about EMC you can also read blogs at our site.
[EMC CX]("http://serversrefurbished.com/")

---

