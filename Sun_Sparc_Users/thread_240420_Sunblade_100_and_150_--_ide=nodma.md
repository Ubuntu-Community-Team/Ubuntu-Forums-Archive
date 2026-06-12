---
title: "Sunblade 100 and 150 -- ide=nodma"
date: 2006-08-20
forum: Sun Sparc Users
---

### Post by Delta_Farce on 2006-08-20
Hi all,

It seems the advice I've been posting about adding the ide=nodma comment to the silo.conf file has been wrong, so I thought I'd post the correct way to do it here.

If you just edit /boot/silo.conf you will get errors on boot and have to manually boot your kernel, what you actually have to do is edit [COLOR="red"]/etc/silo.conf [/COLOR]and add the append="ide=nodma" line to each of your kernels.

```

image=/vmlinuz
        label=Linux
        [COLOR="Red"]append="ide=nodma"[/COLOR]
        initrd=/initrd.img
```

After editing that file, you can check that your silo.conf is valid by running:

```

# [COLOR="Blue"] /sbin/silo[/COLOR]
/etc/silo.conf appears to be valid
```

Then copy it to your /boot directory:

```
# [COLOR="blue"]cp /etc/silo.conf /boot[/COLOR]
```

And check the integrity again:

```

# [COLOR="blue"]/sbin/silo -C /boot/silo.conf[/COLOR]
/boot/silo.conf appears to be valid
```

After that, Ubuntu should load on a Sunblade without problems.

Cheers,

Mark

---

### Post by shoki on 2007-02-17
Thanks for the info. Very nice!

---

