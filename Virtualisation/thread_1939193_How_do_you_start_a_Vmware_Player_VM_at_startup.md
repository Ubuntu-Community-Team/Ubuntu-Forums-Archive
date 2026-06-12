---
title: "How do you start a Vmware Player VM at startup?"
date: 2012-03-11
forum: Virtualisation
---

### Post by WongFuChu on 2012-03-11
I tried adding:

```
vmplayer '/home/user/path/to/vm'
```to startup applications, but it doesn't work. Any ideas?

---

### Post by dcstar on 2012-03-12
> **WongFuChu said:**
> I tried adding:

```
vmplayer '/home/user/path/to/vm'
```to startup applications, but it doesn't work. Any ideas?

You need the full path to the .vmx file, for example:

```
vmplayer /home/dc/vmware/Vista/filename.vmx
```

---

