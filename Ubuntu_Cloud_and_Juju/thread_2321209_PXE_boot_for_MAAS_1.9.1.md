---
title: "PXE boot for MAAS 1.9.1"
date: 2016-04-21
forum: Ubuntu Cloud and Juju
---

### Post by Kok_Hoe_Low on 2016-04-21
Hi Guys,

Pretty new to this ubuntu cloud stuff, hope experts here are able to help. I am now trying to enlist my nodes to MAAS via PXE boot.

Whenever it was power up, it alway complaint the following error:

could not find kernel image: ubuntu/amd64/generic/xenial/no-such-image/boot-kernel

under the "Booting under MAAS direction..."

nomodeset iscsi_target_name=iqn.2004-05.com.ubuntu:maas:ephemeral-ubuntu-i386-generic-xenial-no-such-image iscsi_target_ip=10.1.1.115 iscsi_target_port=3260 iscsi_initiator=maas-enlist ip=::::maas-enlist:BOOTIF ro root=/dev/disk/by-path/ip-10.1.1.115:3260-iscsi-iqn.2004-05.com.ubuntu:maas:ephemeral-ubuntu-i386-generic-xenial-no-such-image-lun-1 overlayroot=tmpfs cloud-config-url=http://192.168.1.115/MAAS/metadata/latest/enlist-preseed/?op=get_enlist_preseed log_host=192.168.1.115 log_port=514

In maas, i did import the image of the default 14.04 LTS amd64 architecture

Any help is appreciated. Thanks peoples :D

---

### Post by michael370 on 2016-04-22
I'm having the exact same issue. My only additional hint is that I had MaaS (version 1.9.1+bzr4543-0ubuntu1 (trusty1)) working for the last few weeks, then yesterday I swapped in some hard drives on my master and nodes (didn't touch the boot drive of the master) and deleted all of my nodes to start over from scratch. Now I can't boot nodes over PXE, and MaaS doesn't see them at all. My nodes are throwing the exact same error: 

> Could not find kernel image: ubuntu/amd64/generic/xenial/no-such-image/boot-kernel

It seems to be looking for a Xenial image, when OP and I both have MaaS set up to boot Trusty... I'm thinking there's some problem lurking under the surface common to both of our situations. 

Any help is appreciated here too!

---

### Post by binoy-mv on 2016-04-23
Hi,

This can be solved by importing the ubuntu 16.04 LTS image. This can be done in the following way

1) Login to maas
2) Click on the menu Images 
3) Select 16.04 LTS and the Architecture. 
4) Click on Apply Changes and wait the images load. 

Then try to reload your PXE boot

Hope this will help you :D

---

### Post by michael370 on 2016-04-25
Thanks for the reply, binoy-mv. I wanted the 14.04 image for consistency with other workstations running the same code (using this as a local cluster in an academic research setting). I had the 14.04 image downloaded, and could find it in /var/lib/maas/boot-resources/current/ubuntu. But when I went to the settings tab of the MaaS web interface the box underneath "Default Ubuntu release used for Commissioning" was empty.

I purged maas and reinstalled, and everything is booting fine. Don't know what the problem was, I hope the op figured out what was wrong.

---

### Post by phalen on 2016-05-01
double check how much disk space you have on your maas server.   2.3 gb is needed for the install but as soon as you get an image its over 16gb needed.  arm/x64/i386  of 14.04 and 15.10  it grew to nearly 30gb of disk space needed.  i was getting those kinds of errors due to lack of disk space on the vm I installed maas for testing.

---

### Post by george-bungarzescu on 2016-08-01
Actualy, just a reboot fixed the ( same ) problem !!!!

Steps:
Install maas
Prepare boot images (trusty)
Setup DHCP (according to maas instructions, see maas documentation )

Before restart (maybe just some services are required to be reloaded, maybe the "cache" of tftpd is implied ), the xenial message above

After restart, everything is ok

---

