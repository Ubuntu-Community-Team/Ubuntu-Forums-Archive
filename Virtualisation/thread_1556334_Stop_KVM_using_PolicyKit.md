---
title: "Stop KVM using PolicyKit???"
date: 2010-08-19
forum: Virtualisation
---

### Post by J&#7885;hn on 2010-08-19
Hi All

WOW first post!

Anyway I have two servers running KVM, when I attempt to do a live migration I get authentication errors as if libvirtd is trying to use PolicyKit even though I haven't asked it to in the config. This error has only occurred since recently upgrading to Lucid (64bit). Anyone have any clues?

Thanks for any advice or suggestions.

Here are the relevant bits to my configs:

The libvirtd.conf entries:

```

auth_unix_ro = "none"
auth_unix_rw = "none"
unix_sock_group = "libvirtd"

```The syslog error:

```
Aug 19 14:09:10 vm2 libvirtd: 14:09:10.798: error : remoteDispatchAuthPolkit:3379 : Policy kit denied action org.libvirt.unix.manage from pid 1928, uid 1001, result: 256#012
```And the entry I made in PolicyKit.conf just to try and get the thing working:

```
<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
    <match action="org.libvirt.unix.manage">
        <match user="john">
          <return result="yes"/>
        </match>
    </match>
</config>

```

---

### Post by J&#7885;hn on 2010-08-23
Well looks like it's just me then. :D

```
sudo apt-get --purge remove policykit libpolkit-grant2 libpolkit-backend-1-0 policykit-1 qemu-common qemu-kvm libpci3 kvm qemu-common qemu-kvm ubuntu-virt-server
```Reboot

```
sudo apt-get install qemu-common qemu-kvm libpci3 kvm qemu-common qemu-kvm ubuntu-virt-server
```Seems to have done the trick.

---

