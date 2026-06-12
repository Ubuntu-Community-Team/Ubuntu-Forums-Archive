---
title: "bugs in openssh in 8.10"
date: 2008-11-20
forum: Server Platforms
---

### Post by mecat on 2008-11-20
hi

I have 2 servers : 8.04 na 8.10
on 8.04 i can use openssh client to connect to my switch 3com 5500G-EI without any problems, but on 8.10 i can't login. I'v attached logs from ssh client and from 3com switch.
Version of openssh in ubuntu 8.10
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
on 8.04
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
Does anybody have any other problems with new version of openssh? Any solutions or tips?

best regards

Miko&#322;aj Habdank

---

### Post by mecat on 2008-11-26
strange but linux putty works.

---

### Post by obg123 on 2008-11-26
First thing that strikes me: Could it be a problem with known_hosts? If so, try erasing the proper line from .ssh/known_hosts.

---

### Post by mecat on 2008-11-28
i'v tried, without any success. i'v also tried from other machine with ubuntu 8.10 desktop - with the same result.

best regards

Mikolaj

---

