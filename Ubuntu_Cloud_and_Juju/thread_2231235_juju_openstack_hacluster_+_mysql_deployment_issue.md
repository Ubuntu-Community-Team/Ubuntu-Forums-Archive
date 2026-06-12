---
title: "juju openstack hacluster + mysql deployment issue"
date: 2014-06-24
forum: Ubuntu Cloud and Juju
---

### Post by mike203 on 2014-06-24
Hello,
 I've been testing an Openstack HA deployment based on  details here: [https://wiki.ubuntu.com/ServerTeam/OpenStackHA](https://wiki.ubuntu.com/ServerTeam/OpenStackHA) . I've tried both a precise and trusty deployment and hacluster never seems to deploy correctly when I add a relationship between mysql and mysql-hacluster.

**I saw the following errors:**
2014-06-24 12:58:07 INFO juju-log Missing required principle configuration: []
2014-06-24 12:58:07 WARNING juju-log Unable to configure corosync right now, bailing
2014-06-24 12:58:07 INFO juju-log End config-changed hook.
2014-06-24 12:58:08 INFO juju-log ha:5: Missing required principle configuration: ['corosync_bindnetaddr', 'corosync_mcastport']
2014-06-24 12:58:08 WARNING juju-log ha:5: Unable to configure corosync right now, bailing

**Then traced it to line 41 in the hook.py file of the hacluster charm:**
               hacluster.get_network_address(
                    utils.relation_get('corosync_bindiface',
                                       unit, relid)
                ),
                'corosync_mcastport': utils.relation_get('corosync_mcastport',
                                                         unit, relid),


**Which is filled by mysql in the ha_relations.py file on line 21:**
    corosync_bindiface = utils.config_get('ha-bindiface')
    corosync_mcastport = utils.config_get('ha-mcastport')

[B]I used the following config to populate those values in mysql and have tried both eth0 and the br0 bridge created with the same results:
[/B]mysql:

 ha-bindiface: 'br0'
 ha-mcastport: '5411'
 vip_iface: 'br0'
 vip: '10.77.2.201'
 vip_cidr: '24'
#
**Here's my interface/IP info on one of the two mysql servers just in case it helps:**
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP qlen 1000
    link/ether 00:25:90:eb:e3:24 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:25:90:eb:e3:25 brd ff:ff:ff:ff:ff:ff
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP
    link/ether 00:25:90:eb:e3:24 brd ff:ff:ff:ff:ff:ff
    inet 10.77.2.105/24 brd 10.77.2.255 scope global br0
    inet6 fe80::225:90ff:feeb:e324/64 scope link
       valid_lft forever preferred_lft forever
ubuntu@r3n1:~$ brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.002590ebe324       no              eth0





**The get_corosync_conf call still can't seem to populate it, so I modified those hacluster hook.py lines to this which looked correct for corosync based on my interfaces:**
                'corosync_bindnetaddr': '10.77.2.0',
                'corosync_mcastport': '5411',




[B]With the above changes, hacluster continues deployment and ends with the log messages below but neither system ever listens on the virtual IP:
[/B]2014-06-24 13:02:19 INFO juju-log hanode:6: Ready to form cluster - informing peers
2014-06-24 13:02:20 INFO juju-log hanode:6: Using rid ha:7 unit mysql/0
2014-06-24 13:02:20 INFO juju-log hanode:6: Configuring and restarting corosync
2014-06-24 13:02:20 INFO hanode-relation-changed  * Restarting corosync daemon corosync
2014-06-24 13:02:20 INFO hanode-relation-changed    ...done.
2014-06-24 13:02:20 INFO juju-log hanode:6: Waiting for PCMK to start
2014-06-24 13:02:43 INFO juju-log hanode:6: Doing global cluster configuration
2014-06-24 13:02:43 INFO juju-log hanode:6: Configuring Resources
2014-06-24 13:02:43 INFO juju-log hanode:6: {}
2014-06-24 13:02:43 INFO juju-log hanode:6: Configuring Groups
2014-06-24 13:02:43 INFO juju-log hanode:6: {}
2014-06-24 13:02:43 INFO juju-log hanode:6: Configuring Master/Slave (ms)
2014-06-24 13:02:44 INFO juju-log hanode:6: {}
2014-06-24 13:02:44 INFO juju-log hanode:6: Configuring Orders
2014-06-24 13:02:44 INFO juju-log hanode:6: {}
2014-06-24 13:02:44 INFO juju-log hanode:6: Configuring Colocations
2014-06-24 13:02:44 INFO juju-log hanode:6: {}
2014-06-24 13:02:44 INFO juju-log hanode:6: Configuring Clones
2014-06-24 13:02:44 INFO juju-log hanode:6: {}

Does anyone have any more ideas on what to try? Is there another charm version that works correctly or am I missing some configuration? Thanks ahead of time for any help! Below is my juju status output for mysql, ceph and hacluster.


Thanks,
  -Mike


**Juju Service Status:**
services:
  ceph:
    charm: local:precise/ceph-106
    exposed: false
    relations:
      client:
      - mysql
      mon:
      - ceph
      osd:
      - ceph-osd
    units:
      ceph/0:
        agent-state: started
        agent-version: 1.18.4
        machine: "1"
        public-address: r3n1.maas
      ceph/1:
        agent-state: started
        agent-version: 1.18.4
        machine: "2"
        public-address: r4n1.maas
  ceph-osd:
    charm: local:precise/ceph-osd-15
    exposed: false
    relations:
      mon:
      - ceph
    units:
      ceph-osd/0:
        agent-state: started
        agent-version: 1.18.4
        machine: "3"
        public-address: r5n2.maas
      ceph-osd/1:
        agent-state: started
        agent-version: 1.18.4
        machine: "4"
        public-address: r1n1.maas
      ceph-osd/2:
        agent-state: started
        agent-version: 1.18.4
        machine: "5"
        public-address: r2n1.maas
  mysql:
    charm: local:precise/mysql-312
    exposed: false
    relations:
      ceph:
      - ceph
      cluster:
      - mysql
      ha:
      - mysql-hacluster
    units:
      mysql/0:
        agent-state: started
        agent-version: 1.18.4
        machine: "1"
        public-address: r3n1.maas
        subordinates:
          mysql-hacluster/1:
            upgrading-from: local:precise/hacluster-69
            agent-state: started
            agent-version: 1.18.4
            public-address: r3n1.maas
      mysql/1:
        agent-state: started
        agent-version: 1.18.4
        machine: "2"
        public-address: r4n1.maas
        subordinates:
          mysql-hacluster/0:
            upgrading-from: local:precise/hacluster-69
            agent-state: started
            agent-version: 1.18.4
            public-address: r4n1.maas
  mysql-hacluster:
    charm: local:precise/hacluster-69
    exposed: false
    relations:
      ha:
      - mysql
      hanode:
      - mysql-hacluster
    subordinate-to:
    - mysql

---

