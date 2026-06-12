---
title: "OpenStack - Horizon Internal Server Error"
date: 2013-03-13
forum: Server Platforms
---

### Post by slice16 on 2013-03-13
Hello All,

I am in the process of installing Openstack on Ubuntu Server 12.04 and am up to the final stage to configure the horizon web front end. When I go to http://<myserver>/horizon and log in with my admin account (which is configured in Keystone), I get an Internal Server Error. 

I am not sure where to start troubleshooting this, as their doesn't seem to be an openstack-dashboard error logs. Apache logs also come up blank. 

I did find an article where is talks about /etc/openstack-dashboard/local_settings.py using 'Member' as the default role from keystone. I have created this role to no avail.

All my nova services are up and showing as healthy:

```
Binary           Host                                 Zone             Status     State Updated_At
nova-consoleauth ms-os01                              nova             enabled    :-)   2013-03-13 11:45:18
nova-cert        ms-os01                              nova             enabled    :-)   2013-03-13 11:45:18
nova-scheduler   ms-os01                              nova             enabled    :-)   2013-03-13 11:45:14
nova-compute     ms-os01                              nova             enabled    :-)   2013-03-13 11:45:15
nova-network     ms-os01                              nova             enabled    :-)   2013-03-13 11:45:15
```

Any ideas would be welcome :)

Thanks in advance,

Paul

---

### Post by Vorteus on 2013-03-18
Hit the same wall trying to bring up openstack on 12.04 AND 12.10 using MASS and JuJu... 

in the node's /var/log/apache2/error.log found this...

[Sun Mar 17 23:36:34 2013] [notice] Apache/2.2.22 (Ubuntu) mod_wsgi/3.4 Python/2.7.3 configured -- resuming normal operations
[Mon Mar 18 03:37:52 2013] [error] unable to retrieve service catalog with token
[Mon Mar 18 03:37:52 2013] [error] Traceback (most recent call last):
[Mon Mar 18 03:37:52 2013] [error]   File "/usr/lib/python2.7/dist-packages/keystoneclient/v2_0/client.py", line 132, in _extract_service_catalog
[Mon Mar 18 03:37:52 2013] [error]     endpoint_type='adminURL')
[Mon Mar 18 03:37:52 2013] [error]   File "/usr/lib/python2.7/dist-packages/keystoneclient/service_catalog.py", line 62, in url_for
[Mon Mar 18 03:37:52 2013] [error]     raise exceptions.EndpointNotFound('Endpoint not found.')
[Mon Mar 18 03:37:52 2013] [error] EndpointNotFound: Endpoint not found.


[http://www.mail-archive.com/openstack@lists.launchpad.net/msg19659.html](http://www.mail-archive.com/openstack@lists.launchpad.net/msg19659.html)


This is apparently an unresolved and long-standing bug... has anyone found a workaround?

---

