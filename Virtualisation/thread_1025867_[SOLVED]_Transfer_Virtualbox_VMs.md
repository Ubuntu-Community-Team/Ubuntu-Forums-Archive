---
title: "[SOLVED] Transfer Virtualbox VMs"
date: 2008-12-30
forum: Virtualisation
---

### Post by celtic426 on 2008-12-30
If it possible to transfer a virtual machine from virtualbox from one OS to another OS on my computer? Thanks.

---

### Post by HotShotDJ on 2008-12-30
> **celtic426 said:**
> If it possible to transfer a virtual machine from virtualbox from one OS to another OS on my computer? Thanks.Are you talking about copying the VDI from one computer (that, for example, is running Ubuntu) to another (that, for example, is running Windows)?  This should be possible.  Give a try and see what happens, although I can see no reason why this should be a problem.

---

### Post by howefield on 2008-12-30
Yes you can, if you mean can you have VirtualBox installed on two computers (doesn't matter what operating system they are running) and use a copy of the VM that you installed on one of them.

Use the clonevdi option to copy the VM eg.

```
VBoxManage clonevdi source destination
```

---

### Post by thomasr on 2008-12-30
When just copying the vdi file, it almost always gets corrupted. The clone vdi works, but there is another way. Zip, tar or rar it, copy  the compressed file to the new computer and uncompress it. Then follow the steps in the manual to create a new vm using an existing vdi.

---

### Post by howefield on 2008-12-31
That's interesting, I'll need to try that.

---

### Post by celtic426 on 2009-01-04
Thanks guys.

---

