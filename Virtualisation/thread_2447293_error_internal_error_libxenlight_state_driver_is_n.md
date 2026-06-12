---
title: "error: internal error: libxenlight state driver is not active"
date: 2020-07-16
forum: Virtualisation
---

### Post by marietto2008 on 2020-07-16
Hello.

I'm trying to create a new xen connection with virt-manager. At the beginning it didn't work because this error : "failed to connect socket to '/var/run/libvirt/-virtxend-sock. file or directory not found" ; but then I followed the @Christian Ehrhardt suggestion on this thread :

[https://askubuntu.com/questions/1259086/socket-to-var-run-libvirt-virtxend-sock-file-o-directory-not-found]("https://askubuntu.com/questions/1259086/socket-to-var-run-libvirt-virtxend-sock-file-o-directory-not-found")

and the first error is gone,but now there is another error : "libxenlight state driver is not active",as u can see below :

```
root@ziomario-I9:/etc/xen# apt install libvirt-daemon-driver-xen qemu-system-x86-xen

root@ziomario-I9:/etc/xen# sudo systemctl restart libvirtd

root@ziomario-I9:/etc/xen# systemctl status libvirtd

root@ziomario-I9:/etc/xen# systemctl status libvirtd
&#9679; libvirtd.service - Virtualization daemon
     Loaded: loaded (/lib/systemd/system/libvirtd.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2020-07-16 13:02:06 CEST; 1h 25min ago
TriggeredBy: &#9679; libvirtd-admin.socket
             &#9679; libvirtd-ro.socket
             &#9679; libvirtd.socket
       Docs: man:libvirtd(8)
             https://libvirt.org
   Main PID: 2399 (libvirtd)
      Tasks: 17 (limit: 32768)
     Memory: 43.5M
     CGroup: /system.slice/libvirtd.service
             &#9492;&#9472;2399 /usr/sbin/libvirtd

lug 16 13:17:06 ziomario-I9 libvirtd[2399]: Unable to open /dev/kvm: File o directory non esistente
lug 16 13:17:06 ziomario-I9 libvirtd[2399]: internal error: Cannot find suitable CPU model for given data
lug 16 13:17:06 ziomario-I9 libvirtd[2399]: Unable to open /dev/kvm: File o directory non esistente
lug 16 13:17:06 ziomario-I9 libvirtd[2399]: operation failed: pool 'default' already exists with uuid 4794da80-c4ef-43a5-aee5>
lug 16 13:17:30 ziomario-I9 libvirtd[2399]: internal error: libxenlight state driver is not active
lug 16 13:17:30 ziomario-I9 libvirtd[2399]: End of file while reading data: Errore di input/output
lug 16 14:10:48 ziomario-I9 libvirtd[2399]: internal error: libxenlight state driver is not active
lug 16 14:10:48 ziomario-I9 libvirtd[2399]: End of file while reading data: Errore di input/output
lug 16 14:20:40 ziomario-I9 libvirtd[2399]: internal error: libxenlight state driver is not active
lug 16 14:20:40 ziomario-I9 libvirtd[2399]: End of file while reading data: Errore di input/output

```

```
root@ziomario-I9:/home/ziomario# virsh -c xen:///
error: failed to connect to the hypervisor
error: internal error: libxenlight state driver is not active

root@ziomario-I9:/home/ziomario# virsh  version
Compiled against library: libvirt 6.0.0
Using library: libvirt 6.0.0
Using API: QEMU 6.0.0
Running hypervisor: QEMU 4.2.0

```

LOG gathered this armor denials,but they appeared before to create the xen domain :

```
root@ziomario-I9:/home/ziomario# dmesg -w | grep apparmor

[    5.887830] evm: security.apparmor
[   31.653223] audit: type=1400 audit(1594897201.258:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=665 comm="apparmor_parser"
[   31.702186] audit: type=1400 audit(1594897201.306:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=672 comm="apparmor_parser"
[   31.802911] audit: type=1400 audit(1594897201.406:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=671 comm="apparmor_parser"
[   31.823300] audit: type=1400 audit(1594897201.430:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/ipsec/stroke" pid=663 comm="apparmor_parser"
[   31.953066] audit: type=1400 audit(1594897201.558:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=669 comm="apparmor_parser"
[   31.953076] audit: type=1400 audit(1594897201.558:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=669 comm="apparmor_parser"
[   31.966592] audit: type=1400 audit(1594897201.570:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=660 comm="apparmor_parser"
[   31.966601] audit: type=1400 audit(1594897201.570:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=660 comm="apparmor_parser"
[   31.966607] audit: type=1400 audit(1594897201.570:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=660 comm="apparmor_parser"
[   31.975582] audit: type=1400 audit(1594897201.582:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lsb_release" pid=664 comm="apparmor_parser"
[   48.715193] audit: type=1400 audit(1594897218.322:59): apparmor="DENIED" operation="open" profile="/{,usr/}sbin/dhclient" name="/proc/1733/task/1734/comm" pid=1733 comm="dhclient" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   48.715835] audit: type=1400 audit(1594897218.322:60): apparmor="DENIED" operation="open" profile="/{,usr/}sbin/dhclient" name="/proc/1733/task/1735/comm" pid=1733 comm="dhclient" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   48.716222] audit: type=1400 audit(1594897218.322:61): apparmor="DENIED" operation="open" profile="/{,usr/}sbin/dhclient" name="/proc/1733/task/1736/comm" pid=1733 comm="dhclient" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[  137.782108] audit: type=1400 audit(1594897307.641:62): apparmor="DENIED" operation="capable" profile="/usr/sbin/cups-browsed" pid=2396 comm="cups-browsed" capability=23  capname="sys_nice"
[  183.363064] audit: type=1400 audit(1594897353.229:63): apparmor="STATUS" operation="profile_load" profile="unconfined" name="docker-default" pid=3461 comm="apparmor_parser"
```

It does not seems that the guest produced armor denials,but anyway,it still does not work.

---

