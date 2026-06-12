---
title: "Perform an action before a service starts and after a service stops"
date: 2010-09-10
forum: Server Platforms
---

### Post by bigcat400 on 2010-09-10
Hi Folks,

I am running Server 10. I have a requirement to perform an action before the MySQL service starts, and perform another action after MySQL service stops.

I found the init script for MySQL under /etc/init/mysql.conf. I added my thing to the pre-start script there and works fine.

I am having trouble finding the script that stops the server so I can modify. I've searched all over the place and I can't figure it out.

I appreciate any info on this or suggestion as to how to do this differently.

Thanks

---

### Post by bigcat400 on 2010-09-10
> **bigcat400 said:**
> Hi Folks,

I am running Server 10. I have a requirement to perform an action before the MySQL service starts, and perform another action after MySQL service stops.

I found the init script for MySQL under /etc/init/mysql.conf. I added my thing to the pre-start script there and works fine.

I am having trouble finding the script that stops the server so I can modify. I've searched all over the place and I can't figure it out.

I appreciate any info on this or suggestion as to how to do this differently.

Thanks

never mind, just realized there is post-stop script, it just wasn't present in the mysql init file .

---

