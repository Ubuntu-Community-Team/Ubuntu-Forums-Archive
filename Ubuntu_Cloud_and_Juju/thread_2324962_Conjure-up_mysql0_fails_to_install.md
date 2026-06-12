---
title: "Conjure-up mysql/0 fails to install"
date: 2016-05-17
forum: Ubuntu Cloud and Juju
---

### Post by Carey_Pillar on 2016-05-17
Anyone else having this issue 

Xenial 16.04LTS

Juju is deploying and mysql/0 fails to install

Logs say that dependencies are missing.  looks like looking for older 5.6 packages.  add trusty repos to souces list for this particular container.  see in logs that they pick up.  still no luck

mysql/0 still fails with hook failed: "install"

thanks in advance

CP

---

### Post by tom232 on 2016-05-19
> **Carey_Pillar said:**
> Anyone else having this issue 

Xenial 16.04LTS

Juju is deploying and mysql/0 fails to install

Logs say that dependencies are missing.  looks like looking for older 5.6 packages.  add trusty repos to souces list for this particular container.  see in logs that they pick up.  still no luck

mysql/0 still fails with hook failed: "install"

thanks in advance

CP

I just wanted to chime in that I am running into the same problem. Even with manually installing mysql-5.6 through the repos it continues to fail:

unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40 Traceback (most recent call last):
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/var/lib/juju/agents/unit-mysql-0/charm/hooks/install.real", line 686, in <module>
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     main()
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/var/lib/juju/agents/unit-mysql-0/charm/hooks/install.real", line 679, in main
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     hooks.execute(sys.argv)
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/var/lib/juju/agents/unit-mysql-0/charm/hooks/charmhelpers/core/hookenv.py", line 717, in execute
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     self._hooks[hook_name]()
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/var/lib/juju/agents/unit-mysql-0/charm/hooks/charmhelpers/contrib/hardening/harden.py", line 81, in _harden_inner2
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     return f(*args, **kwargs)
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/var/lib/juju/agents/unit-mysql-0/charm/hooks/install.real", line 119, in install
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     render_config()
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/var/lib/juju/agents/unit-mysql-0/charm/hooks/install.real", line 133, in render_config
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     'private_address': get_host_ip(),
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/var/lib/juju/agents/unit-mysql-0/charm/hooks/percona_utils.py", line 119, in get_host_ip
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     answers = dns.resolver.query(hostname, 'A')
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/usr/lib/python2.7/dist-packages/dns/resolver.py", line 981, in query
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     raise_on_no_answer, source_port)
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40   File "/usr/lib/python2.7/dist-packages/dns/resolver.py", line 910, in query
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40     raise NXDOMAIN
unit-mysql-0: 2016-05-19 14:41:44 INFO unit.mysql/0.install logger.go:40 dns.resolver.NXDOMAIN
unit-mysql-0: 2016-05-19 14:41:44 ERROR juju.worker.uniter.operation runhook.go:107 hook "install" failed: exit status 1
unit-mysql-0: 2016-05-19 14:41:44 INFO juju.worker.uniter resolver.go:107 awaiting error resolution for "install" hook
unit-mysql-0: 2016-05-19 14:41:51 INFO juju.worker.leadership tracker.go:182 mysql/0 will renew mysql leadership at 2016-05-19 14:42:21.221139329 +0000 UTC


It appears to be related to [https://bugs.launchpad.net/charms/+source/percona-cluster/+bug/1571789](https://bugs.launchpad.net/charms/+source/percona-cluster/+bug/1571789)

---

### Post by tom232 on 2016-05-19
So some time in IRC (thanks Ryan!) and here is the status.
There was a bug that was introduced when Ubuntu removed mysql 5.6 in the main repos which the mysql charm was relying on.
There was a quick patch made but it has not made it into the openstack-charmers-next channel yet.  There is an updated package in the works.

In the meantime cs:~openstack-charmers/xenial/percona-cluster-0 should be a working version.

---

