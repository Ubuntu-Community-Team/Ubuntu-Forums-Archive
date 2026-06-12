---
title: "Xen 3.2 and vlans, no network on domU"
date: 2008-08-08
forum: Virtualisation
---

### Post by pløp on 2008-08-08
Some day ago, i have try to enable vlan on Xen DomU. I was able to start the domU, but without network.

Here, what i have do (on Ubuntu Server 8.04.1 - amd64):
```
apt-get install vlan
echo '8021q' >>/etc/initramfs-tools/modules
echo 'scsi_mod' >>/etc/initramfs-tools/modules
echo 'sd_mod' >>/etc/initramfs-tools/modules
apt-get install ubuntu-xen-server
```

I setup my vlan interface on /etc/network/interfaces, change the switch port configuration (untagged -> tagged) and reboot the box.

After the reboot, I'm reconnect with SSH, very good it's work with vlan policy.

I build a domu, i change the specify the good netdev for the domu (in the good vlan), and i lanch the domu.

Everething work, but the domu have'nt cany network connexion. I try to ping it, nothing. I try to lookup the ARP table, and i have "IP.ADRESSE (incomplete HW address)" if i remember.

For the network configuration, i have this :
```
             ,------ vlan 2 (private vlan, only for the dom0)
  peth0 -----
             `------ vlan X (public vlan, for the domu)
```

If i put a ip address on the vlan X for the dom0, i can have access on the dom0 with this IP adress

I have also try the multiple-vlan script by [renial.net]("http://renial.net/weblog/2007/02/27/xen-vlan/"), and nothing.

Do have any suggestion ?

---

