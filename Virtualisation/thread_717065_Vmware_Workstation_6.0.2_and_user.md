---
title: "Vmware Workstation 6.0.2 and user"
date: 2008-03-06
forum: Virtualisation
---

### Post by Koybe on 2008-03-06
Hello, 

I just download the evaluation version of Vmware Workstation. It's well installed using the kernel headers. Anyway, now I can only run it using sudo. I can't use it (or even the player installed) as a user.

```

~$ vmware
/bin/sh: Can't open /usr/bin/vmware
~$ ls -l /usr/bin/vmware
-r-xr-x--x 1 root root 4575 2008-03-06 22:14 /usr/bin/vmware

```

And even if i give everyone the read permission it won't help.

Any idea?

---

### Post by fjgaude on 2008-03-06
I guess you can change the permissions:

```
sudo chmod 644 /usr/bin/vmware
```

```
sudo chown loginname:loginname /usr/bin/vmware
```

Or you could run Nautilus in root:

```
gksudo nautilus
```

Then go to /usr/bin/vmware and use permissions to change from whatever it is now to your login name.

Let us know how you are doing.

---

### Post by Koybe on 2008-03-07
> **Koybe said:**
> ]And even if i give everyone the read permission it won't help.

Hello, as I said before, it won't help :
```
~$ sudo chmod 755 /usr/bin/vmware
:~$ vmware
/bin/sh: Can't open /usr/lib/vmware/lib/wrapper-gtk24.sh
```I'm going trough a permission hell and I'm quite sure it's not the good way to go.

And yes it works fine as root but I don't want to.

Thanks.

---

