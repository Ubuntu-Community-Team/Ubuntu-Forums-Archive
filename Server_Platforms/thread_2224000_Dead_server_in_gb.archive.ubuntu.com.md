---
title: "Dead server in gb.archive.ubuntu.com"
date: 2014-05-14
forum: Server Platforms
---

### Post by candlerb on 2014-05-14
Sorry but I'm not sure where else to post this report!

gb.archive.ubuntu.com gives a round-robin DNS reply to four servers, but one of them is dead.

$ nslookup gb.archive.ubuntu.com
...

Non-authoritative answer:
Name:	gb.archive.ubuntu.com
Address: 91.189.92.201
Name:	gb.archive.ubuntu.com
Address: 194.169.254.10
Name:	gb.archive.ubuntu.com
Address: 91.189.88.153
Name:	gb.archive.ubuntu.com
Address: 91.189.92.200
 $ telnet 91.189.88.153 80
Trying 91.189.88.153...
^C

(According to reverse DNS, this is "cherufe.canonical.com")

As a result, package updates are slower than they should be as sometimes this server is hit and takes a while to time out.

I've checked, this is the authoritative answer:

$ dig +norec @ns1.canonical.com. gb.archive.ubuntu.com. a
...
;; ANSWER SECTION:
gb.archive.ubuntu.com.	600	IN	A	194.169.254.10
gb.archive.ubuntu.com.	600	IN	A	91.189.88.153
gb.archive.ubuntu.com.	600	IN	A	91.189.92.200
gb.archive.ubuntu.com.	600	IN	A	91.189.92.201

Can the entry for 91.189.88.153 be removed please?

Thanks,

Brian.

---

### Post by slickymaster on 2014-05-14
Moved to the **Server Platforms** sub-forum.

---

### Post by orygynz on 2014-05-14
I have the same problem with cherufe ip 91.189.88.153. (security ubuntu)
I can't upgrade a server, host unreachable.

---

### Post by candlerb on 2014-06-24
It has been fixed now.

```
$ nslookup gb.archive.ubuntu.com
...
Non-authoritative answer:
Name:	gb.archive.ubuntu.com
Address: 91.189.92.201
Name:	gb.archive.ubuntu.com
Address: 194.169.254.10
Name:	gb.archive.ubuntu.com
Address: 91.189.92.200

```

---

