---
title: "Microstack with 22.04.2 on VirtualBox with nested pages enabled?"
date: 2023-07-16
forum: Ubuntu Cloud and Juju
---

### Post by atod2 on 2023-07-16
Has anyone followed the official instructions at:

[https://ubuntu.com/openstack/install](https://ubuntu.com/openstack/install)

and has a successful installation?

I'm using VB 7.0.8 and am noting hangs during the step to Bootstrap the cloud:

> sunbeam cluster bootstrap --accept-defaults

Specifically "Deploying OpenStack Control Plane to Kubernetes".

I had to abort the script.  I also note, that I did not run this step as sudo root.

I try to re-run the above bootstrap and receive:
>  db_root: cannot open: /etc/target 

Finally I get the response:

>  Node has been bootstrapped with roles: control, compute 





I'm wondering if this is a problem with the installation scripts, version mismatch or VirtualBox itself.  I allocated 16GB RAM and 4 CPUs to the Ubuntu VM.

Thanks

---

