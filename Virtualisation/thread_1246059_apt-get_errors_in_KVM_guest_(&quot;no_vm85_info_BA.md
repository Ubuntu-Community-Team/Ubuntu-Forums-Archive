---
title: "apt-get errors in KVM guest (&quot;no vm85_info: BAD&quot;)"
date: 2009-08-21
forum: Virtualisation
---

### Post by der_flo on 2009-08-21
Hello everybody,

i set up a fresh KVM guest and tried to ```
apt-get update
```But the output was:
```

Fetching:1 http://de.archive.ubuntu.com jaunty Release.gpg [189B]
E: Method http has died unexpectedly!

```dmesg shows:
```

http[1703]: segfault at 0 ip 00000000 sp bfc1487c error 14 in http[8048000+d000]
no vm86_info: BAD

```Does anybody have an idea what the problem could be?

Thanks,
der Flo

---

### Post by bdmc on 2009-08-23
This is almost exactly the problem that I am having too.

The "host" machine does not exhibit any of these symptoms, no segfaults in the kern.log, no failures in apt-get, none of the problems shown in all of the VMs.

The issues in the VMs are slightly intermittant, though.  apt-get update may be perfectly successful, but apt-get install fortune fails every time.

I have apt-proxy installed on the host, and all of the VMs look to that.  I have tried editing the sources.list file in VMs to refer to the "official" mirrors, with no change.  I have tried changing from HTTP to FTP mirrors with no change.

I have tried Jaunty and Intrepid guest OSs, no difference.


Does ANYBODY have any useful ideas?


Thanks,
Brian

---

### Post by jcdutton on 2009-09-28
Same problem here.
host is running a 32bit kernel on a 64bit capable system
The guest is running the same kernel as the host.

---

### Post by der_flo on 2009-10-02
My problems are gone - perhaps a kernel update?
Please check it.

---

### Post by __p1n__ on 2009-10-02
> **bdmc said:**
> Does ANYBODY have any useful ideas?


Try a better hypervisor and run those guest images in an HVM.

---

### Post by manasi on 2010-03-29
I am having exactly the same issue.
Did you manage to solve this issue?
how do i do a kernel upgrade when apt-get is not working ?
apt-get fails  with this error
E:Method http has died unexpectedly.
My network is fine I am able to ping the source.

---

### Post by der_flo on 2010-03-30
> **manasi said:**
> I am having exactly the same issue.
Did you manage to solve this issue?
how do i do a kernel upgrade when apt-get is not working ?
apt-get fails  with this error
E:Method http has died unexpectedly.
My network is fine I am able to ping the source.

I did an kernel upgrade in the host, not in the vm, but sorry, I'm not sure anymore.
Finally I went with Debian as host OS, which is quite more reliable.

Ciao,
der Flo

---

### Post by manasi on 2010-03-31
Thank you.
I will see if that works for me!

---

### Post by nutznboltz on 2010-04-02
Pre-Karmic virtio network driver had some issues which have been resolved.

[http://www.mail-archive.com/kvm@vger.kernel.org/msg21631.html](http://www.mail-archive.com/kvm@vger.kernel.org/msg21631.html)

---

