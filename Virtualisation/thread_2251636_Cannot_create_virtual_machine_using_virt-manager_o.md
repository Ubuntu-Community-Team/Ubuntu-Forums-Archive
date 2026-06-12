---
title: "Cannot create virtual machine using virt-manager on xen"
date: 2014-11-05
forum: Virtualisation
---

### Post by janucik-mikolaj on 2014-11-05
Hello, I want to create virtual machine using virt-manager on xen but after filling everything up virt-manager gives me 2 errors 
[COLOR=#333333]
[/COLOR]

```

Nie mo&#380;na uko&#324;czy&#263; instalacji: "End of file while reading data: B&#322;&#261;d wej&#347;cia/wyj&#347;cia"
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 96, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1983, in do_install
    guest.start_install(False, meter=meter)
  File "/usr/lib/python2.7/dist-packages/virtinst/Guest.py", line 1246, in start_install
    noboot)
  File "/usr/lib/python2.7/dist-packages/virtinst/Guest.py", line 1314, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3202, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: End of file while reading data: B&#322;&#261;d wej&#347;cia/wyj&#347;cia

```
"B&#322;&#261;d wej&#347;cia/wyj&#347;cia" means input/output error

and second error

```
B&#322;&#261;d podczas sonda&#380;u po&#322;&#261;czenia "xen:///": internal error: client socket is closed

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 296, in _tick
    conn.tick()
  File "/usr/share/virt-manager/virtManager/connection.py", line 1311, in tick
    self._tick(noStatsUpdate)
  File "/usr/share/virt-manager/virtManager/connection.py", line 1320, in _tick
    self.hostinfo = self.vmm.getInfo()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3344, in getInfo
    if ret is None: raise libvirtError ('virNodeGetInfo() failed', conn=self)
libvirtError: internal error: client socket is closed
```


I'm running ubuntu 14.04lts and xen 4.4.0
After stopping libvirt-bin service and starting it with libvirtd command it gives me this [http://pastebin.com/XuaMXReb](http://pastebin.com/XuaMXReb) and crashes.
Could somebody help me with this ?

---

### Post by TheFu on 2014-11-05
I don't have the answer, just a few questions which might help others to help you.
* is the virt-manager running on the same machine or a different machine?
* is the userid on the Xen host (Dom0) in the libvirtd group? (I ask because this is commonly missed)
* has this worked on this machine before?
* has this worked with other VMs before?

I did look thought the pastebin - thanks for that - didn't see anything clearly wrong. Sorry.

---

### Post by janucik-mikolaj on 2014-11-05
> **TheFu said:**
> [COLOR=#000000]* is the virt-manager running on the same machine or a different machine?[/COLOR]
The same machine
> **TheFu said:**
> [COLOR=#000000]* is the userid on the Xen host (Dom0) in the libvirtd group? (I ask because this is commonly missed)[/COLOR]
Yes, also tried running virt-manager as root with the same result
> **TheFu said:**
> [COLOR=#000000]* has this worked on this machine before?[/COLOR]
No, but I have succesfully started Xen virtual machine using xl utility
> **TheFu said:**
> [COLOR=#000000]* has this worked with other VMs before?[/COLOR]
Haven't tried

---

