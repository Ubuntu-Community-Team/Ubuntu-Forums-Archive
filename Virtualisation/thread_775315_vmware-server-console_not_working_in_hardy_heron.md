---
title: "vmware-server-console not working in hardy heron"
date: 2008-04-30
forum: Virtualisation
---

### Post by sdahlin on 2008-04-30
Following several posts in the forums I was able to get the vmware and vmware-mui up and running in hardy heron 8.04, but the vmware-server-console refuses to run.  When I attempt to start it nothing comes up and I can find no trace of logs to try to trace the problem.  I am not sure where to turn next.

Thanks,
Steve

---

### Post by gaebriel on 2008-05-02
what version of vmware server are you using?

---

### Post by robfantini on 2008-05-07
Here is how I got it to work.

```
d/l 1.05 version.
tar xf  VMware-server-console-1.0.5-80187.tar.gz
cd vmware-server-console-distrib
sudo ./vmware-install.pl
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware-server-consolelib/libgcc_s.so.1/
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware-server-console/lib/libpng12.so.0/

```

I got this info from :  [http://x86virtualization.com/virtualizationnews/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html](http://x86virtualization.com/virtualizationnews/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html)

---

