---
title: "Trying to install Ubuntu 11.10 Daily in KVM, possible bug?"
date: 2011-08-09
forum: Server Platforms
---

### Post by PyrexKidd on 2011-08-09
Hello,

I am trying to install 11.10 Daily Build (Server and desktop) in a virtual qemu/kvm environment.

I am receiving the following error:

```

trap divide error ip:7fc7885e94ee sp:7fff936b306 error:0 in libapt-pkg.so.4.11.0[7fc788577000+114000]

```

(I have attached the full output from cat /var/log/syslog as screen shots below, unfortunately as tehy are VM's I cannot copy/paste/upload the error log.)

This is how I created/launched my server
```

# qemu-img create -f qcow2 ./ubuntu-server-11.10-daily_build-x86_64.qcow2 50G

Formatting './ubuntu-server-11.10-daily_build-x86_64.qcow2', fmt=qcow2 size=53687091200 encryption=off cluster_size=0

# qemu-system-x86_64 -hda ./ubuntu-server-11.10-daily_build-x86_64.qcow2 -boot d -cdrom /home/user/Downloads/oneiric-server-amd64.iso

```

This is how I created/launched my desktop version.
```

# qemu-img create -f qcow2 ./ubuntu-desktop-11.10-daily_build-x86_64.qcow2 50G

Formatting './ubuntu-desktop-11.10-daily_build-x86_64.qcow2', fmt=qcow2 size=53687091200 encryption=off cluster_size=0

# qemu-system-x86_64 -hda ./ubuntu-deskt-11.10-daily_build-x86_64.qcow2 -boot d -cdrom /home/user/Downloads/oneiric-alternate-amd64.iso -m 2048 &

```

Not sure if I should report this as a bug or if there is an issue with the way I am trying to initialize my KVM.  For the record this works with 11.04 server and I have not tried 11.04 Desktop.

Thoughts?

Thanks.

---

