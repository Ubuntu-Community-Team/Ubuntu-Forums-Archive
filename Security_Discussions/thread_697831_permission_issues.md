---
title: "permission issues"
date: 2008-02-15
forum: Security Discussions
---

### Post by jonette20 on 2008-02-15
Hi,

Hoping someone can help me.  Have asked at other forums, but no answers yet.

I am new to Linux and currently running Ubuntu 7.04.
Installed Squid back in Oct and have had no problems until a couple of days ago i tried to edit my squid.conf to add a website and it tells me
"Operation not permitted"

When I do a ls -l squid.conf the output is showing rwx across the board.
When I do a right click - properties - permission, it shows owner root, group root, and other all have read & write permissions.

However, it will not allow me to edit the file, even logged on as root.

I have always added websites to this file and have not changed anything.

What could have happened?  Where do I start to troubleshoot?

Thanks in advance for any help
jonette20

---

### Post by k_grdn on 2008-02-15
Hi,

Try lsattr squid.conf to see if any of the extended attributes are set.

Do you have apparmor or selinux installed?

Regards,

k_grdn

---

### Post by jonette20 on 2008-02-19
Hi,
Here is the output of lsattr squid.conf.


brewer@SERVG10:/etc/squid$ lsattr squid.conf
----i------------- squid.conf
brewer@SERVG10:/etc/squid$ 


Does this tell you anything?
After doing a man on lsattr and chattr I understand that the i means it cannot be edited at all unless by superuser or process with
CAP_LINUX_IMMUTABLE.
Wouldn't root be superuser?  
Cant anyone tell me how to change this attribute.
jonette20

---

### Post by jonette20 on 2008-02-19
Hi,

Thanks K_grdn.  Getting that information lead me to chattr.  Someone had suggested that I try chattr -i /etc/squid/squid.conf and that got rid of the i that I saw when I did the lsattr squid.conf that u suggested.

I am now able to edit file.

Thanks again

---

