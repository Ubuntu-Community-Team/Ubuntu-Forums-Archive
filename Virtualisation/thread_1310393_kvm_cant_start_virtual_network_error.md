---
title: "kvm cant start virtual network error?"
date: 2009-11-01
forum: Virtualisation
---

### Post by sdowney717 on 2009-11-01
just building a machine in kvm and the network seems to be a problem

> Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 1303, in validate_final_page
    net.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 620, in create
    if ret == -1: raise libvirtError ('virNetworkCreate() failed', net=self)
libvirtError: internal error 'dnsmasq --strict-order --bind-interfaces --pid-file=/var/run/libvirt/network/default.pid --conf-file=  --listen-address 192.168.122.1 --except-interface lo --dhcp-range 192.168.122.2,192.168.122.254' exited with non-zero status 2 and signal 0: 
dnsmasq: failed to bind listening socket for 192.168.122.1: Address already in use


address in use where, i dont get it.
> scott@scott-desktop:~$ ping 192.168.122.1
PING 192.168.122.1 (192.168.122.1) 56(84) bytes of data.
^C
--- 192.168.122.1 ping statistics ---
17 packets transmitted, 0 received, 100% packet loss, time 16126ms

scott@scott-desktop:~$ 



---

### Post by rod40cool on 2010-03-08
Hey I'm having the exact same issue. Did you work out a solution to this?

---

### Post by danstoner on 2010-08-06
I also have this issue.

"short term fix" is:

#  sudo /etc/init.d/dnsmasq stop

 * Stopping DNS forwarder and DHCP server dnsmasq                        [ OK ] 


# virsh net-start default


Have not yet researched a long-term fix.

---

### Post by danstoner on 2010-08-06
Possibly related to bug:

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/231060](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/231060)


The dnsmasq package cannot be removed due to dependency issues.


I do want my vm to run in behind a NAT layer.

Disabling dnsmasq seems to have solved my issue.

Ubuntu lucid gui runlevel is 2.

```
sudo /etc/init.d/dnsmasq stop
sudo virsh net-start default
sudo mv /etc/rc2.d/S15dnsmasq /etc/rc2.d/K15dnsmasq
```Are there side-effects to running without dnsmasq?  I have not noticed anything yet.

---

### Post by danstoner on 2010-08-06
BTW, the error I was getting when trying to start the vm with virt-manager was:

Error starting domain: Failed to add tap interface to bridge 'virbr0': No such device

---

