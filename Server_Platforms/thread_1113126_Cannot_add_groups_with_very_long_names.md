---
title: "Cannot add groups with very long names"
date: 2009-04-01
forum: Server Platforms
---

### Post by jonta on 2009-04-01
I tried to add a group in ubuntu 8.04 server with a name that is 40 chars long and  got:

addgroup: `/usr/sbin/groupadd -g 1058 hehehehehehehehehehehehehehehehehehehehe' returned error code 3. Exiting.

Now this was just a testgroup but i am planning on having groups with the same length. What is the max lenght and can you increase it? For a modern OS under 40 chars for a group name seems a bit short.

---

### Post by HermanAB on 2009-04-01
There are many reasons for NOT having very long names.  One is compatibility with other POSIX systems, another is having mercy on the poor sysadmins.

---

### Post by jonta on 2009-04-01
but i am the sysadmin ^^ Should at least be a choice. Perhaps with a --break-compatibility option

---

