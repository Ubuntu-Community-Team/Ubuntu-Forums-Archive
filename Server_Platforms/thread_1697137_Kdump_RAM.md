---
title: "Kdump RAM"
date: 2011-02-28
forum: Server Platforms
---

### Post by mannmaniyar on 2011-02-28
Hi,

Greetings!!

I configured Kdump and tested it by creating a crash.

everthing was working fine.

the issuse is time taken for creating a vmcore file.

it took me 3 hours to create a vmcore file over NFS.

test environment senario:

I have server with 100GB RAM for which kdump was configured.

vmcore file is created on other server using NFS share.

intially I configured crashkernal with 128M@16M. it took more than 3 hours to create vmcore file.

then i configured crashkernal with 512M@16M. it took around 1 hour to create vmcore file.

I just wanted to can increase RAM for crashkernal are then any limitation.

any other suggestions to increase the perfomance.

Thanks in advance.

Mann

---

