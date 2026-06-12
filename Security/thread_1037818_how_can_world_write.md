---
title: "how can world write"
date: 2009-01-12
forum: Security
---

### Post by ms.shams on 2009-01-12
Hi,

if one of my file has 777 permission and exists on public_html folder on my server, how can world write on my file without any user account? can you explain it?

---

### Post by hyper_ch on 2009-01-12
apache can write to it

---

### Post by ms.shams on 2009-01-12
i know. but only application that run on server can do it? or all users can?

---

### Post by hyper_ch on 2009-01-12
all users and daemons on the server can write to it... that's what the "world" permissions are for.

---

### Post by scorp123 on 2009-01-12
> **ms.shams said:**
> how can world write on my file without any user account? can you explain it? Most processes do in fact have their own user accounts. Go and take a look at this file:  **/etc/passwd**

There will be a dozen or so accounts owned by various programs. If you have a file with "777" permissions then this means that these programs can write to that file too. Depending on what you are doing this can be desirable (e.g. using Apache for WebDAV or something like that?) or extremely undesirable (e.g. a hacker attacking your installation and tricking any of the processes to overwrite the file with malicious code!).

It's called "world writable" because there is nothing that would stop anything at writing to this file. If something somehow can gain access to that file --no matter if good or bad-- it will be able to overwrite that file.

---

