---
title: "Unable to resolve localhost??"
date: 2011-06-26
forum: Server Platforms
---

### Post by scott_tiger on 2011-06-26
**sudo: unable to resolve host localhost.localdomain**

I have installed apache2 web server

When I am using **sudo vi *filename*** I am getting the above error.

Also when I am using **localhost/folder_name/filename.php** **I am not ****able to connect to resource I am looking for**, but when I am  using
**127.0.0.1/folder_name/filename.php** I am **getting** the required web page of my project...

Please help???

---

### Post by papibe on 2011-06-26
Could you post these files? 

```
/etc/hosts
/etc/nsswitch.conf
```

Regards.

---

### Post by scott_tiger on 2011-07-01
the problem still persists..
/etc/hosts
/etc/nsswitch.conf files are not present in my /etc folder..

---

### Post by kamaji792 on 2011-07-01
> **scott_tiger said:**
> the problem still persists..
/etc/hosts
/etc/nsswitch.conf files are not present in my /etc folder..

So that may be the problem:

I'm running **10.04 Lts - desktop**,
My **/etc/hosts** file was:
```
127.0.0.1   localhost
127.0.1.1   host-name

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Change **host-name** to your hostname.

My **/etc/nsswitch.conf** file is:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

Permissions are:
```
-rw-r--r-- 1 root root 318 2011-06-08 16:36 /etc/hosts
-rw-r--r-- 1 root root 518 2010-01-31 15:57 /etc/nsswitch.conf
```

Hope that helps K

---

