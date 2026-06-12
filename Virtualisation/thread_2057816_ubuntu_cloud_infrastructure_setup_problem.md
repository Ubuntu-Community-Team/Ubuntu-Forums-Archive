---
title: "ubuntu cloud infrastructure setup problem"
date: 2012-09-14
forum: Virtualisation
---

### Post by saurabh4485 on 2012-09-14
Hi,

I am configuring the Ubuntu cloud infrastructure 12.04 LTS.
I sucessfully configured the MASS server with extra virtual ip.
**Mass Server** : eth0   => 192.168.10.171
                     eth0:0 => 192.168.10.172

Now, i install JUJU in the same server and configure the two nodes using Mac address. As per the documentation i configure two nodes on DHCP server.
**Network Range :** 192.168.10.171,192.168.10.178
Node1 => 192.168.10.174
Node2 => 192.168.10.178

after juju bootstrap these two nodes showing status ready and i can boot then by click on MASS server URL account.

Now, i am deploying the mysql & wordpress using JUJU its sucessfully configured but "JUJU status" command not showing the URL from which i can access it.
As per docs node1 is configured for mysql and node2 is configured for wordpress.

**Output :** 
mass@mass:~$ juju status
2012-09-14 18:06:08,922 INFO Connecting to environment...
2012-09-14 18:06:09,555 INFO Connected to environment.
machines:
  0:
    agent-state: running
    dns-name: node1
    instance-id: /MAAS/api/1.0/nodes/node-7c480086-fda1-11e1-bea0-e06995abcfb9/
    instance-state: unknown
  1:
    agent-state: not-started
    dns-name: node2
    instance-id: /MAAS/api/1.0/nodes/node-3ae06a02-fe28-11e1-b3fb-e06995abcfb9/
    instance-state: unknown
  2:
    instance-id: pending
  3:
    instance-id: pending
services:
  mysql:
    charm: cs:precise/mysql-7
    relations:
      db:
      - wordpress
    units:
      mysql/0:
        agent-state: pending
        machine: 1
        public-address: null
  wordpress:
    charm: cs:precise/wordpress-7
    exposed: true
    relations:
      db:
      - mysql
      - wordpress-db
      loadbalancer:
      - wordpress
    units:
      wordpress/0:
        agent-state: pending
        machine: 2
        open-ports: []
        public-address: null
  wordpress-db:
    charm: cs:precise/mysql-7
    relations:
      db:
      - wordpress
    units:
      wordpress-db/0:
        agent-state: pending
        machine: 3
        public-address: null
2012-09-14 18:06:10,172 INFO 'status' command finished successfully
 
[B]I am following the below document.
[https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure) [/B]

**Please guide me, what is my mistake.** :(

Regards
Saurabh

---

### Post by saurabh4485 on 2012-09-17
Hi,

Please help me to come out this problem. I am stuck on this.

Regards
Saurabh

---

### Post by saurabh4485 on 2012-09-25
Unfortunately, I didn't receive any help from this community regarding this R&D.so i have to move on to save my job and i configured the openstack with ubuntu 12.04 and its working fine.

Using MASS & JUJU i got success on Local env,but it was not feasible.In MASS ENV i ddidn't get Public ip address in JUJU STATUS command after deployment of mysql and wordpress. 

Regards
Saurabh

---

