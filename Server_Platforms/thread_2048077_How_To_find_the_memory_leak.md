---
title: "How To find the memory leak?"
date: 2012-08-26
forum: Server Platforms
---

### Post by THPubs on 2012-08-26
Im preparing a web-server and have already installed Wordpress on it. Everything worked fine. But instantly, the memory usage went up. Now I only have 300MB of memory free. To check the problem, I disabled some services like php, nginx, fail2ban, psad and mysql. It reduced the memory usage by a small amount but still its too high.

Then I restarted the machine and started working again. Again after some time, the memory usage shot up! How can I locate the exact problem? What might be causing this issue?

PS : Its an Ubuntu

PS : It looks like the swap is not yet used. Swap usage : 0 (The server is a virtual machine (KVM))

---

### Post by Bachstelze on 2012-08-26
How are you checking the amount of free memory?

---

### Post by THPubs on 2012-08-26
> **Bachstelze said:**
> How are you checking the amount of free memory?

The output of free -m

             total       used       free     shared    buffers     cached
Mem:          2003       1764        238          0         43       1350
-/+ buffers/cache:        370       1633
Swap:         2043          0       2043

---

### Post by Bachstelze on 2012-08-26
Read this: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by THPubs on 2012-08-26
> **Bachstelze said:**
> Read this: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Thanks a lot for the explanation :)

---

