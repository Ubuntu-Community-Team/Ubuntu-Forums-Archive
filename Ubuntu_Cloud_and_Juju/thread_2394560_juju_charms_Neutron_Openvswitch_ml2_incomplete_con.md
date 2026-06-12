---
title: "juju charms Neutron Openvswitch ml2 incomplete configuration"
date: 2018-06-18
forum: Ubuntu Cloud and Juju
---

### Post by Rockfreak101 on 2018-06-18
I am deploying a openstack node with the openstack-base bundle. I am running into issues where my networks are not assigned to the correct vlan, or none for flat. I've noticed ml2 conf is missing on my computes, wich I suspect to be part of the problem, but I can't figure out why, I've done various permutations of the build always with same result.

I am new to posting my issues so please inform me what you need from me and I'll provide it.

My config :
```
series: xenialapplications:
  neutron-gateway:
    charm: cs:neutron-gateway-247
    num_units: 1
    options:
      plugin: ovs
      run-internal-router: none
      bridge-mappings: 'physnet0:br-ex'
      data-port: 'br-ex:bond0'
      flat-network-providers: physnet0
      debug: true
      instance-mtu: 8050
      enable-l3-agent: false
      enable-metadata-network: true
      openstack-origin: 'cloud:xenial-queens'
      os-data-network: 172.17.2.0/27
      use-syslog: true
      verbose: true
      vlan-ranges: 'physnet0:100:200'
      worker-multiplier: 0.75
      #config-flags: core_plugin=ml2
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    annotations:
      gui-x: '0'
      gui-y: '0'
    to:
      - '0'
  rabbitmq-server:
    charm: cs:rabbitmq-server-72
    num_units: 1
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    annotations:
      gui-x: '500'
      gui-y: '250'
    to:
      - 'lxd:neutron-gateway/0'
  mysql:
    charm: cs:percona-cluster-259
    num_units: 1
    options:
      access-network: 172.17.1.0/24
      cluster-network: 172.17.1.0/24
      innodb-buffer-pool-size: 256M
      max-connections: 1000
    constraints: >-
      spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net
    annotations:
      gui-x: '0'
      gui-y: '250'
    to:
      - 'lxd:neutron-gateway/0'
  nova-cloud-controller:
    charm: cs:nova-cloud-controller-306
    num_units: 1
    options:
      network-manager: Neutron
      bridge-interface: ''
      bridge-ip: ''
      bridge-netmask: ''
      console-access-protocol: novnc
      single-nova-consoleauth: False
      debug: true
      enable-serial-console: true
      openstack-origin: 'cloud:xenial-queens'
      os-admin-network: 172.17.1.0/24
      os-internal-network: 172.17.1.0/24
      os-public-network: 10.76.83.96/27
      ram-allocation-ratio: '4.0'
      service-guard: true
      use-internal-endpoints: true
      use-syslog: true
      verbose: true
      worker-multiplier: 0.75
    constraints: >-
      spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net
    annotations:
      gui-x: '0'
      gui-y: '500'
    to:
      - 'lxd:nova-compute/1'
  openstack-dashboard:
    charm: cs:openstack-dashboard-257
    num_units: 1
    options:
      cinder-backup: true
      endpoint-type: 'publicURL,internalURL,adminURL'
      neutron-network-firewall: true
      openstack-origin: 'cloud:xenial-queens'
      password-retrieve: true
      use-syslog: true
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    expose: true
    annotations:
      gui-x: '500'
      gui-y: '-250'
    to:
      - 'lxd:nova-compute/2'
  ceph-osd:
    charm: cs:ceph-osd-257
    num_units: 2
    options:
      autotune: true
      ceph-cluster-network: 172.17.3.0/24
      ceph-public-network: 172.17.4.0/24
      crush-initial-weight: '1.0'
      loglevel: 10
      osd-devices: >-
        /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh /dev/sdi /dev/sdj
        /dev/sdk /dev/sdl /dev/sdm /dev/sdn /dev/sdo /dev/sdp /dev/sdq /dev/sdr
        /dev/sds /dev/sdt /dev/sdu /dev/sdv
      osd-journal: /dev/sdb
      osd-journal-size: 10024
      osd-reformat: 'true'
      source: 'cloud:xenial-queens'
      use-syslog: true
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    annotations:
      gui-x: '1000'
      gui-y: '500'
    to:
      - '1'
      - '2'
  cinder-ceph:
    charm: cs:cinder-ceph-231
    options:
      ceph-osd-replication-count: 2
      use-syslog: true
    annotations:
      gui-x: '750'
      gui-y: '250'
  cinder:
    charm: cs:cinder-268
    num_units: 1
    options:
      block-device: None
      ceph-osd-replication-count: 2
      debug: true
      glance-api-version: 2
      openstack-origin: 'cloud:xenial-queens'
      os-internal-network: 172.17.1.0/24
      os-public-network: 10.76.83.96/27
      use-internal-endpoints: true
      use-syslog: true
      verbose: true
      worker-multiplier: 0.75
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    annotations:
      gui-x: '750'
      gui-y: '0'
    to:
      - 'lxd:nova-compute/0'
  nova-compute:
    charm: cs:nova-compute-282
    num_units: 3
    options:
      bridge-interface: ''
      bridge-ip: ''
      bridge-netmask: ''
      ceph-osd-replication-count: 2
      config-flags: default_ephemeral_format=ext4
      debug: true
      enable-live-migration: true
      enable-resize: true
      libvirt-image-backend: rbd
      openstack-origin: 'cloud:xenial-queens'
      os-internal-network: 172.17.1.0/24
      resume-guests-state-on-host-boot: true
      use-internal-endpoints: true
      use-multipath: true
      use-syslog: true
      verbose: true
      config-flags: libvirt_vif_driver= ' '
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    annotations:
      gui-x: '250'
      gui-y: '250'
    to:
      - '1'
      - '2'
      - '3'
  ntp:
    charm: cs:ntp-24
    annotations:
      gui-x: '1000'
      gui-y: '0'
  glance:
    charm: cs:glance-264
    num_units: 1
    options:
      ceph-osd-replication-count: 2
      openstack-origin: 'cloud:xenial-queens'
      os-admin-network: 172.17.1.0/24
      os-internal-network: 172.17.1.0/24
      os-public-network: 10.76.83.96/27
      use-internal-endpoints: true
      use-syslog: true
      verbose: true
      worker-multiplier: 0.75
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    annotations:
      gui-x: '250'
      gui-y: '0'
    to:
      - 'lxd:nova-compute/1'
  neutron-api:
    charm: cs:neutron-api-258
    num_units: 1
    options:
      neutron-plugin: ovs
      neutron-external-network: ext_net
      debug: true
      default-tenant-network-type: vxlan
      dns-ha: true
      enable-dvr: true
      l2-population: true
      enable-ml2-port-security: true
      enable-ml2-dns: true
      enable-qos: true
      extra-source: 'cloud:xenial-queens'
      global-physnet-mtu: 9000
      manage-neutron-plugin-legacy-mode: true
      flat-network-providers: physnet0
      neutron-security-groups: true
      openstack-origin: 'cloud:xenial-queens'
      os-admin-network: 172.17.1.0/24
      os-internal-network: 172.17.1.0/24
      os-public-network: 10.76.83.96/27
      overlay-network-type: vxlan gre
      use-syslog: true
      verbose: true
      vlan-ranges: 'physnet0:100:200'
      vni-ranges: 1000:2000
      vsd-auth-ssl: false
      worker-multiplier: 0.75
      supported-pci-vendor-devs: 14e4:1657 8086:1528
      config-flags: core_plugin=ml2
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    annotations:
      gui-x: '500'
      gui-y: '500'
    to:
      - 'lxd:nova-compute/0'
  ceph-radosgw:
    charm: cs:ceph-radosgw-256
    num_units: 1
    options:
      os-admin-network: 172.17.1.0/24
      os-internal-network: 172.17.1.0/24
      os-public-network: 10.76.83.96/27
      source: 'cloud:xenial-queens'
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    expose: true
    annotations:
      gui-x: '1000'
      gui-y: '250'
    to:
      - '0'
  ceph-mon:
    charm: cs:ceph-mon-23
    num_units: 3
    options:
      ceph-cluster-network: 172.17.3.0/24
      ceph-public-network: 172.17.4.0/24
      expected-osd-count: 38
      loglevel: 10
      source: 'cloud:xenial-queens'
      use-syslog: true
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    annotations:
      gui-x: '750'
      gui-y: '500'
    to:
      - 'lxd:nova-compute/0'
      - 'lxd:nova-compute/1'
      - 'lxd:nova-compute/2'
  neutron-openvswitch:
    charm: cs:neutron-openvswitch-249
    options:
      bridge-mappings: 'physnet0:br-ex'
      data-port: 'br-ex:bond0'
      debug: true
      dns-servers: 10.76.83.97
     # dnsmasq-flags: 'dhcp-option-force=26,1550'
      enable-local-dhcp-and-metadata: true
      os-data-network: 172.17.2.0/24
      flat-network-providers: physnet0
      use-syslog: true
      verbose: true
      vlan-ranges: 'physnet0:100:200'
    annotations:
      gui-x: '250'
      gui-y: '500'
  keystone:
    charm: cs:keystone-275
    num_units: 1
    options:
      admin-password: new1-Sys
      debug: true
      log-level: DEBUG
      openstack-origin: 'cloud:xenial-queens'
      os-admin-network: 10.76.83.96/27
      os-internal-network: 172.17.1.0/24
      os-public-network: 10.76.83.96/27
      use-syslog: true
      verbose: true
      worker-multiplier: 0.75
    constraints: 'spaces=default,os-internal-net,os-tenant-net,os-storage-net,os-stor-mgt-net'
    expose: true
    annotations:
      gui-x: '500'
      gui-y: '0'
    to:
      - 'lxd:nova-compute/2'
relations:
  - - 'ceph-mon:client'
    - 'cinder-ceph:ceph'
  - - 'nova-compute:amqp'
    - 'rabbitmq-server:amqp'
  - - 'neutron-gateway:amqp'
    - 'rabbitmq-server:amqp'
  - - 'keystone:shared-db'
    - 'mysql:shared-db'
  - - 'nova-cloud-controller:identity-service'
    - 'keystone:identity-service'
  - - 'glance:identity-service'
    - 'keystone:identity-service'
  - - 'neutron-api:identity-service'
    - 'keystone:identity-service'
  - - 'neutron-openvswitch:neutron-plugin-api'
    - 'neutron-api:neutron-plugin-api'
  - - 'neutron-api:shared-db'
    - 'mysql:shared-db'
  - - 'neutron-api:amqp'
    - 'rabbitmq-server:amqp'
  - - 'neutron-gateway:neutron-plugin-api'
    - 'neutron-api:neutron-plugin-api'
  - - 'glance:shared-db'
    - 'mysql:shared-db'
  - - 'glance:amqp'
    - 'rabbitmq-server:amqp'
  - - 'nova-cloud-controller:image-service'
    - 'glance:image-service'
  - - 'nova-cloud-controller:cloud-compute'
    - 'nova-compute:cloud-compute'
  - - 'nova-cloud-controller:amqp'
    - 'rabbitmq-server:amqp'
  - - 'nova-cloud-controller:quantum-network-service'
    - 'neutron-gateway:quantum-network-service'
  - - 'nova-compute:neutron-plugin'
    - 'neutron-openvswitch:neutron-plugin'
  - - 'neutron-openvswitch:amqp'
    - 'rabbitmq-server:amqp'
  - - 'openstack-dashboard:identity-service'
    - 'keystone:identity-service'
  - - 'nova-cloud-controller:shared-db'
    - 'mysql:shared-db'
  - - 'nova-cloud-controller:neutron-api'
    - 'neutron-api:neutron-api'
  - - 'cinder:image-service'
    - 'glance:image-service'
  - - 'cinder:amqp'
    - 'rabbitmq-server:amqp'
  - - 'cinder:identity-service'
    - 'keystone:identity-service'
  - - 'cinder:cinder-volume-service'
    - 'nova-cloud-controller:cinder-volume-service'
  - - 'cinder-ceph:storage-backend'
    - 'cinder:storage-backend'
  - - 'ceph-mon:client'
    - 'nova-compute:ceph'
  - - 'nova-compute:ceph-access'
    - 'cinder-ceph:ceph-access'
  - - 'cinder:shared-db'
    - 'mysql:shared-db'
  - - 'ceph-mon:client'
    - 'glance:ceph'
  - - 'ceph-osd:mon'
    - 'ceph-mon:osd'
  - - 'ntp:juju-info'
    - 'nova-compute:juju-info'
  - - 'ntp:juju-info'
    - 'neutron-gateway:juju-info'
  - - 'ceph-radosgw:mon'
    - 'ceph-mon:radosgw'
  - - 'ceph-radosgw:identity-service'
    - 'keystone:identity-service'
  - - 'nova-compute:image-service'
    - 'glance:image-service'
machines:
  '0':
    series: xenial
    constraints: arch=amd64 cpu-cores=32 mem=163840 tags=a-000
  '1':
    series: xenial
    constraints: arch=amd64 cpu-cores=32 mem=65536 tags=a-000
  '2':
    series: xenial
    constraints: arch=amd64 cpu-cores=32 mem=65536 tags=a-000
  '3':
    series: xenial
    constraints: arch=amd64 cpu-cores=32 mem=163840 tags=a-000

```

