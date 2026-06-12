---
title: "Can't use ACL on /var"
date: 2011-07-24
forum: Security
---

### Post by sdlyr8 on 2011-07-24
I'm trying to setup ACL (access control lists) on my /var/www folder so myself and my roommate can work on a site together. I've installed ACL and added the acl option to fstab for the root (/), but whenever I try to setfacl, I still get > setfacl: /var/www: Operation not permitted

I can however share folders in my /home directory so I guess it has to be that /var isn't getting the ACL option.

Here is my fstab file:
> proc            /proc           proc    nodev,noexec,nosuid,acl 0       0
/dev/mapper/franklin-root /               ext4    errors=remount-ro,acl 0       1
/dev/sda1       /boot           ext2    defaults,acl        0       2
/dev/mapper/franklin-swap_1 none  


What am I missing?

---

### Post by bodhi.zazen on 2011-07-24
Did you run that command as root ?

Post the entire command you ran.

---

