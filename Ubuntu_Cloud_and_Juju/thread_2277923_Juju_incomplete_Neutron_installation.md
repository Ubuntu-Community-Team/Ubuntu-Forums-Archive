---
title: "Juju incomplete Neutron installation"
date: 2015-05-12
forum: Ubuntu Cloud and Juju
---

### Post by nicolasleiva on 2015-05-12
We have installed Openstack on distributed nodes using Juju + MAAS. Everything looks good, but **Neutron cli is unresponsive**.


```
[SIZE=1][FONT=courier new]user@controller:~$ nova list[/FONT][/SIZE]
[SIZE=1][FONT=courier new]+----+------+--------+------------+-------------+----------+[/FONT][/SIZE]
[SIZE=1][FONT=courier new]| ID | Name | Status | Task State | Power State | Networks |[/FONT][/SIZE]
[SIZE=1][FONT=courier new]+----+------+--------+------------+-------------+----------+[/FONT][/SIZE]
[SIZE=1][FONT=courier new]+----+------+--------+------------+-------------+----------+[/FONT][/SIZE]
[SIZE=1][FONT=courier new]user@controller:~$[/FONT][/SIZE]
[SIZE=1][FONT=courier new]user@controller:~$ neutron --version[/FONT][/SIZE]
[SIZE=1][FONT=courier new]2.3.4[/FONT][/SIZE]
[SIZE=1][FONT=courier new]user@controller:~$[/FONT][/SIZE]
[SIZE=1][FONT=courier new]user@controller:~$ neutron net-list[/FONT][/SIZE]
[SIZE=1][FONT=courier new]**Connection to neutron failed: (504, 'Gateway Timeout')**[/FONT][/SIZE]
[SIZE=1][FONT=courier new]user@controller:~$[/FONT][/SIZE]

```


If we pressed CRTL+C, we would get:


```
[FONT=courier new][SIZE=1]user@controller:~$ neutron net-list[/SIZE][/FONT]
[FONT=courier new][SIZE=1]^CTraceback (most recent call last):[/SIZE][/FONT]
[FONT=courier new][SIZE=1]  File "/usr/bin/neutron", line 10, in <module>[/SIZE][/FONT]
[FONT=courier new][SIZE=1]    sys.exit(main())[/SIZE][/FONT]
[FONT=courier new][SIZE=1]<snip>[/SIZE][/FONT]
[FONT=courier new][SIZE=1]** File "/usr/lib/python2.7/dist-packages/neutronclient/client.py", line 239, in authenticate**[/SIZE][/FONT]
[FONT=courier new][SIZE=1]**    content_type="application/json")**[/SIZE][/FONT]
[FONT=courier new][SIZE=1]  File "/usr/lib/python2.7/dist-packages/neutronclient/client.py", line 146, in _cs_request[/SIZE][/FONT]
[FONT=courier new][SIZE=1]    resp, body = self.request(*args, **kargs)[/SIZE][/FONT]
[FONT=courier new][SIZE=1]  File "/usr/lib/python2.7/dist-packages/httplib2/__init__.py", line 1569, in request[/SIZE][/FONT]
[FONT=courier new][SIZE=1]    (response, content) = self._request(conn, authority, uri, request_uri, method, body, headers, redirections, cachekey)[/SIZE][/FONT]
[FONT=courier new][SIZE=1]  File "/usr/lib/python2.7/dist-packages/httplib2/__init__.py", line 1316, in _request[/SIZE][/FONT]
[FONT=courier new][SIZE=1]    (response, content) = self._conn_request(conn, request_uri, method, body, headers)[/SIZE][/FONT]
[FONT=courier new][SIZE=1]  File "/usr/lib/python2.7/dist-packages/httplib2/__init__.py", line 1251, in _conn_request[/SIZE][/FONT]
[FONT=courier new][SIZE=1]    conn.connect()[/SIZE][/FONT]
[FONT=courier new][SIZE=1]  File "/usr/lib/python2.7/dist-packages/httplib2/__init__.py", line 900, in connect[/SIZE][/FONT]
[FONT=courier new][SIZE=1]    self.sock.connect((self.host, self.port) + sa[2:])[/SIZE][/FONT]
[FONT=courier new][SIZE=1]  File "/usr/lib/python2.7/dist-packages/httplib2/socks.py", line 424, in connect[/SIZE][/FONT]
[FONT=courier new][SIZE=1]    self.__negotiatehttp(destpair[0], destpair[1])[/SIZE][/FONT]
[FONT=courier new][SIZE=1]  File "/usr/lib/python2.7/dist-packages/httplib2/socks.py", line 374, in __negotiatehttp[/SIZE][/FONT]
[FONT=courier new][SIZE=1]    resp = self.recv(1)[/SIZE][/FONT]
[FONT=courier new][SIZE=1]KeyboardInterrupt[/SIZE][/FONT]

```


