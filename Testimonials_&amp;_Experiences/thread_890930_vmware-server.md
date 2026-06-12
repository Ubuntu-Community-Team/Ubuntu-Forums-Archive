---
title: "vmware-server"
date: 2008-08-15
forum: Testimonials &amp; Experiences
---

### Post by decoherence on 2008-08-15
Hoo boy! Was it ever a mistake for me to install VMWare-server from the partners repository! It stopped working one day. I purged it and tried to reinstall

```
sudo apt-get update
...
sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  vmware-server-kernel-modules vmware-server-kernel-modules-2.6.22-14
...
```

Unfortunately,

```
uname -r
2.6.22-15-generic

```

oops! guess having vmware-server in partners didn't work out as planned.... *grumble grumble*

remember, don't mix your "free" with your Free.

(oh, and yeah this is a gutsy machine)

---

