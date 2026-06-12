---
title: "qcow encryption question"
date: 2012-12-12
forum: Virtualisation
---

### Post by ghat on 2012-12-12
hi

I wrote this up in a domain.xml

```

    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/vol/libvirt/images/fvg.qcow2'/>
      <target dev='hda' bus='ide'/>
      <encryption format='qcow'>
        <secret type='passphrase' uuid='855349dd-3c9b-4943-81aa-6d7fd2a9920b'/>
      </encryption>
    </disk>

```

What is the equivalent of that to use with a virt-install command ?

The qcow secrets etc are all setup already.. I can setup a domain.xml and start the domain, have it boot to a install cdrom etc, but I want to know how one can do the same thing with virt-install

G

---

