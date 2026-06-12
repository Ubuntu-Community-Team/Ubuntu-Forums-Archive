---
title: "assign /dev/pts entry to virtual serial device with libvirt"
date: 2011-01-11
forum: Virtualisation
---

### Post by jpwalters on 2011-01-11
Hi,

I'm using Lucid 10.04 with libvirt version 0.8.3 and qemu version 0.13.0.  I want to assign a virtual serial device with one endpoint on the host and the other in the guest VM, and I want the host endpoint to be fixed.  To do that, I'm using the following entry in my VM's xml file:

```

<serial type='pty'>
     <source path='/dev/pts/19' />
     <target port='0' />
</serial>


```This does create the serial device, but it doesn't obey the /dev/pts/19 entry, instead choosing a somewhat arbitrary entry in /dev/pts.  Is it possible to fix the host device name, such as what I'm trying to do in the example above?

---

