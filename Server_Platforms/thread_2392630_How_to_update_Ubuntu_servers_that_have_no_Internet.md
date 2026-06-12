---
title: "How to update Ubuntu servers that have no Internet access"
date: 2018-05-23
forum: Server Platforms
---

### Post by gutterpunk77 on 2018-05-23
Hi there,

I am very new to Ubuntu and have been given 9x Ubuntu 14.04 VM servers that need updating to latest levels (I have not built these myself). I currently patch a number of Windows servers but have now had these added to my workload. These servers do not have any internet access and so I need to know if anyone can help by explaining how I can update these servers.

Many thanks

---

### Post by howefield on 2018-05-23
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by LHammonds on 2018-05-23
Does the underlying host for these VMs have access to the Internet?  In other words, are these servers just being denied access or are they not capable of accessing the Intenet-based repositories?

If you can get them temporary access, it would be easiest do apply patches that way.  Otherwise you will need to setup a repository server that does have access and then move it where the VMs can access them.  I have not configured a local repository so I'm not well-versed in the steps but I do know it is possible to host your own local repository.

LHammonds

---

### Post by rsteinmetz70112 on 2018-05-23
Just a note. 14.04 LTS is still supported but support will end around April on next year. You should probably be planning on updating those servers to a newer release sometime before then.

---

### Post by TheFu on 2018-05-23
[http://manpages.ubuntu.com/manpages/artful/man8/apt-offline.8.html](http://manpages.ubuntu.com/manpages/artful/man8/apt-offline.8.html) - apt-offline.  There is a bit of a chick-egg problem, however.

---

### Post by gutterpunk77 on 2018-05-29
Thanks for your replies everyone.

---

