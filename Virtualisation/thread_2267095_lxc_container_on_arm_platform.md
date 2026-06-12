---
title: "lxc container on arm platform"
date: 2015-02-27
forum: Virtualisation
---

### Post by praveen_kumar_verm on 2015-02-27
Hi, 




we want to use lxc-utils on ARM platform.


We have downloaded the ubuntu filesystem from following site.
[http://images.linuxcontainers.org/images/ubuntu/precise/armhf/default/20150226_03:49/](http://images.linuxcontainers.org/images/ubuntu/precise/armhf/default/20150226_03:49/)


ubuntu image info:
=========================================================================================
root@10:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise


root@10:~# cat /etc/apt/sources.list
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) precise main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) precise-updates main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) precise-security main restricted universe multiverse


# TI release PPA
deb [http://ppa.launchpad.net/tiomap-dev/release/ubuntu](http://ppa.launchpad.net/tiomap-dev/release/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/tiomap-dev/release/ubuntu](http://ppa.launchpad.net/tiomap-dev/release/ubuntu) precise main
=========================================================================================


We have properly configured the network settings to connect to the external url.


Please help us in following issues:


1. When we tried to install package using apt-get, We got the following error.  What is "Size mismatch" error in following log.


root@10:~# apt-get install lxc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apparmor bridge-utils cgroup-lite cloud-utils debootstrap dnsmasq-base
  euca2ools iptables libapparmor1 libcap2 libcap2-bin libgmp10 libidn11
  libnetfilter-conntrack3 libnfnetlink0 libpam-cap libyaml-0-2 openssl
  python-boto python-crypto python-m2crypto python-paramiko python-yaml rsync
  wget
Suggested packages:
  apparmor-profiles apparmor-docs apparmor-utils libcap-dev btrfs-tools lvm2
  qemu-user-static ca-certificates python-crypto-dbg python-crypto-doc
  openssh-server
The following NEW packages will be installed:
  apparmor bridge-utils cgroup-lite cloud-utils debootstrap dnsmasq-base
  euca2ools iptables libapparmor1 libcap2 libcap2-bin libgmp10 libidn11
  libnetfilter-conntrack3 libnfnetlink0 libpam-cap libyaml-0-2 lxc openssl
  python-boto python-crypto python-m2crypto python-paramiko python-yaml rsync
  wget
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,544 kB of archives.
After this operation, 19.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  apparmor libidn11 bridge-utils libcap2 libgmp10 libyaml-0-2 libapparmor1
  libnfnetlink0 libnetfilter-conntrack3 dnsmasq-base iptables rsync lxc
  python-m2crypto openssl wget python-boto euca2ools libcap2-bin libpam-cap
  python-crypto python-paramiko python-yaml cgroup-lite cloud-utils
  debootstrap
Install these packages without verification [y/N]? y
Get:1 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise-updates/main apparmor armhf 2.7.102-0ubuntu3.10 [292 kB]
Get:2 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise/main libidn11 armhf 1.23-2 [107 kB]
Get:3 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) precise-updates/main bridge-utils armhf 1.5-2ubuntu7 [32.1 kB]
Fetched 5,070 B in 5s (879 B/s)
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/a/apparmor/apparmor_2.7.102-0ubuntu3.10_armhf.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/a/apparmor/apparmor_2.7.102-0ubuntu3.10_armhf.deb)  Size mismatch
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/libi/libidn/libidn11_1.23-2_armhf.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/libi/libidn/libidn11_1.23-2_armhf.deb)  Size mismatch
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/b/bridge-utils/bridge-utils_1.5-2ubuntu7_armhf.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/b/bridge-utils/bridge-utils_1.5-2ubuntu7_armhf.deb)  Size mismatch


Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/d/debootstrap/debootstrap_1.0.40~ubuntu0.7_all.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/d/debootstrap/debootstrap_1.0.40~ubuntu0.7_all.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


2. So I manually downloaded all the required package for lxc on HOST PC and manually installed on target board(ARM). So I am able to successfully run lxc-execute command; but when I tried to create a package using lxc-create I got the follwing error.


root@10:~# lxc-create -n test -t ubuntu 


No config file specified, using the default config
debootstrap is /usr/sbin/debootstrap
Checking cache download in /var/cache/lxc/precise/rootfs-armhf ... 
installing packages: vim,ssh
Downloading ubuntu precise minimal ...
I: Retrieving Release
E: Invalid Release file, no valid components
failed to execute template 'ubuntu'
aborted


Please let us know how to overcome the above error. Is it possible to use the existing rootfs for a the container also, so it won't look for network for additional info.


3. I tried to update using apt-get but got the following error:
root@10:~# apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Get:2 [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release.gpg
Get:3 [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates Release.gpg
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release 
Get:5 [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release     
E: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

---

### Post by praveen_kumar_verm on 2015-03-02
Hi, 

I have used the existing ubuntu image(for arm target board) & able to use lxc-create.
Please help me resolving apt-get related issues.
 
Thanks & Regards
Prav

---

