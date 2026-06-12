---
title: "CAn I block myspace....."
date: 2007-08-17
forum: Ubuntu Christian Edition
---

### Post by ginnie6 on 2007-08-17
using dansguardian? I've just started using this and am not sure if it can do it? Thanks!

---

### Post by 1/0 on 2007-08-17
I would probably just add it to the hosts file.

```
sudo echo '127.0.0.1 myspace.com' >> /etc/hosts
```

---

### Post by 1/0 on 2007-08-17
I think this could work if you really want to use dansguardian. (Not using it myself.)

```
grep -r -i "myspace.com" /etc/dansguardian/lists/blacklists

```

---

### Post by raijinsetsu on 2007-08-17
> **1/0 said:**
> I would probably just add it to the hosts file.

```
sudo echo '127.0.0.1 myspace.com' >> /etc/hosts
```

That's dirty. Whenever someone attempted to access myspace.com, they'd get the matching service, if any, on the localhost. I wouldn't suggest doing this.

---

### Post by 1/0 on 2007-08-17
Change it to 127.0.0.2 then...

---

