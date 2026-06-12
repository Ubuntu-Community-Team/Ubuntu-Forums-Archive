---
title: "Openstack deployment issues"
date: 2021-02-27
forum: Virtualisation
---

### Post by deees2 on 2021-02-27
Hi,

I am getting hook failed: "config-changed", any guidance to debug the issue. I had deployed this through juju, status was working fine until I deployed VM instance.

  ```
ovn-chassis/0*             error     idle             10.141.14.62                       hook failed: "config-changed"


labuser@maas:~$ juju status
Model      Controller       Cloud/Region           Version  SLA          Timestamp
openstack  juju-controller  maas.dc.co.uk/default  2.7.6    unsupported  20:19:00Z


App                     Version  Status   Scale  Charm                   Store       Rev  OS      Notes
ceph-mon                15.2.7   active       1  ceph-mon                jujucharms   53  ubuntu
ceph-osd                15.2.7   active       2  ceph-osd                jujucharms  308  ubuntu
ceph-radosgw            15.2.7   active       1  ceph-radosgw            jujucharms  294  ubuntu
cinder                  17.0.1   active       1  cinder                  jujucharms  308  ubuntu
cinder-ceph             17.0.1   active       1  cinder-ceph             jujucharms  260  ubuntu
cinder-mysql-router     8.0.23   active       1  mysql-router            jujucharms    6  ubuntu
dashboard-mysql-router  8.0.23   active       1  mysql-router            jujucharms    6  ubuntu
glance                  21.0.0   active       1  glance                  jujucharms  303  ubuntu
glance-mysql-router     8.0.23   active       1  mysql-router            jujucharms    6  ubuntu
keystone                18.0.0   active       1  keystone                jujucharms  321  ubuntu
keystone-mysql-router   8.0.23   active       1  mysql-router            jujucharms    6  ubuntu
mysql-innodb-cluster    8.0.23   active       3  mysql-innodb-cluster    jujucharms    5  ubuntu
neutron-api             17.0.0   active       1  neutron-api             jujucharms  292  ubuntu
neutron-api-plugin-ovn  17.0.0   active       1  neutron-api-plugin-ovn  jujucharms    4  ubuntu
neutron-mysql-router    8.0.23   active       1  mysql-router            jujucharms    6  ubuntu
nova-cloud-controller   22.0.1   active       1  nova-cloud-controller   jujucharms  352  ubuntu
nova-compute            22.0.1   active       1  nova-compute            jujucharms  325  ubuntu
nova-mysql-router       8.0.23   active       1  mysql-router            jujucharms    6  ubuntu
ntp                     3.5      active       1  ntp                     jujucharms   44  ubuntu
openstack-dashboard     18.6.1   active       1  openstack-dashboard     jujucharms  311  ubuntu
ovn-central             20.03.1  active       2  ovn-central             jujucharms    5  ubuntu
ovn-chassis             20.03.1  error        1  ovn-chassis             jujucharms   10  ubuntu
placement               4.0.0    active       1  placement               jujucharms   17  ubuntu
placement-mysql-router  8.0.23   active       1  mysql-router            jujucharms    6  ubuntu
rabbitmq-server         3.8.2    active       1  rabbitmq-server         jujucharms  108  ubuntu
vault                   1.5.4    blocked      1  vault                   jujucharms   44  ubuntu
vault-mysql-router      8.0.23   active       1  mysql-router            jujucharms    6  ubuntu


Unit                         Workload  Agent  Machine   Public address  Ports              Message
ceph-mon/0*                  active    idle   0/lxd/0   10.141.14.54                       Unit is ready and clustered
ceph-osd/0                   active    idle   0         10.141.14.2                        Unit is ready (1 OSD)
ceph-osd/1*                  active    idle   1         10.141.14.62                       Unit is ready (1 OSD)
ceph-radosgw/0*              active    idle   0/lxd/1   10.141.14.46    80/tcp             Unit is ready
cinder/0*                    active    idle   0/lxd/2   10.141.14.45    8776/tcp           Unit is ready
  cinder-ceph/0*             active    idle             10.141.14.45                       Unit is ready
  cinder-mysql-router/0*     active    idle             10.141.14.45                       Unit is ready
glance/0*                    active    idle   0/lxd/3   10.141.14.48    9292/tcp           Unit is ready
  glance-mysql-router/0*     active    idle             10.141.14.48                       Unit is ready
keystone/0*                  active    idle   0/lxd/4   10.141.14.55    5000/tcp           Unit is ready
  keystone-mysql-router/0*   active    idle             10.141.14.55                       Unit is ready
mysql-innodb-cluster/0*      active    idle   1         10.141.14.62                       Unit is ready: Mode: R/O
mysql-innodb-cluster/1       active    idle   0/lxd/5   10.141.14.47                       Unit is ready: Mode: R/W
mysql-innodb-cluster/2       active    idle   1/lxd/0   10.141.14.57                       Unit is ready: Mode: R/O
neutron-api/0*               active    idle   0/lxd/6   10.141.14.53    9696/tcp           Unit is ready
  neutron-api-plugin-ovn/0*  active    idle             10.141.14.53                       Unit is ready
  neutron-mysql-router/0*    active    idle             10.141.14.53                       Unit is ready
nova-cloud-controller/0*     active    idle   0/lxd/7   10.141.14.44    8774/tcp,8775/tcp  Unit is ready
  nova-mysql-router/0*       active    idle             10.141.14.44                       Unit is ready
nova-compute/0*              active    idle   1         10.141.14.62                       Unit is ready
  ntp/0*                     active    idle             10.141.14.62    123/udp            chrony: Ready
  ovn-chassis/0*             error     idle             10.141.14.62                       hook failed: "config-changed"
openstack-dashboard/0*       active    idle   0/lxd/8   10.141.14.43    80/tcp,443/tcp     Unit is ready
  dashboard-mysql-router/0*  active    idle             10.141.14.43                       Unit is ready
ovn-central/0                active    idle   0/lxd/9   10.141.14.3     6641/tcp,6642/tcp  Unit is ready (northd: active)
ovn-central/1*               active    idle   1/lxd/1   10.141.14.56    6641/tcp,6642/tcp  Unit is ready (leader: ovnnb_db, ovnsb_db)
placement/0*                 active    idle   0/lxd/10  10.141.14.42    8778/tcp           Unit is ready
  placement-mysql-router/0*  active    idle             10.141.14.42                       Unit is ready
rabbitmq-server/0*           active    idle   0/lxd/11  10.141.14.49    5672/tcp           Unit is ready
vault/0*                     blocked   idle   0/lxd/12  10.141.14.52    8200/tcp           Vault service not running
  vault-mysql-router/0*      active    idle             10.141.14.52                       Unit is ready


Machine   State    DNS           Inst id               Series  AZ       Message
0         started  10.141.14.2   controller            focal   default  Deployed
0/lxd/0   started  10.141.14.54  juju-766828-0-lxd-0   focal   default  Container started
0/lxd/1   started  10.141.14.46  juju-766828-0-lxd-1   focal   default  Container started
0/lxd/2   started  10.141.14.45  juju-766828-0-lxd-2   focal   default  Container started
0/lxd/3   started  10.141.14.48  juju-766828-0-lxd-3   focal   default  Container started
0/lxd/4   started  10.141.14.55  juju-766828-0-lxd-4   focal   default  Container started
0/lxd/5   started  10.141.14.47  juju-766828-0-lxd-5   focal   default  Container started
0/lxd/6   started  10.141.14.53  juju-766828-0-lxd-6   focal   default  Container started
0/lxd/7   started  10.141.14.44  juju-766828-0-lxd-7   focal   default  Container started
0/lxd/8   started  10.141.14.43  juju-766828-0-lxd-8   focal   default  Container started
0/lxd/9   started  10.141.14.3   juju-766828-0-lxd-9   focal   default  Container started
0/lxd/10  started  10.141.14.42  juju-766828-0-lxd-10  focal   default  Container started
0/lxd/11  started  10.141.14.49  juju-766828-0-lxd-11  focal   default  Container started
0/lxd/12  started  10.141.14.52  juju-766828-0-lxd-12  focal   default  Container started
1         started  10.141.14.62  compute               focal   default  Deployed
1/lxd/0   started  10.141.14.57  juju-766828-1-lxd-0   focal   default  Container started
1/lxd/1   started  10.141.14.56  juju-766828-1-lxd-1   focal   default  Container started


labuser@maas:~$
```

---

### Post by wildmanne39 on 2021-02-27
Moved to Virtualisation sub-forum.

---

