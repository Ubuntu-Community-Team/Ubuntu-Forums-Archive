---
title: "Openstack installation - Identity service"
date: 2015-02-14
forum: Server Platforms
---

### Post by David_Barman on 2015-02-14
I am following the Ubuntu 14.04 OpenStack Installation Guide.
I have installed and configured the keystone service.  Created admin tenant, admin user, and the admin role.  I am to the point to verify the operation of the Identity service.
I execute the following command:
keystone --os-tenant-name admin --os-username admin --os-password <my password here> --os-auth-url [http://oscn:35357/v2.0](http://oscn:35357/v2.0) token-get
and I get the following message:

Authorization Failed: An unexpected error prevented the server from fulfilling your request. (HTTP 500)

If I run the command with the --debug parameter I get:

DEBUG:keystoneclient.auth.identity.v2:Making authentication request to [http://oscn:35357/v2.0/tokens](http://oscn:35357/v2.0/tokens)
INFO:urllib3.connectionpool:Starting new HTTP connection (1): oscn
DEBUG:urllib3.connectionpool:Setting read timeout to 600.0
DEBUG:urllib3.connectionpool:"POST /v2.0/tokens HTTP/1.1" 500 143
DEBUG:keystoneclient.session:Request returned failure status: 500
Authorization Failed: An unexpected error prevented the server from fulfilling your request. (HTTP 500)

I also tried to look at the keystone log, but I can't seem to do so.  First off the /var/log/keystone folder was not accessible (permission denied error)
So I chmod the folder to 777, and now I can get to the folder, but its empty.

So I don't know what is going on with the logs to get more info here.

I am really stuck, I have tried everything I can think of.  Any help would be GREATLY appreciated.

---

### Post by sebastien-jeannetot on 2015-08-21
Hello David

I have the exact same problem. Have you found a solution?

Thanks

---

### Post by sebastien-jeannetot on 2015-08-23
Can anyone help me? I let more information below:

When creating the identity endpoint following the guide [http://docs.openstack.org/juno/install-guide/install/apt/content/keystone-services.html](http://docs.openstack.org/juno/install-guide/install/apt/content/keystone-services.html), I get a "An unexpected error prevented the server from fulfilling your request. (HTTP 500)" error. My cloud design runs openstack (Juno) over 3 Virtual Machines (Ubuntu server 14.04), but at that point (keystone install and setup) I am only working on the controller node. 

    > openstack@controller:~$ more source.src 
    export OS_SERVICE_TOKEN=f000c6975f9c93d5cb5e
    export OS_SERVICE_ENDPOINT=http://controller:35357/v2.0
    openstack@controller:~$ source source.src 
    openstack@controller:~$ keystone --debug endpoint-create --service-id fcb0d0f94e19474fad673041534a902c --publicurl [http://controller:5000/v2.0](http://controller:5000/v2.0) --internalurl [http://controller:5000/v2.0](http://controller:5000/v2.0) --adminurl [http://controller:35357/v2.0](http://controller:35357/v2.0) --region nantes
    DEBUG:keystoneclient.session:REQ: curl -i -X GET [http://controller:35357/v2.0/OS-KSADM/services/fcb0d0f94e19474fad673041534a902c](http://controller:35357/v2.0/OS-KSADM/services/fcb0d0f94e19474fad673041534a902c) -H "User-Agent: python-keystoneclient" -H "X-Auth-Token: f000c6975f9c93d5cb5e"
    INFO:urllib3.connectionpool:Starting new HTTP connection (1): controller
    DEBUG:urllib3.connectionpool:Setting read timeout to 600.0
    DEBUG:urllib3.connectionpool:"GET /v2.0/OS-KSADM/services/fcb0d0f94e19474fad673041534a902c HTTP/1.1" 200 158
    DEBUG:keystoneclient.session:RESP: [200] {'date': 'Tue, 09 Jun 2015 20:42:02 GMT', 'vary': 'X-Auth-Token', 'content-length': '158', 'content-type': 'application/json', 'x-distribution': 'Ubuntu'} 
    RESP BODY: {"OS-KSADM:service": {"id": "fcb0d0f94e19474fad673041534a902c", "enabled": true, "type": "identity", "name": "keystone", "description": "OpenStack Identity"}}
    
    DEBUG:keystoneclient.session:REQ: curl -i -X POST [http://controller:35357/v2.0/endpoints](http://controller:35357/v2.0/endpoints) -H "User-Agent: python-keystoneclient" -H "Content-Type: application/json" -H "X-Auth-Token: f000c6975f9c93d5cb5e" -d '{"endpoint": {"adminurl": "http://controller:35357/v2.0", "service_id": "fcb0d0f94e19474fad673041534a902c", "region": "nantes", "internalurl": "http://controller:5000/v2.0", "publicurl": "http://controller:5000/v2.0"}}'
    INFO:urllib3.connectionpool:Starting new HTTP connection (1): controller
    DEBUG:urllib3.connectionpool:Setting read timeout to 600.0
    DEBUG:urllib3.connectionpool:"POST /v2.0/endpoints HTTP/1.1" 500 143
    DEBUG:keystoneclient.session:RESP:
    DEBUG:keystoneclient.session:Request returned failure status: 500
    An unexpected error prevented the server from fulfilling your request. (HTTP 500)
    openstack@controller:~$ 
    openstack@controller:~$ 
    openstack@controller:~$ netstat -an | grep -i listen
    tcp        0      0 10.0.2.15:3306          0.0.0.0:*               LISTEN     
    tcp        0      0 127.0.0.1:11211         0.0.0.0:*               LISTEN     
    tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN     
    tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
    tcp        0      0 0.0.0.0:35357           0.0.0.0:*               LISTEN     
    tcp        0      0 0.0.0.0:5000            0.0.0.0:*               LISTEN     
    tcp6       0      0 :::80                   :::*                    LISTEN     
    tcp6       0      0 :::22                   :::*                    LISTEN     
    unix  2      [ ACC ]     STREAM     LISTENING     11817    /var/run/libvirt/libvirt-sock
    unix  2      [ ACC ]     STREAM     LISTENING     11819    /var/run/libvirt/libvirt-sock-ro
    unix  2      [ ACC ]     STREAM     LISTENING     9263     /var/run/dbus/system_bus_socket
    unix  2      [ ACC ]     STREAM     LISTENING     8269     @/com/ubuntu/upstart
    unix  2      [ ACC ]     STREAM     LISTENING     11913    /var/run/mysqld/mysqld.sock
    unix  2      [ ACC ]     SEQPACKET  LISTENING     8584     /run/udev/control
    unix  2      [ ACC ]     STREAM     LISTENING     9822     @ISCSIADM_ABSTRACT_NAMESPACE
    unix  2      [ ACC ]     STREAM     LISTENING     10441    /var/run/acpid.socket
    
    openstack@controller:~$ more /var/log/keystone/keystone.conf
    /var/log/keystone/keystone.conf: Permission non accordée
    openstack@controller:~$ sudo more /var/log/keystone/keystone.conf
    /var/log/keystone/keystone.conf: Aucun fichier ou dossier de ce type
    openstack@controller:~$ sudo cat /var/log/keystone/keystone.conf
    cat: /var/log/keystone/keystone.conf: Aucun fichier ou dossier de ce type
    openstack@controller:~$ sudo ls /var/log/keystone/
    openstack@controller:~$ 
    
    
    openstack@controller:~$ dmesg | tail
    [   20.757621] init: mongodb main process (1168) terminated with status 100
    [   23.891161] Ebtables v2.0 registered
    [   24.085109] ip_tables: (C) 2000-2006 Netfilter Core Team
    [   24.184411] ip6_tables: (C) 2000-2006 Netfilter Core Team
    [   32.976051] init: plymouth-upstart-bridge main process (150) killed by TERM signal
    [   45.127989] Bridge firewalling registered
    [   45.297645] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
    [   45.345844] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
    [   57.975301] cgroup: systemd-logind (652) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
    [   57.975304] cgroup: "memory" requires setting use_hierarchy to 1 on the root

I tried to uninstall/reinstall keystone with the commands sudo apt-get remove and sudo apt-get install.
Thank you in advance for your help.

---

### Post by sebastien-jeannetot on 2015-08-29
solved by launching manual sync of the db:

> openstack@controller:~$ keystone-manage db_sync
2015-08-29 18:50:59.560 3246 INFO migrate.versioning.api [-] 44 -> 45... 
2015-08-29 18:50:59.579 3246 INFO migrate.versioning.api [-] done
2015-08-29 18:50:59.580 3246 INFO migrate.versioning.api [-] 45 -> 46... 
2015-08-29 18:50:59.584 3246 INFO migrate.versioning.api [-] done
2015-08-29 18:50:59.584 3246 INFO migrate.versioning.api [-] 46 -> 47... 
[...]

---

