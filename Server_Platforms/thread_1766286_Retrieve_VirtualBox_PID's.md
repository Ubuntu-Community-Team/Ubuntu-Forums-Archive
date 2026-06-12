---
title: "Retrieve VirtualBox PID's"
date: 2011-05-24
forum: Server Platforms
---

### Post by dragos2 on 2011-05-24
Hi all,

I have a setup with VirtualBox 4.0.8 on Ubuntu 8.04 host.

I configured a virtual machine to use 4 processors (out of 8 cores) and I am trying to set
CPU affinity on them but ps is reporting only one VirtualBox procees:
```

user   30810  5.3 19.6 3541996 3238772 ?     Sl   May23  67:20 /usr/lib/virtualbox/VirtualBox --comment vmname --startvm f98b8960-6ac7-4a71-b76f-a42fe88d9bcd --no-startvm-errormsgbox

```and htop utility shows up to 4-6 VirtualBox processes.

Any suggestion on how to retrieve the correct PID for the 4 processes/threads ?

---

