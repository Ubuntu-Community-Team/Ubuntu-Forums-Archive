---
title: "Xen migrate failure"
date: 2009-10-22
forum: Virtualisation
---

### Post by kameleon25 on 2009-10-22
I have 2 xen systems setup. Both are running ubuntu 8.04 server. One is 32-bit (SERVER1) and the other is 64-bit (SERVER2). Both are on a local gigabit network. I have 3 VM's I need to migrate over off of SERVER1 on to SERVER2. I have ISCSI setup and both machines are connected to the drives. I have also setup the needed migration parts in the /etc/xen/xend-config.sxp on both servers.

I am able to "migrate" from/to the same machine without failure. When I try to migrate to the other machine it fails with the error:

```
root@virtual:~# xm migrate --live 3 sienna
Error: /usr/lib/xen/bin/xc_save 4 3 0 0 1 failed
Usage: xm migrate <Domain> <Host>

Migrate a domain to another machine.

Options:

-h, --help           Print this help.
-l, --live           Use live migration.
-p=portnum, --port=portnum
                     Use specified port for migration.
-n=nodenum, --node=nodenum
                     Use specified NUMA node on target.
-s, --ssl            Use ssl connection for migration.

root@virtual:~#
```

where 3 is the VM ID that is listed when I do an `xm list` and sienna is the machine it is going to.

I have tried migrating to localhost also and it appears to work:

```
root@virtual:~#xm list 
Name                                        ID   Mem VCPUs      State   Time(s)
Domain-0                                     0  4737     2     r-----  40349.4
highlander                                   8   768     1     -b----    793.7
pbx                                          3   512     1     -b----  13597.7
tundra                                       6  1024     1     -b----  22172.6

root@virtual:~# xm migrate --live 3 localhost
root@virtual:~# xm list
Name                                        ID   Mem VCPUs      State   Time(s)
Domain-0                                     0  4737     2     r-----  40355.2
highlander                                   8   768     1     -b----    796.6
pbx                                          9   512     1     -b----      0.0
tundra                                       6  1024     1     -b----  22174.0
root@virtual:~#
```

I have googled for this error to no avail. I need to migrate the machines so I can take the original server down and reinstall. Any assistance is greatly appreciated.

---

