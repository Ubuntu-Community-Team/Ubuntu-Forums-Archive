---
title: "Accessing webserver on Guest OS using bridged wireless?"
date: 2011-02-13
forum: Virtualisation
---

### Post by khughitt on 2011-02-13
Hi all,

I've been trying to figure out how to open up access to a web server, or any other ports for that matter, running on a Guest OS. I've seen several different solutions out there (e.g. port forwarding, using host-only or bridged adapter), but so far none have worked for me.

The host machine is Ubuntu 9.04 desktop, and the guest machine is Ubuntu 10.10 server.

Has anyone had luck with this on a wireless network connection?

Thanks,

---

### Post by CharlesA on 2011-02-13
Post the output of this please (when run from the guest):

```
ifconfig -a
```

---

### Post by khughitt on 2011-02-14
Hi CharlesA,

Only the loopback interface shows up:

```

lo Link encap: Local Loopback
   inet addr: 127.0.0.1 Mask 255.0.0.0
   ...

```

For the Virtualbox network adaptors section for the Guest OS I'm currently using the PCnet-FAST III adapter, however, I've tried most of the others and none seemed to work.

---

### Post by CharlesA on 2011-02-14
Try using the Intel Pro/1000 MT Desktop network card.

That's what my Linux guests are using.

---

### Post by khughitt on 2011-02-16
Same result. Is your host machine connected over Wifi? I suspect that this might be the issue.

---

### Post by mciverza on 2011-02-16
> **pwnedd said:**
> Hi all,


Has anyone had luck with this on a wireless network connection?

Thanks,

Bridged networking is NOT possible with a wireless link. only with a lan cable connected link. (AFAIK)

I suggest you plug directly into a switch, change the Virtual Machine to used bridged adaptor eth0 and see if that doesn't solve your problems.

---

### Post by CharlesA on 2011-02-16
> **pwnedd said:**
> Same result. Is your host machine connected over Wifi? I suspect that this might be the issue.
Mine is hardwired, not wireless.

---

### Post by howefield on 2011-02-16
> **mciverza said:**
> Bridged networking is NOT possible with a wireless link. only with a lan cable connected link. (AFAIK)

I believe bridged networking is very possible over wireless, at least since about version 3.0 of VirtualBox.

---

### Post by CharlesA on 2011-02-16
I think I've done it over wireless before, but it's been a while, since my netbook can't really handle running a Virtual Machine. Heh.

---

### Post by dinusuresh on 2011-11-25
hi pwnedd, i was having the same problem as you were. I tried all possible ways to access my guest web server on my host but it didn't work for some reason though i did have my eth0 show up with an address of 10.0.2.15.
Anyways, i don't want to prolong with the same story. I tried port-forwarding my port 80 and bingo!!!
I have attached a pic of the configuration i tried. Hope it works for you too buddy :)

---

