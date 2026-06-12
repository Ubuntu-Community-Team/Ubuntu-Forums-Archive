---
title: "MAAS and JUJU restore a backup - state server"
date: 2015-12-02
forum: Ubuntu Cloud and Juju
---

### Post by Marco_Mezzaro on 2015-12-02
Hi all,

I have 4 servers in a MAAS environment. I've bootstrapped a juju env. and done my first backup with " juju backups create ". backup completed with no errors.
actually I am in testing phase so I'm trying all common ops to manage maas and juju.
I cannot restore my backup as new state server.

```
# juju backups restore -b --file=juju-backup-20151202-161803.tar.gz -e maas
ERROR old bootstrap instance ["HOST01.maas:/MAAS/api/1.0/nodes/node-8c49a03e-8d54-11e5-80b4-0022199ab5bd/"] still seems to exist; will not replace
```

I create a new juju environment and try to restore my backup there.

```
# juju backups restore -b --file=juju-backup-20151202-161803.tar.gz -e maastest
ERROR cannot determine state server instances: environment is not bootstrapped

```


this is my environment.yaml

```
root@maas-srv:~# cat /root/.juju/environments.yaml 
environments:
  maas:
    type: maas
    maas-server: 'http://10.44.44.1:80/MAAS'
    maas-oauth: 'MAAS-API-KEY'
    admin-secret: admin
    default-series: trusty

  maastest:
    type: maas
    maas-server: 'http://10.44.44.1:80/MAAS'
    maas-oauth: 'DIFFERENT-MAAS-API-KEY-DIFFERENT-MAAS-USER'
    admin-secret: admin
    default-series: trusty
```

I followed this manual page: [https://jujucharms.com/docs/stable/juju-backups](https://jujucharms.com/docs/stable/juju-backups)
in particular:
[B]In the case that the original state server no longer exists, it is possible to re-bootstrap the environment and restore the backup to the new state-server. To do this, use the '-b' switch
[/B]
but I've got all above errors.
at least, I've upgraded juju and maas to latest version: JUJU 1.26-alpha2-vivid-amd64; MAAS Version 1.8.3+bzr4053-0ubuntu1 (vivid1); pervious versions has the same problem.

Thank You for any help provided.

---

