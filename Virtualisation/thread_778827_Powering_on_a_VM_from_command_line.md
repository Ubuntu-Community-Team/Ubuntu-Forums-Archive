---
title: "Powering on a VM from command line"
date: 2008-05-02
forum: Virtualisation
---

### Post by TurboRush on 2008-05-02
Hello,

Been playing around with VMServer on Gutsy and currently have XP setup and Gutsy Server setup (so I can mess around with out doing any real damage :) ).

Anyway, I've found myself with some free time today but am remote. Is there a way to power on a Virtual machine from the command line? I'd like to fire up that server slice so I can SSH into it, but need to get it powered on from my remote location.

Thanks.

---

### Post by Kokopelli on 2008-05-02
```
vmware-cmd -v <config location> start
```

in the directory there is a vmx file which is the config for the vm.

so as an example

```
 vmware-cmd -v /var/lib/vmware/Virtual\ Machines/XPClean/XPClean.vmx start
```

will start my clean room XP image.

The -v is not strictly necessary (it is verbose mode).

```
vmware-cmd -v <config location> stop
```

will stop the VM.  There are additional options and commands as well.

[http://www.vmware.com/support/esx21/doc/vmware-cmd.html](http://www.vmware.com/support/esx21/doc/vmware-cmd.html)

should do if you are curious.

---

### Post by TurboRush on 2008-05-02
Works like a charm. One thing for others trying to attempt this... you either need to go into options and uncheck "make vm private" OR you'll need to issue your user name and password at the command line to make this work, i.e.,

```

vmware-cmd -v -H localhost -U user -P password /var/lib/vmware-server/Virtual\ Machines/Ubuntu/Ubuntu.vmx start
```

---

