---
title: "Ethenet cable not being recognized, though live"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by daggerx on 2012-02-29
Running 12.04 Alpha 2 and so far so good. The only problem that I have is that my gigabit network Ethernet cable is not being recognized (its plugged in and live) and under W7 – it is being recognized and is active. My network stuff if faded but my wireless is flawless. Please advise as to how I can fix my Ethernet so it can be seen. Thanks.

---

### Post by daggerx on 2012-02-29
Can anyone assist?

---

### Post by praseodym on 2012-02-29
Please show the outputs of:

> lspci -nnk | grep -iA2 net
lsmod

---

### Post by Iowan on 2012-02-29
Moved to Ubuntu +1 (Precise Pangolin) subforum.

---

### Post by ventrical on 2012-03-01
> **daggerx said:**
> Can anyone assist?

What happens to me from time to time is that I experiment with some PCs and I'll notice that if I have a seperate ethernet card and an onboard ethernet that is disabled , the ethertnet card will not be recognised. So, conversely, I will actually have to enable the onboard LAN in CMOS. Also. in contradistinction , the LAN option can be disabled also. I think it may be a bug with the networking and have seen it a few times now on different mach9ines , older and newer alike.

---

