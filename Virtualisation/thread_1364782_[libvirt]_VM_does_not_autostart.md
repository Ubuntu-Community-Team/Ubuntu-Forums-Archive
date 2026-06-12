---
title: "[libvirt] VM does not autostart"
date: 2009-12-26
forum: Virtualisation
---

### Post by Quetschke on 2009-12-26
Hello guys,


I am using libvirt/virsh to manage my KVM domains.

I have set up autostart for domain 'bob' by:
```
manager@charlie:~$ virsh autostart bob
Connecting to uri: qemu:///system
Domain bob als automatisch zu starten markiert
```

The symlink has been created successfully:```
manager@charlie:~$ ls -lah /etc/libvirt/qemu/autostart/
insgesamt 8,0K
drwxr-xr-x 2 root root 4,0K 2009-12-26 14:32 .
drwxr-xr-x 4 root root 4,0K 2009-12-26 14:54 ..
lrwxrwxrwx 1 root root   25 2009-12-26 14:32 bob.xml -> /etc/libvirt/qemu/bob.xml
```

But the domain isn't auto-started on boot although libvirtd is running.

Are there any ideas how to solve this?

Thanks in advance.

Tobias


P.S. The autostart of networks is working very well:
```
manager@charlie:~$ virsh net-list
Connecting to uri: qemu:///system
Name                 Status     Automatischer Start
-----------------------------------------
default              Aktiv      yes
```


P.P.S. 'bob' is running without problems when it is started manually:
```
manager@charlie:~$ virsh list
Connecting to uri: qemu:///system
 Id Name                 Status
----------------------------------
  2 bob                  laufend
```

---

### Post by HeikoH on 2010-01-07
I have the same issue with Ubuntu 9.10.
I've also filed a bug report, please check it out and if the issue seems similar to yours respond that you're also having the issue. Perhaps that will draw some attention from the developers (the bug is still marked NEW while I've filed it about a month ago).

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/495394](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/495394)

---

### Post by leechguy on 2010-07-24
I had the same issue in Ubuntu 10.04. I have created a bridge device myself with a static ip address. The problem is that the libvirt upstart script doesn't wait for the bridge to be up before starting libvirtd.

My bridge is called br0 and I have updated the /etc/init/libvirt-bin.conf upstart script so that it waits for the bridge to be up:

Old start line (not waiting for the bridge):

[FONT=Courier New]start on runlevel [2345][/FONT]

New start line (waiting for the bridge):

[FONT=Courier New]start on (runlevel [2345] and net-device-up IFACE=br0)[/FONT]

Hope this helps.

---

