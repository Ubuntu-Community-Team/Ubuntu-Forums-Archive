---
title: "VMWare 2.0.1 on Ibex: bridged networking issue"
date: 2009-06-19
forum: Virtualisation
---

### Post by bucketoftruth on 2009-06-19
If you're having trouble using vmnet0 for bridged networking with VMWare 2.0.1 on Ibex (possibly others) I've found a work-around.  Something that starts after vmware (probably nm-applet) is killing the bridged connection.  Before you start your VM guest, execute
```
sudo /etc/init.d/vmware stop
sudo /etc/init.d/vmware start
```
to restart the vmware services.  Then fire up your VM guest and, viola, bridged networking.

If anyone has any insight into what is knocking out the bridging capabilities prior to restarting vmware, please post a followup.

YMMV

---

