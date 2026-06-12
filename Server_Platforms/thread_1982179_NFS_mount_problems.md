---
title: "NFS mount problems"
date: 2012-05-18
forum: Server Platforms
---

### Post by paradoxni on 2012-05-18
Hey folks,

Having some problems with NFS on 11.10 64bit ubuntu-server.

I have exported a share on a file server and have 6 (virtualised, cloned) web servers attempting to mount.

4 servers mount the NFS ok, however the last 2 give the error:

```

mount.nfs: access denied by server while mounting

```

The fstab etc. on each of the 6 servers are identical (they are clones), however only 4 can connect at once?? is there a limit?

/etc/exports on fileserver:
```

/u0/share 192.168.0.*(rw,no_root_squash,async)

```

fstab on each web server:
```

192.168.0.10:/u0/share /share nfs vers=3,_netdev,user,rsize=8192,wsize=8192,timeo=14,intr 0 0

```

Baffling me how most servers can mount, but some cannot, even when they are all identical (apart from IP address).

---

### Post by SeijiSensei on 2012-05-18
What do the server logs show when it denies access?

---

### Post by paradoxni on 2012-05-18
> **SeijiSensei said:**
> What do the server logs show when it denies access?

refused mount request from .... for /u0/share (/u0/share): unmatched host

---

### Post by rubylaser on 2012-05-18
Do you have an /etc/hosts.allow file or firewall rule that is preventing these two hosts from connecting? 

```
cat /etc/hosts.allow
cat /etc/hosts.deny
```
```
iptables -nvL
```

One other stupid question; you've verified that networking is setup properly on these two vm's and something wasn't fat fingered setting up the static ips? 

As a temporary fix, you could add the insecure option to your /etc/exports but that would be a hack just to get it working.

---

### Post by SeijiSensei on 2012-05-19
> **paradoxni said:**
> /etc/exports on fileserver:
```

/u0/share 192.168.0.*(rw,no_root_squash,async)

```


I don't think a star works there.  I know that a CIDR subnet declaration will work:

```

/u0/share 192.168.0.0/24(rw,no_root_squash,async)

```

---

### Post by rubylaser on 2012-05-19
I've never used a wildcard either and always use a CIDR mask, but I did see some examples online using a wildcard.  Personally, I'd switch it to a CIDR mask and re-export though to make sure that's not causing the problem.

---

### Post by Jose Catre-Vandis on 2012-05-19
Also, is it always the same to virtual servers that won't connect? What happens if you shut down a couple of the ones that work, can the non-connecting ones now connect? 

Agree with the others about replacing the * with a 24. Also try using full IP address as opposed to host name :)

---

### Post by tdbtdb on 2013-01-07
[LEFT]I had similar mounting problems "refused mount request from" "unmatched host". The server was running ubuntu, the exported disks were external USB disks. Everything had been working, then stopped after reboot. The "cure" was to run "[COLOR=Red]exportfs[/COLOR] -a" on the server. NFS daemon had been running, but apprently partitions did not all get exported. Maybe boot-up USB timing issue?
[/LEFT]

---

