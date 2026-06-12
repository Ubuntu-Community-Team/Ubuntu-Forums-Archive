---
title: "virsh connect failed"
date: 2008-07-20
forum: Virtualisation
---

### Post by ktulu73 on 2008-07-20
Hi,

I have problems connecting via  virsh -c qemu+ssh:///192.168.2.190
to a remote host.
The curious thing is, that the connection via virt-manager work. I tried in both directions (have two hosts running). 
Also virsh -c qemu+ssh:///localhost failed with same error (connection to hypervisor failed).

Regards

---

### Post by ktulu73 on 2008-07-20
Ok,

I tried since yesterday................
Searched with google. 
It's so simple, on remote connection only two slashes!!!
So, with virsh -c qemu+ssh://192.168.2.190/system everything work.

:rolleyes:

---

