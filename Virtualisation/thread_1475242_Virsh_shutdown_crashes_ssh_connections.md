---
title: "Virsh shutdown crashes ssh connections"
date: 2010-05-06
forum: Virtualisation
---

### Post by MerlinGuy on 2010-05-06
Hello,

I am running kvm on a Lucid - amd64 platform.  I have a number of vm guests which I connect to from a Window's machine via Putty or from the Host server using ssh.  My problem is if I use the 'virsh shutdown vm0' or 'virsh destroy vm0' I have a 50-50 chance of losing all my ssh connections to my host server from my Windows Desktop.  If I go directly to the host server and issue a '/etc/init.d/networking restart' I can reconnect immediately, if not I have to wait around 5-10 minutes before I can re-establish a ssh connect to the host server.  I set the server up to use a network bridge and the vm guests can be either static or dhcp.

Anyone else encountering this issue?

Any suggestions?

---

### Post by daimoniac on 2011-02-08
I'm facing the exact same problem using 10.04 LTS (Lucid).

Have you been able to resolve this issue?

---

### Post by daimoniac on 2011-02-08
Corresponding syslog:

```
Feb  7 14:13:48 ixskvm01 kernel: [8750831.367622] brpri1: port 19(ixvw01190) entering disabled state
Feb  7 14:13:48 ixskvm01 kernel: [8750832.092059] device ixvw01190 left promiscuous mode
Feb  7 14:13:48 ixskvm01 kernel: [8750832.092066] brpri1: port 19(ixvw01190) entering disabled state
Feb  7 14:13:51 ixskvm01 kernel: [8750834.339920] brpub2: port 15(ixvw01191) entering disabled state
Feb  7 14:13:52 ixskvm01 kernel: [8750836.185585] device ixvw01191 left promiscuous mode
Feb  7 14:13:52 ixskvm01 kernel: [8750836.185592] brpub2: port 15(ixvw01191) entering disabled state
Feb  7 14:13:55 ixskvm01 upstart-udev-bridge[28700]: Disconnected from Upstart
Feb  7 14:13:55 ixskvm01 init: upstart-udev-bridge main process (28700) terminated with status 1
Feb  7 14:13:55 ixskvm01 init: upstart-udev-bridge main process ended, respawning
Feb  7 14:13:55 ixskvm01 kernel: [8750838.569054] type=1505 audit(1297084435.246:168): operation="profile_remove" pid=4024 name=libvirt-1c683e63-9137-5e5c-257d-7cb299341c7e namespace=default
Feb  7 14:17:07 ixskvm01 kernel: [8751030.962267] nf_conntrack: table full, dropping packet.
Feb  7 14:17:13 ixskvm01 kernel: [8751036.614856] nf_conntrack: table full, dropping packet.
Feb  7 14:17:24 ixskvm01 kernel: [8751047.586480] nf_conntrack: table full, dropping packet.
Feb  7 14:18:06 ixskvm01 kernel: [8751089.049822] nf_conntrack: table full, dropping packet.
Feb  7 14:19:58 ixskvm01 kernel: [8751201.569266] type=1505 audit(1297084798.816:169): operation="profile_load" pid=4246 name=libvirt-1c683e63-9137-5e5c-257d-7cb299341c7e
Feb  7 14:19:58 ixskvm01 kernel: [8751201.710928] device ixvw01190 entered promiscuous mode
Feb  7 14:19:58 ixskvm01 kernel: [8751201.712951] brpri1: port 19(ixvw01190) entering forwarding state
Feb  7 14:19:58 ixskvm01 kernel: [8751201.716691] device ixvw01191 entered promiscuous mode
Feb  7 14:19:58 ixskvm01 kernel: [8751201.718766] brpub2: port 15(ixvw01191) entering forwarding state

```

---

### Post by alessiogambi on 2011-05-10
Sorry, 
just retried and this did not solved the problem.

-- Alessio

Hi,
I had the same problem (Ubuntu natty) with a bridge extbr0 "manually" created and associated to eth0

I solved this by changing the **/etc/network/interfaces** file and rebooting (to remove the bridge extbr0 associated to eth0):

Old file was:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
 	address XXX.XXX.XXX.XXX
	netmask XXX.XXX.XXX.XXX
	network XXX.XXX.XXX.XXX
	broadcast XXX.XXX.XXX.XXX
	gateway XXX.XXX.XXX.XXX
	dns-nameservers XXX.XXX.XXX.XXX

---------------------------------
---------------------------------

The new file is:
auto lo
iface lo inet loopback

# The primary network interface
auto **br0**
iface **br0** inet static
	address XXX.XXX.XXX.XXX
	netmask XXX.XXX.XXX.XXX
	network XXX.XXX.XXX.XXX
	broadcast XXX.XXX.XXX.XXX
	gateway XXX.XXX.XXX.XXX
	dns-nameservers XXX.XXX.XXX.XXX

bridge_ports	**eth0**
bridge_stp	off
bridge_fd	9

---

### Post by Dedoimedo on 2011-05-12
Does this happen with non-putty ssh connections?
Are you using openssh or another ssh server/client?
Dedoimedo

---

### Post by alessiogambi on 2011-05-30
openssh... but the host machine is not even reachable via ping.

---

