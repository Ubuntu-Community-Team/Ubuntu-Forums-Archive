---
title: "bind reverse dns problem.."
date: 2007-08-18
forum: Server Platforms
---

### Post by Underpants on 2007-08-18
```

$TTL    604800
@ IN SOA rooter.aaron.lan. admin.aaron.lan. (
                2006081401;
                28800;
                604800;
                604800;
                86400
)

                IN      NS      localhost.

1               IN      PTR     aaron.lan
11              IN      PTR     boxen.aaron.lan
10              IN      PTR     bluebox.aaron.lan

```

That is my reverse zone file. 
When I do an nslookup to 10.10.1.11 I get the following back
```
11.1.10.10.in-addr.arpa name = boxen.aaron.lan.**1.10.10.in-addr.arpa.**
```

Why is it giving me extra stuff, in the bold? what's wrong with my file?

---

### Post by erito on 2007-08-19
Try something like this and see if it works:
@ IN SOA rooter.aaron.lan. admin.aaron.lan. (
                2006081401; serial-no
                28800; refresh
                604800; retry
                604800; expiry
                86400 ); min-ttl
;

                IN      NS      localhost.;

1               IN      PTR     aaron.lan.
11              IN      PTR     boxen.aaron.lan.
10              IN      PTR     bluebox.aaron.lan.

I've never seens that error message before, but I see some syntax errors that might cause some problems.

---

### Post by Mr. C. on 2007-08-20
> **Underpants said:**
> ```

1               IN      PTR     aaron.lan
11              IN      PTR     boxen.aaron.lan
10              IN      PTR     bluebox.aaron.lan

```

Host names here must end with a dot, as in :

> **Underpants said:**
> ```

1               IN      PTR     aaron.lan.
11              IN      PTR     boxen.aaron.lan.
10              IN      PTR     bluebox.aaron.lan.

```

or the default zone will be added.

MrC

---

