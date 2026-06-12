---
title: "UEC booting fail"
date: 2010-08-20
forum: Server Platforms
---

### Post by herryson on 2010-08-20
I installed UEC(Ubuntu with Eucalyptus) using Ubuntu Server 10.04 LTS on cluster.
Then I have some following errors during booting servers.
Although severs have LSI SATA HBA, I installed Ubuntu not using LVM. I installed Ubuntu using entire disk.

One of error msg is like following, and server stops.

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 53723/4300800 files, 530418/17179648 blocks

Other error msg is like this, and server also stops after this msg.

fsck from util-linux-ng 2.17.2
init: procps main process (367) terminated with status 255
/dev/sda1: clean, 53723/4300800 files, 530418/17179648 blocks

And another error msg is like following. In this case server success to boot.

fsck from util-linux-ng 2.17.2
init: procps main process (367) terminated with status 255
/dev/sda1: clean, 53723/4300800 files, 530418/17179648 blocks
* starting AppArmor profiles [ok]
* Starting AOC devices discovery and mounting AoE filesystems
* not started
* Starting web server apache2
apache2 : Could not reliably determine the server's fully qualified domain name using 147.**.**.**(yadda yadda yadda) for ServeName

Can you figure out what is problem?
Is this hardware problem of disk?
This servers are old machines. They are 3 years old or more.

---

### Post by abhijeetdesai on 2010-08-27
having a similar problem !!!!

---

