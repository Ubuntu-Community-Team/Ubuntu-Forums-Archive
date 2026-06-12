---
title: "Latest proposed errors"
date: 2019-04-30
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-04-30
E: libnewt0.52: 33.3333:installed libnewt0.52:amd64 package post-installation script subprocess returned error exit status 2 
( No file name for libnewt0.52:amd64)

E: whiptail: dependency problems - leaving unconfigured (No file name for whiptail:amd64)

---

### Post by harry332 on 2019-04-30
Right, the newt_0.52.20-8ubuntu1 ( [https://launchpad.net/ubuntu/+source/newt/0.52.20-8ubuntu1](https://launchpad.net/ubuntu/+source/newt/0.52.20-8ubuntu1) ) was bad. It was impossible to install and it damaged the setup if installed in a way that not even the new fixed version of newt_0.52.20-8ubuntu2 ( [https://launchpad.net/ubuntu/+source/newt/0.52.20-8ubuntu2](https://launchpad.net/ubuntu/+source/newt/0.52.20-8ubuntu2) ) could be installed properly.

The only way to solve this is as follows (in case the bad version was installed):
- download network-manager ( [https://launchpad.net/ubuntu/+source/network-manager/1.16.0-0ubuntu2](https://launchpad.net/ubuntu/+source/network-manager/1.16.0-0ubuntu2) ) to be later installed manually if needed
- purge newt (libnewt0.52, whiptail) with the network-manager and friendly recovery
- reinstall the fixed newt (libnewt0.52, whiptail) and network-manager + friendly recovery

I tried this and it works.

---

### Post by dino99 on 2019-04-30
First time i'm seeing such an issue: even can't purge that libnewt0.52 package, either via synaptic or terminal: get an error script 1 code.

Solution found to bypass that lock: edit '/var/lib/dpkg/status' , find and purge the whole libnewt0.52 block, save; then reconfiguring was possible.
Now that issue is solved.

Thanks Harry for the help.

---

