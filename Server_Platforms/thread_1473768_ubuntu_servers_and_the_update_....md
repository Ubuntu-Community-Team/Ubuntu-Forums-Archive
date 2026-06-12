---
title: "ubuntu servers and the update ..."
date: 2010-05-05
forum: Server Platforms
---

### Post by fahd on 2010-05-05
Hi folks ...

I would like to know how to update the current ubuntu server 10.04 kernel ver. to the new one. I just gave the following commands:

sudo apt-get update
sudo apt-get upgrade

A lot of things were updated except the kernel. Any clue. Thanks in advance.

Fahd
100505

---

### Post by koenn on 2010-05-05
you shouldn't try to upgrade with apt-get, use update-manager-core

-> [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)


Since you are already half-upgraded, that might not work; in that case 
```
sudo apt-get dist-upgrade
``` might get you through, 
or you may need to manually install the kernel you want/need
```

# get a list
apt-cache search linux-image

#pick one and install it: (example)
sudo apt-get install linux-image-2.6.24-18-generic

```
note that this is NOT the recommended upgrade procedure.
Also, it may be useful to run apt-get upgrade or dist-upgrade again after you installed the new kernel, in case the newer kernel version makes some packages upgradeable again.

---

### Post by fahd on 2010-05-05
Thank you for rendering a help.

Fahd
100505

---

