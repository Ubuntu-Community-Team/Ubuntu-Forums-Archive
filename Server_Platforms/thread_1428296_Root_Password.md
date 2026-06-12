---
title: "Root Password"
date: 2010-03-12
forum: Server Platforms
---

### Post by kfd on 2010-03-12
Hi
Can someone please help me.
Can you tell me how to find thte root password on Server 9.1

Thanks
Kevin

---

### Post by sisco311 on 2010-03-12
By default, the root account password is locked. Use sudo:
[uhelp]community/RootSudo[/uhelp]

---

### Post by cdenley on 2010-03-12
There is no root password unless you set one. Either way, you cannot recover the password (within a reasonable amount of time if it is reasonably strong), you can only reset it.

---

