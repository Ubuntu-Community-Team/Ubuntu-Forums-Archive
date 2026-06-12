---
title: "KVM: Problem creating VM with vmbuilder and bridged Network"
date: 2008-11-03
forum: Virtualisation
---

### Post by pred2k on 2008-11-03
Hi, i installed **Ubuntu 8.10 server** and choose the Package "Virtual Machine host". 
I installed the **python-vm-builder** to create a new VM based of the JeOS.

Because i wanted a bridged Network i changes the interface Element in /etc/vmbuilder/libvirt/libvirtxml.tmpl 
```
<interface type='bridge'>
   <source network='br0'/>
</interface>

```
.. and created a dhdcp br0 Interface in the /etc/network/interfaces

Then i executed my vmbuilder command:```
sudo vmbuilder kvm ubuntu --suite intrepid --flavour virtual --arch i386 -o --libvirt qemu:///system ...
```

and during creating the VM, following error appeared:
```
libvir: QEMU error : internal error No <source> 'dev' attribute specified with <interface type='bridge'/>
2008-11-01 17:25:58,925 INFO     Cleaning up
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 29, in <module>
    VMBuilder.run()
  File "/usr/lib/python2.5/site-packages/VMBuilder/__init__.py", line 66, in run
    frontend.run()
  File "/usr/lib/python2.5/site-packages/VMBuilder/plugins/cli/__init__.py", line 67, in run
    vm.create()
  File "/usr/lib/python2.5/site-packages/VMBuilder/vm.py", line 447, in create
    self.deploy()
  File "/usr/lib/python2.5/site-packages/VMBuilder/vm.py", line 177, in deploy
    if getattr(plugin, 'deploy')():
  File "/usr/lib/python2.5/site-packages/VMBuilder/plugins/libvirt/__init__.py", line 61, in deploy
    self.conn.defineXML(vmxml)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 866, in defineXML
    if ret is None:raise libvirtError('virDomainDefineXML() failed', conn=self)
libvirt.libvirtError: virDomainDefineXML() failed internal error No <source> 'dev' attribute specified with <interface type='bridge'/>
```

i don't know whats wrong, because i have a <source>-Element beflow the <interface>.

---

### Post by nknight on 2008-11-03
I just fought through this myself. The docs are in error, as is the error message given by vmbuilder. #-o

You need to replace this:

```

<interface type='bridge'>
   <source network='br0'/>
</interface>

```

With this:

```

<interface type='bridge'>
   <source bridge='br0'/>
</interface>

```

The error from vmbuilder really should have been "No <source> 'bridge' attribute[...]".

---

### Post by pred2k on 2008-11-03
> **nknight said:**
> You need to replace this:

...

With this:

```

<interface type='bridge'>
   <source bridge='br0'/>
</interface>

```

Yep, thats it! Thanks for that advice. =D>

Should be changed in the VMBuilder-howto asap.

---

