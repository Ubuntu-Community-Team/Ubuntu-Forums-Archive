---
title: "List of services converted to Upstart"
date: 2010-04-30
forum: Server Platforms
---

### Post by frodemt on 2010-04-30
Hi.

Where can I find a list of services converted to upstart in Ubuntu 10.04? What is the syntax for stoping, starting and restarting these services?

---

### Post by cdenley on 2010-04-30
> **frodemt said:**
> 
Where can I find a list of services converted to upstart in Ubuntu 10.04? 

```

ls -1 /etc/init|cut -d . -f 1

```
> **frodemt said:**
> What is the syntax for stoping, starting and restarting these services?
```

man initctl

```

---

### Post by ghost_ryder35 on 2010-04-30
I am lazy so I still just run the init scripts manually from /etc/init.d/

---

### Post by pksings on 2010-04-30
service whatever stop
service whatever start
service whatever restart

will also work.

---

### Post by CharlesA on 2010-04-30
> **ghost_ryder35 said:**
> I am lazy so I still just run the init scripts manually from /etc/init.d/

Tried that for Samba, doesn't work since the init.d script was removed. Ended up using service smbd stop/start to get it going.

Same with dhcp3-server and ssh

---

### Post by cdenley on 2010-04-30
> **CharlesA said:**
> Tried that for Samba, doesn't work since the init.d script was removed. Ended up using service smbd stop/start to get it going.

Same with dhcp3-server and ssh

The samba init.d script wasn't removed. It was divided since smbd and nmbd are managed separately now.
```

ls /etc/init.d/?mbd

```

---

### Post by CharlesA on 2010-04-30
> **cdenley said:**
> The samba init.d script wasn't removed. It was divided since smbd and nmbd are managed separately now.
```

ls /etc/init.d/?mbd

```

Thanks. I didn't even notice that, probably because I am use to just using "samba" instead of smbd.

---