Connectivity wise, all the services are on the same LAN and we can ping/ssh to all nodes. Some troubleshooting logs:


```
[FONT=courier new][SIZE=1]ubuntu@juju-machine-13-lxc-4:~$ cat /var/log/neutron/server.log | grep WARNING[/SIZE][/FONT]
[FONT=courier new][SIZE=1]<snip>[/SIZE][/FONT]
[FONT=courier new][SIZE=1]2015-05-12 04:21:47.680 32427 WARNING neutron.openstack.common.db.sqlalchemy.session [-] This application has not enabled MySQL traditional mode, which means silent data corruption may occur. Please encourage the application developers to enable this mode.[/SIZE][/FONT]
[FONT=courier new][SIZE=1]2015-05-12 04:21:48.386 32427 WARNING neutron.api.extensions [req-42b7d5c5-813d-470d-9a06-21e675c78ae5 None] Extension allowed-address-pairs not supported by any of loaded plugins[/SIZE][/FONT]
[FONT=courier new][SIZE=1]2015-05-12 04:21:48.398 32427 WARNING neutron.api.extensions [req-42b7d5c5-813d-470d-9a06-21e675c78ae5 None] Extension flavor not supported by any of loaded plugins[/SIZE][/FONT]
[FONT=courier new][SIZE=1]2015-05-12 04:21:48.415 32427 WARNING neutron.api.extensions [req-42b7d5c5-813d-470d-9a06-21e675c78ae5 None] Extension port-security not supported by any of loaded plugins[/SIZE][/FONT]
[FONT=courier new][SIZE=1]2015-05-12 04:21:48.419 32427 WARNING neutron.api.extensions [req-42b7d5c5-813d-470d-9a06-21e675c78ae5 None] Extension routed-service-insertion not supported by any of loaded plugins[/SIZE][/FONT]
[FONT=courier new][SIZE=1]2015-05-12 04:21:48.420 32427 WARNING neutron.api.extensions [req-42b7d5c5-813d-470d-9a06-21e675c78ae5 None] Extension router-service-type not supported by any of loaded plugins[/SIZE][/FONT]
[FONT=courier new][SIZE=1]2015-05-12 04:21:48.424 32427 WARNING neutron.api.extensions [req-42b7d5c5-813d-470d-9a06-21e675c78ae5 None] Extension security-group not supported by any of loaded plugins[/SIZE][/FONT]
[FONT=courier new][SIZE=1]2015-05-12 04:21:48.461 32427 WARNING keystoneclient.middleware.auth_token [-] Configuring auth_uri to point to the public identity endpoint is required; clients may not be able to authenticate against an admin endpoint[/SIZE][/FONT]

```



Neutron config:


