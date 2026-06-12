---
title: "Control xen vith virt-manager over ssh"
date: 2008-04-20
forum: Virtualisation
---

### Post by iler on 2008-04-20
Hi!

I have xen 3.2 succesfully running on my Ubuntu 8.04 RC server and now I'm trying to use xen with virt-manager over ssh. But when I try to connect to remote server I get this error in virt-manager:

```
Unable to open a connection to the libvirt management daemon.

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started

```

After that I installed those packages and some more packages to make sure that there isn't anything missing from my server. But still I get the same error every time. Here is some more details of the error:

```
Unable to open connection to hypervisor URI 'xen+ssh://192.168.1.5/':
<class 'libvirt.libvirtError'> virConnectOpenReadOnly() failed remoteDispatchClientRequest: internal error: library function returned error but did not set virterror
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 331, in _open_thread
    self.vmm = libvirt.openReadOnly(self.uri)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 144, in openReadOnly
    if ret is None:raise libvirtError('virConnectOpenReadOnly() failed')
libvirtError: virConnectOpenReadOnly() failed remoteDispatchClientRequest: internal error: library function returned error but did not set virterror

```

This is what I get with xm list on my server:
```
Name                                        ID   Mem VCPUs      State   Time(s)
Domain-0                                     0  3888     2     r-----    236.0

```

So anyone can tell me where's the problem?

---

### Post by iler on 2008-04-21
And another question. Does anyone have a working system with this kind of setup (virt-manager over ssh to another computer)? If you have a working system could you post what version of virt-manager and xen you have. Thanks!

---

### Post by Ares Drake on 2008-04-22
Hi there.

I get the same error on my local xen deamon. So it is probably not an ssh issue but rather a bug in virt-manager, I guess?

There is a bug report with our error at launchpad:
[https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/198957](https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/198957)

However the solution there (installing libvirt-bin) doesn't help me, still get the same error.

---

### Post by iler on 2008-04-23
So it seems that current version of virt-manager in hardy doesn't work at all or? I have tested it only to try remote management so can't say anything about local xen instances. Hopefully they get this fixed asap.

I posted my error to that bug report also. It's funny that it is stated as 'patched' and it still broken. Seems that no one didn't really see the real problem behind that bug.

---

### Post by Age_M on 2008-05-05
Hi,

actually, virt-manager is working here. Maybe you forgot to add your ssh-user to the libvirtd group on the Xen-Server, where libvirtd is running?

On the Xen-Server check:

```
groups <your-username-here>
... libvirtd ...
```

If the user is not in the libvirtd group just add him:
```
adduser <your-username-here> libvirtd
```

After this the ssh connection from your client-machine with virt-manager should work.

But I am experiencing another problem:
libvirtd is dying after a few seconds on the server. Maybe you could tell me if this happens at your machine too.

Thanks in advance
Age_M

---

### Post by Ares Drake on 2008-05-06
> **Age_M said:**
> Hi,

actually, virt-manager is working here. Maybe you forgot to add your ssh-user to the libvirtd group on the Xen-Server, where libvirtd is running?

On the Xen-Server check:

```
groups <your-username-here>
... libvirtd ...
```

If the user is not in the libvirtd group just add him:
```
adduser <your-username-here> libvirtd
```

After this the ssh connection from your client-machine with virt-manager should work.

But I am experiencing another problem:
libvirtd is dying after a few seconds on the server. Maybe you could tell me if this happens at your machine too.

Thanks in advance
Age_M

Thank you for your hint. However I am already a member of the group libvirtd. So it must be sth else...

Have a look here, I suppose it is this bug:

[https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/220985](https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/220985)

---

### Post by fyzix on 2008-05-20
Seems there are still problems.

```
$ virsh -c xen://system list
connecting to uri:xen://system
libvir: Remote error: cannot access CA certificate '/etc/pki/CA/cacert.pem':no such file or directory(2)
error: failed to connect to the hypervisor
```

---

### Post by Droc on 2008-06-01
Well, I think you're just missing a slash there:

```

% virsh -c qemu:///system list
Connecting to uri: qemu:///system
 Id Name                 State
----------------------------------

% virsh -c qemu://system list 
Connecting to uri: qemu://system
libvir: Remote error : Cannot access CA certificate '/etc/pki/CA/cacert.pem': No such file or directory (2)
error: failed to connect to the hypervisor


```

---

### Post by Wonderbird on 2008-07-30
Thanks...  That worked for me...  (Don't know how I missed that third slash...)

---