Problem example :
```
tenid=$(openstack project show v666 -f value -c id)
neutron net-create --tenant-id $tenid v666-100 --provider:network_type vlan --provider:physical_network physnet0 --provider:segmentation_id 100 --router:external=True
neutron subnet-create --tenant-id $tenid v666-100 10.4.163.192/27 --gateway 10.4.163.222 --allocation-pool start=10.4.163.194,end=10.4.163.220 --enable-dhcp --name v666-100
jluczani@us-a-reg-maas:~/openstack-base$ neutron port-list | grep 10.4.163
| e3b1974f-d614-4a5c-b9f7-4cfcf5d18a56 |      | fa:16:3e:40:6d:6e | {"subnet_id": "0fc59cfa-8cc0-4223-bcd3-6c697e90e328", "ip_address": "10.4.163.194"} |
jluczani@us-a-reg-maas:~/openstack-base$ ping -c 3 10.4.163.194
PING 10.4.163.194 (10.4.163.194) 56(84) bytes of data.


--- 10.4.163.194 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2000ms
jluczani@us-a-reg-maas:~/openstack-base$ neutron port-show e3b1974f-d614-4a5c-b9f7-4cfcf5d18a56 -F binding:host_id -F  binding:vif_details -F device_owner -F device_id
+---------------------+-------------------------------------------------------------------------------+
| Field               | Value                                                                         |
+---------------------+-------------------------------------------------------------------------------+
| binding:host_id     | ilo-7428                                                                      |
| binding:vif_details | {"port_filter": true, "datapath_type": "system", "ovs_hybrid_plug": true}     |
| device_id           | dhcp2ce52741-8ba3-5ea6-b4c9-b88c3d5002e7-0cba6e44-5a1f-470a-98c1-648d8016c6f2 |
| device_owner        | network:dhcp                                                                  |
+---------------------+-------------------------------------------------------------------------------+

```
```
jluczani@us-a-reg-maas:~/openstack-base$ juju ssh 1
ubuntu@ilo-7428:~$ sudo ovs-vsctl show
sudo: unable to resolve host ilo-7428
394da09c-3436-438d-af8b-23551947cdff
    Manager "ptcp:6640:127.0.0.1"
        is_connected: true
    Bridge br-ex
    Bridge br-int
        Controller "tcp:127.0.0.1:6633"
            is_connected: true
        fail_mode: secure
        Port "tape3b1974f-d6"
            tag: 1
            Interface "tape3b1974f-d6"
        Port int-br-ex
            Interface int-br-ex
                type: patch
                options: {peer=phy-br-ex}
        Port "qvob6c9a70b-e1"
            tag: 2
            Interface "qvob6c9a70b-e1"
        Port "qr-ff4035c9-57"
            tag: 2
            Interface "qr-ff4035c9-57"
                type: internal
        Port "qvofab40efd-a8"
            tag: 2
            Interface "qvofab40efd-a8"
        Port "qvo182811ec-a3"
            tag: 2
            Interface "qvo182811ec-a3"
        Port br-int
            Interface br-int
                type: internal
        Port "fg-3d8b97c3-83"
            tag: 3
            Interface "fg-3d8b97c3-83"
                type: internal
        Port patch-tun
            Interface patch-tun
                type: patch
                options: {peer=patch-int}
    ovs_version: "2.9.0"

```