```
[FONT=courier new][SIZE=1]ubuntu@juju-machine-13-lxc-4:~$ sudo cat /etc/neutron/neutron.conf[/SIZE][/FONT]
[FONT=courier new][SIZE=1]# icehouse[/SIZE][/FONT]
[FONT=courier new][SIZE=1]###############################################################################[/SIZE][/FONT]
[FONT=courier new][SIZE=1]# [ WARNING ][/SIZE][/FONT]
[FONT=courier new][SIZE=1]# Configuration file maintained by Juju. Local changes may be overwritten.[/SIZE][/FONT]
[FONT=courier new][SIZE=1]## Restart trigger None[/SIZE][/FONT]
[FONT=courier new][SIZE=1]###############################################################################[/SIZE][/FONT]
[FONT=courier new][SIZE=1]<snip>[/SIZE][/FONT]
[FONT=courier new][SIZE=1][keystone_authtoken][/SIZE][/FONT]
[FONT=courier new][SIZE=1]signing_dir = /var/cache/neutron[/SIZE][/FONT]
[FONT=courier new][SIZE=1]service_protocol = http[/SIZE][/FONT]
[FONT=courier new][SIZE=1]service_host = 10.0.0.21[/SIZE][/FONT]
[FONT=courier new][SIZE=1]service_port = 5000[/SIZE][/FONT]
[FONT=courier new][SIZE=1]auth_host = 10.0.0.21[/SIZE][/FONT]
[FONT=courier new][SIZE=1]auth_port = 35357[/SIZE][/FONT]
[FONT=courier new][SIZE=1]auth_protocol =  http[/SIZE][/FONT]
[FONT=courier new][SIZE=1]admin_tenant_name = services[/SIZE][/FONT]
[FONT=courier new][SIZE=1]admin_user = quantum[/SIZE][/FONT]
[FONT=courier new][SIZE=1]admin_password = GY4BYj8M5Rx3FymxkJzMmbHcnVBTsxMG35nBJpN8VRcx3zxMbx6F4tBNbL4jTwyP[/SIZE][/FONT]
[FONT=courier new][SIZE=1][database][/SIZE][/FONT]
[FONT=courier new][SIZE=1]connection = mysql://neutron:h5rMNq6qbCx6hVhPWFPWHPNpZRNTnGbk@10.0.0.18/neutron[/SIZE][/FONT]
[FONT=courier new][SIZE=1]max_pool_size = 256[/SIZE][/FONT]

```



We noticed we didn&#8217;t have auth_uri on api-paste.ini


```
[SIZE=1][FONT=courier new]ubuntu@juju-machine-13-lxc-4:~$ sudo cat /etc/neutron/api-paste.ini[/FONT][/SIZE]
[SIZE=1][FONT=courier new]<snip>[/FONT][/SIZE]
[SIZE=1][FONT=courier new]
[/FONT][/SIZE]
[SIZE=1][FONT=courier new][filter:authtoken][/FONT][/SIZE]
[SIZE=1][FONT=courier new]paste.filter_factory = keystoneclient.middleware.auth_token:filter_factory[/FONT][/SIZE]

```


So we added to api-paste.ini the following, which cleared the auth_uri warning.


```
[FONT=courier new][SIZE=1]auth_host = 10.0.0.21[/SIZE][/FONT]
[FONT=courier new][SIZE=1]auth_uri = [http://10.0.0.21:5000/v2.0](http://10.0.0.21:5000/v2.0)[/SIZE][/FONT]
[FONT=courier new][SIZE=1]admin_tenant_name = services[/SIZE][/FONT]
[FONT=courier new][SIZE=1]admin_user = quantum[/SIZE][/FONT]
[FONT=courier new][SIZE=1]admin_password = GY4BYj8M5Rx3FymxkJzMmbHcnVBTsxMG35nBJpN8VRcx3zxMbx6F4tBNbL4jTwyP[/SIZE][/FONT]

```



On Horizon we initially had the following Network Agents:



[LIST]
[*]Open vSwitch agent
[/LIST]


We executed the following on Network node:


```
[FONT=courier new][SIZE=1]ubuntu@juju-machine-13-lxc-4:~$ **sudo apt-get install neutron-server neutron-dhcp-agent neutron-plugin-openvswitch-agent neutron-l3-agent**[/SIZE][/FONT]
[FONT=courier new][SIZE=1]Reading package lists&#8230; Done[/SIZE][/FONT]
[FONT=courier new][SIZE=1]<snip>[/SIZE][/FONT]

```


Which added some Network Agents:



[LIST]
[*]Open vSwitch agent
[*]Metadata agent
[*]DHCP agent
[/LIST]


But that didn&#8217;t clear the other warnings and we still don&#8217;t see L3 agent nor we can execute Neutron cli commands. Any clue?


We get same result with different charm combinations:


[LIST]
[*]quantum-gateway charm and setting network-manager as Neutron when running the nova-cloud-controller
[*]neutron-api and neutron-openvswitch charms with and without network-manager as Neutron when running the nova-cloud-controller
[/LIST]


Thanks

---

