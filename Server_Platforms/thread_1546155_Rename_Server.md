---
title: "Rename Server"
date: 2010-08-04
forum: Server Platforms
---

### Post by erbag on 2010-08-04
How do I rename my server from the terminal... suppose i want to change the name from server to ubuntu-server... How do I do that?

---

### Post by bschelst on 2010-08-05
- open terminal
- sudo vi /etc/hostname

change it...

- sudo service hostname start

---

### Post by Ryan Dwyer on 2010-08-05
You should also update your hostname in /etc/hosts if it's there.

---

### Post by Iowan on 2010-08-05
> **Ryan Dwyer said:**
> You should also update your hostname in /etc/hosts if it's there. If you don't update */etc/hosts* and */etc/hostname* at the same time, **sudo** seems to get confused and complain.

---

