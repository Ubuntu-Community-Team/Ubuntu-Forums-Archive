---
title: "xen guest hang after upgrade to 12.04"
date: 2012-04-28
forum: Virtualisation
---

### Post by M1chaelk on 2012-04-28
Hi,

After upgrading my xen server and guests (domu) to 12.04  I have a problem with  the guest hanging in "/scripts/init-bottom":
```

Loading, please wait...
[    0.439032] udevd[85]: starting version 175
Begin: Loading essential drivers ... [    0.529304] Console: switching to colour frame buffer device 160x64
[    0.568546] console [tty0] enabled
done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
[    1.262279] EXT4-fs (xvda1): INFO: recovery required on readonly filesystem
[    1.262353] EXT4-fs (xvda1): write access will be enabled during recovery
[    1.293709] EXT4-fs (xvda1): recovery complete
[    1.294895] EXT4-fs (xvda1): mounted filesystem with ordered data mode. Opts: (null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
```Any hints why? Everything worked perfectly fine before the upgrade...

Note: I don't have this problem with the 11.10 guests on the same server...

Thanks in advance

Michael

---

### Post by CharonOfNyx on 2012-05-02
A similar problem (maybe the same) after upgrade LTSP server and client images from 11.10 to 12.04.

If in lts.conf is configured a local printer:
```
[MAC]
PRINTER_0_DEVICE=/dev/lp0 (orPRINTER_0_DEVICE=anythingelse)
```the client with MAC can't boot and it stops after "Begin: Running /scripts/init-bottom ... done."

On server in /var/log/syslog:
```
dhcpd: DHCPDISCOVER from [MAC] via eth0
.....
dhcpd: DHCPACK on 192.168.0.60 to [MAC] via eth0
nbd_server[2071]: connect from 192.168.0.60, assigned file is /opt/ltsp/images/i386.img
nbd_server[2071]: Can't open authorization file (null) (Bad address).
nbd_server[2071]: Authorized client
nbd_server[32636]: Starting to serve
nbd_server[32636]: Size of exported file/device is 687316992
```and stops here without the message "Disconnect request received" as is expected.

If I put in comment PRINTER_0_DEVICE in lts.conf everything is just fine and that terminal boot ok.:confused:
Maybe there is a bug, but I do not know how to report it. Any help will be appreciated.

PS Sorry for my bad stupid english.

---

