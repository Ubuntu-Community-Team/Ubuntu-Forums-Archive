---
title: "LXC strange ubuntu user provisioning"
date: 2018-02-04
forum: Virtualisation
---

### Post by abic on 2018-02-04
My google-foo is failing me and I can't seem to find documentation that explains what I'm doing wrong :/

I have a number of LXC/LXD containers running on an ubuntu 16.04 server.
I try to script creating new containers with something like the following:

```

#!/bin/bash


set -ex


lxc launch 'ubuntu:16.04' awesomelxc
lxc exec --mode=non-interactive awesomelxc -- groupmod -n awesomegrp ubuntu

```

Running this script gives:

```

+ lxc launch ubuntu:16.04 awesomelxc
Creating awesomelxc
Starting awesomelxc
+ lxc exec --mode=non-interactive awesomelxc -- groupmod -n awesomegrp ubuntu
groupmod: group 'ubuntu' does not exist

```

How ever the group exists after the script finishes and I can run the following:

```

lxc exec --mode=non-interactive awesomelxc -- groupmod -n awesomegrp ubuntu

```

If I do a groupadd instead of groupmod in my script then the awesomelxc group is added, but so is ubuntu, only at the next available GID.

What gives? When are the ubuntu group and ubuntu user provisioned? And why can I not script both the lxc launch and the lxc exec commands in the same script?

---

### Post by abic on 2018-02-04
My bad, I didn't realize that the ubuntu user and group was initialized from cloud-init. Now I have to go figure out how that works...

---

### Post by simosx on 2018-02-13
> **abic said:**
> My bad, I didn't realize that the ubuntu user and group was initialized from cloud-init. Now I have to go figure out how that works...

When the LXD container starts, it takes a few seconds for cloud-init to complete. 
You would just need to wait a bit (a few seconds) before running the rest of your script.

But as you say, if you could use cloud-init yourself in order to make those changes, then it would be the best solution.
Here is how to use cloud-init, 
[https://blog.simos.info/how-to-preconfigure-lxd-containers-with-cloud-init/](https://blog.simos.info/how-to-preconfigure-lxd-containers-with-cloud-init/)

---

