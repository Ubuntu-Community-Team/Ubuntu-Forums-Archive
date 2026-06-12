---
title: "deploying microstack on a server with an ovs bridge configured (sunbeam)"
date: 2024-01-22
forum: Ubuntu Cloud and Juju
---

### Post by scttstrck on 2024-01-22
I've been looking into Sunbeam / Microstack for a while now.
I recently wanted to deploy it on physical machines where I configured the networking to go over an ovs bridge.
In the end it would always timeout at (30/31) while deploying openstack, as neutron would error out.
Does anyone know how I can look into the log of the failed neutron instance?
I'd like to see if I can make some small changes to get it working, as I could then show it off on my demo lab.

---

### Post by scttstrck on 2024-01-22
I got the answer elsewhere thanks to a helpfull soul.

[COLOR=#D51928][FONT=Inconsolata]kubectl logs -n openstack --container neutron-server neutron-0[/FONT][/COLOR]

---

