---
title: "Installing php5.2.13"
date: 2010-04-05
forum: Server Platforms
---

### Post by dtommy79 on 2010-04-05
Hi,

How can I install php5.2.13 from repository?

If I use sudo apt-get install php5

it installs for me php5.2.6 with suhosin patch

I only want a plain php install

---

### Post by Bachstelze on 2010-04-05
> **dtommy79 said:**
> Hi,

How can I install php5.2.13 from repository?

If I use sudo apt-get install php5

it installs for me php5.2.6 with suhosin patch

I only want a plain php install

Build it from source.

---

### Post by dtommy79 on 2010-04-05
How?

---

### Post by Bachstelze on 2010-04-05
Download source, ./configure, make, sudo make install. It's been a while since I last built PHP from source, but I don't recall it having any particular issue with compiling, just standard procedure.

---

