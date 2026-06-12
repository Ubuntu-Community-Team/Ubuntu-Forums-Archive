---
title: "Unable to migrate images! &quot;monitor socket did not show up.: connection refused&quot;"
date: 2011-06-24
forum: Virtualisation
---

### Post by uidzer0 on 2011-06-24
Hey everyone,

I've just setup an additional virtual machine server, running 10.04LTS. I'm attempting to migrate some of the guests from the old server to the new server via the virtual machine manager (virt-manager). When I run migration I get the error:

```
monitor socket did not show up.: Connection refused

```
Details->
```
Unable to migrate guest:
 Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/migrate.py", line 453, in _async_migrate
    vm.migrate(dstconn, migrate_uri, rate, live, secure)
  File "/usr/share/virt-manager/virtManager/domain.py", line 230, in migrate
    self._backend.migrate(destconn.vmm, flags, newname, interface, rate)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 429, in migrate
    if ret is None:raise libvirtError('virDomainMigrate() failed', dom=self)
libvirtError: monitor socket did not show up.: Connection refused

```

Has anyone else run into this problem? Or happen to know of another way to migrate (live) hosts to a new server?

Thanks!

---

### Post by uidzer0 on 2011-06-27
bump: nothing? has anyone ever been able to migrate a VM?

---

### Post by drahst on 2011-10-18
bump

Yeah... I'm getting this too...

---

### Post by ronnieredd on 2012-03-19
Me bumping too.
Another forum discusses changing the cd rom on the guest to be unhooked. My machine doesn't have one so, that's not fixing it...](*,)

---

### Post by ronnieredd on 2012-04-18
Bumping again
:confused:

---

