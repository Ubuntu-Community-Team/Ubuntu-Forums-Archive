---
title: "Kernel mismatch between uname and apt-get?"
date: 2012-10-19
forum: Server Platforms
---

### Post by BelJoost on 2012-10-19
I wonder if it is safe to upgrade?

My situation is the following.

After SSHing to my ubuntu server 10.04.4 LTS it says:
> 18 packages can be updated.

So to check what packages can be upgraded I issue:
```
sudo apt-get -s upgrade
```

And it tells me (I left out other packages):
> The following packages will be upgraded:
  [...] linux-headers-2.6.32-41 linux-headers-2.6.32-41-server linux-image-2.6.32-41-server [...]

But when I check what kernel I am running by issuing:
```
uname -rmi
```

It tells me:
> 2.6.32-44-server x86_64 unknown

---

