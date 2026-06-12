---
title: "vmware keyboard issues with UK layout"
date: 2009-11-01
forum: Server Platforms
---

### Post by nicolasdiogo on 2009-11-01
hi

i have vmware 2 installed on a ubuntu hardy 64 host, and i am having great difficulties in finding a solution the my problem with keyboard mapping on the guest OS (mainly ubuntu - but also windows).

i have searched for solutions and done the following.

added the following line to my /etc/vmware/config on the host
```

xkeymap.nokeycodeMap = true

```

and configure vmware server again
```

vmware-config.pl

```

i have also added the line to my local config (~/.vmware/config) on the client (machine connecting to host)
```

xkeymap.nokeycodeMap = true

```

but these steps did not solve the problem of mapping my keyboard correctly.
for example;
- my arrow keys do not work
- no insert, home, page up or down, etc..

i have found a number of solutions on the web but they seem to be focused on the general keyboard for US.

any assistance fixing the UK (and other) keyboard layouts on vmware 2 will be mostly appreciated.

thanks,

---

### Post by nicolasdiogo on 2009-11-03
Hello,

just bumping to see if there anyone who lend a hand here..

thanks

---

### Post by nicolasdiogo on 2009-11-10
bumping again..

---

### Post by netkom on 2009-11-10
Hi,

but your keyboards works fine in ubuntu hardy?

Cheers

---

### Post by nicolasdiogo on 2009-11-11
thanks,

but is your installation like?

could you post your /etc/vmware/config file here?

regards

---

