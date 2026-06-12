---
title: "Accessing server inside virtual box windows 7 from host ubuntu 12.04?"
date: 2013-08-24
forum: Virtualisation
---

### Post by boy18nj on 2013-08-24
Hello,

I'm using ubuntu 12.04 and am using windows 7 thru virtual box. I've oracle express 11g running inside virtual box window 7 on 127.0.0.1:8080 . Virtual box settings are set to NAT. 

How do i access virtual box window 7 127.0.0.1:8080 from host ubuntu 12.04?

THanks

---

### Post by Cheesemill on 2013-08-24
*Thread moved to **Virtualisation**.*

Change your VM so that it uses bridged mode instead of NAT, then just go to [http://serveripaddress:8080](http://serveripaddress:8080).

---

### Post by boy18nj on 2013-08-24
Thanks for reply.

I set Virtual Box to Bridged Adapter.

I tried Virtual Box Windows 7 IP address as-

192.168.0.7:8080 from Ubuntu

Still it didn't worked. Am i doing something missing?

---

