---
title: "Fail to attach CDWriter"
date: 2010-02-19
forum: Virtualisation
---

### Post by satimis on 2010-02-19
Hi folks


KVM
Host - Fedora 12 64bit
VM (guest) - Windows Server 2008 64bit


Fail to attach CDWriter.


$ sudo virsh -c qemu:///system start vm06_wser08```

Domain vm06_wser08 started
```


$ cat VM/DEV/cd.xml ```

<disk type="block" device="cdrom">
<target dev="hdc" bus="ide"/>
<readonly/>
<source dev="/dev/sr0"/>
</disk>

```


$ sudo virsh attach-device vm06_wser08 VM/DEV/cd.xml```

error: Failed to attach device from VM/DEV/cd.xml
error: server closed connection

```


$ sudo tail /var/log/messages```

Feb 19 15:45:36 localhost kernel: br0: port 2(vnet0) entering forwarding state
Feb 19 15:48:31 localhost libvirtd: 15:48:31.574: error : qemudDomainChangeEjectableMedia:5186 : internal error No device with bus 'ide' and target 'hdc'
Feb 19 15:48:31 localhost kernel: libvirtd[1738]: segfault at 70 ip 00000000004367e2 sp 00007f210acfc8f0 error 4 in libvirtd[400000+7f000]
Feb 19 15:48:31 localhost abrtd: Directory 'ccpp-1266565711-1639' creation detected
Feb 19 15:48:31 localhost abrtd: Lock file '/var/cache/abrt/ccpp-1266565711-1639.lock' is locked by process 21223
Feb 19 15:48:32 localhost abrtd: Lock file '/var/cache/abrt/ccpp-1266565711-1639.lock' is locked by process 21223
Feb 19 15:48:33 localhost abrt[21223]: saved core dump of pid 1639 (/usr/sbin/libvirtd) to /var/cache/abrt/ccpp-1266565711-1639/coredump (60129280 bytes)
Feb 19 15:48:33 localhost abrtd: Getting local universal unique identification...
Feb 19 15:48:33 localhost abrtd: New crash, saving
Feb 19 15:48:33 localhost abrtd: RunApp('/var/cache/abrt/ccpp-1266565711-1639','test x"`cat component`" = x"xorg-x11-server-Xorg" && cp /var/log/Xorg.0.log .')

```



If I put following content on vm06_wser08 ; (cd.xml)```

<disk type="block" device="cdrom">
<target dev="hdc" bus="ide"/>
<readonly/>
<source dev="/dev/sr0"/>
</disk>

```


Then it works.  CDWriter can be attached to Vista.  But I must insert the CD on the drive before starting vm06_wser08.  Otherwises it complain.


Please help.  TIA


B.R.
Stephen L

---

