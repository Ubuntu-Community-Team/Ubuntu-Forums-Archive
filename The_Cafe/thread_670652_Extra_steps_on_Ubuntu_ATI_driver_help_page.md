---
title: "Extra steps on Ubuntu ATI driver help page"
date: 2008-01-17
forum: The Cafe
---

### Post by Ozor Mox on 2008-01-17
I'm not sure whether this is the right place to put this but I thought it might help as I've just had to follow these steps myself.

On [this ATI driver installation guide](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a), there are some additional packages that need to be installed otherwise there are errors when creating the deb files that do not make it obvious that packages are missing. These are:

```
dpkg-dev
dh-make
```

I thought maybe someone might like to add this information to the page, as additional packages to:

```
sudo apt-get install dkms
```

---

### Post by bufsabre666 on 2008-01-17
i always advise to people, use envy, it always works perfect for me

---

### Post by Ozor Mox on 2008-01-17
> i always advise to people, use envy, it always works perfect for  me

It does indeed, and it's a much easier solution as I've found out, but I thought it might be nice to correct the information there anyway :)

---

### Post by bufsabre666 on 2008-01-17
> **Ozor Mox said:**
> It does indeed, and it's a much easier solution as I've found out, but I thought it might be nice to correct the information there anyway :)

indeed my friend

---