please note I have no ports with the appropriate tag of 100 as provided by my neutron config.

Also I have installed other nodes and have always had openvswitch and ml2 installed and configured on my computes, trippleO, but in juju instance I am not getting the same config as expected.
```

jluczani@us-a-reg-maas:~/openstack-base$ juju ssh nova-compute/0
ubuntu@ilo-7428:~$ sudo ls /etc/neutron/
sudo: unable to resolve host ilo-7428
api-paste.ini   dnsmasq.conf      l3_agent.ini        neutron.conf  policy.d     rootwrap.conf  secret.txt
dhcp_agent.ini  fwaas_driver.ini  metadata_agent.ini  plugins       policy.json  rootwrap.d
ubuntu@ilo-7428:~$ sudo ls /etc/neutron/plugins/ml2/
sudo: unable to resolve host ilo-7428
openvswitch_agent.ini

```

```
jluczani@us-a-reg-maas:~/openstack-base$ juju ssh neutron-api/0
ubuntu@juju-2b87f9-1-lxd-2:~$ sudo ls /etc/neutron/
sudo: unable to resolve host juju-2b87f9-1-lxd-2
api-paste.ini     l3_agent.ini  neutron_lbaas.conf   plugins   policy.json    rootwrap.d
fwaas_driver.ini  neutron.conf  neutron_vpnaas.conf  policy.d  rootwrap.conf  services_lbaas.conf
ubuntu@juju-2b87f9-1-lxd-2:~$ sudo ls /etc/neutron/plugins/ml2/
sudo: unable to resolve host juju-2b87f9-1-lxd-2
ml2_conf.ini

```








So either my config is incorrect still, which I can't identify, or there may be a limitation to the charms?

Thank you for any assistance.

---

### Post by fahadysf on 2019-01-14
I know it has been around half a year. But could you share how you got around this. I am in a similar situation where the neutron configs are empty on the comute nodes, which might even be normal. But the main issue is that instances can't talk to each other or their gateway and don't get DHCP IPs in networks of type 'local' which are supposed to be linked together via GRE tunnels by neutron-openvswitch.

---

