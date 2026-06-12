---
title: "2 net interfaces only one shows in ifconfig"
date: 2011-10-21
forum: Server Platforms
---

### Post by prezbedard on 2011-10-21
I have Ubuntu Server 10.04 x64 installed on an HP D180 G6

It has 2 network cards but only 1 shows up in interfaces or when I run ifconfig. When I run lspci | grep Network both are shown. They are exactly the same.

What can I do to properly configure the 2nd to work?

Thanks,

---

### Post by newbie-user on 2011-10-21
You might have to set it up manually in the /etc/network/interfaces file.

---

