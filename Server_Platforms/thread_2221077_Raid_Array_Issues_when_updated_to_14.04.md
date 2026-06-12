---
title: "Raid Array Issues when updated to 14.04"
date: 2014-04-30
forum: Server Platforms
---

### Post by Edward_Collinson on 2014-04-30
Hi, When I updated to Ubuntu Server 14.04
Whenever I try to bring up my raid1 array I get this error:

Error starting RAID array: Command-line `mdadm --assemble  --scan --uuid "512b8cd2:ef97bb8b:34d3cdef:4ec0cc58"' exited with non-zero exit status 2:  (udisks-error-quark, 0)

This is rather annoying. :(
How do I fix this? :confused:

~Ed

---

### Post by lukeiamyourfather on 2014-05-01
Try it without specifying the UUID.

```
 sudo mdadm --assemble --scan
```

---

### Post by Edward_Collinson on 2014-05-01
I tried that and it gives me this:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

~Ed

---

### Post by drfox on 2014-05-03
> **Edward_Collinson said:**
> I tried that and it gives me this:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

~Ed

I'm getting the identical "no talloc...c:4864,leaking memory" error toward the end of the boot up/os loading procedure.

---

### Post by Edward_Collinson on 2014-05-03
I didn't have that Issue, I mannaged to boot directly into the Ubuntu GUI and managed it from there. Did it just start doing it with the new update?
It could be a bug.

---

### Post by drfox on 2014-05-03
> **Edward_Collinson said:**
> I didn't have that Issue, I mannaged to boot directly into the Ubuntu GUI and managed it from there. Did it just start doing it with the new update?
It could be a bug.

I don't use a GUI, but yes, it started last night when I upgraded from Precise LTS to Trusty LTS server.

---

### Post by Edward_Collinson on 2014-05-03
Ok, I think it might just be a bug? Don't take my word for it. I am not particularly good with this type of thing :P
Sorry I can't help you too much :/

---

