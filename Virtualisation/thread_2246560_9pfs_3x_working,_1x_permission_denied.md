---
title: "9pfs: 3x working, 1x permission denied"
date: 2014-10-01
forum: Virtualisation
---

### Post by sgofferj on 2014-10-01
So, I set up a new vm with (4) 9p shares...

```
    <filesystem type='mount' accessmode='mapped'>
      <source dir='/storage/exec'/>
      <target dir='exec'/>
      <readonly/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </filesystem>
    <filesystem type='mount' accessmode='mapped'>
      <source dir='/storage/asterisk/etc'/>
      <target dir='astetc'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </filesystem>
    <filesystem type='mount' accessmode='mapped'>
      <source dir='/storage/asterisk/lib'/>
      <target dir='astlib'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </filesystem>
    <filesystem type='mount' accessmode='mapped'>
      <source dir='/storage/asterisk/spool'/>
      <target dir='astspool'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </filesystem>
```

and mounted them in the guest...

```
astetc                                  /etc/asterisk           9p      trans=virtio,version=9p2000.L,rw    0   0
astlib                                  /var/lib/asterisk       9p      trans=virtio,version=9p2000.L,rw    0   0
astspool                                /var/spool/asterisk     9p      trans=virtio,version=9p2000.L,rw    0   0
exec                                    /exec                   9p      trans=virtio,version=9p2000.L,rw    0   0
```

And 3 work and the 4th (/var/lib/asterisk) gives me a "permission denied" for everything exept listing the directory. Any file access or listing subdirectories are denied.
Dir/file permissions on the host are ok. Nothing suspicious in the syslog. I'm pretty new to qemu, so I don't really know where to look for the problem.

---

