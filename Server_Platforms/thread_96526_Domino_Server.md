---
title: "Domino Server"
date: 2005-11-29
forum: Server Platforms
---

### Post by Frasir on 2005-11-29
Hi,

I've installed Domino 6.5.2 on Ubuntu.

When I manually start the Domino Server, I have the following error:
/opt/lotus/notes/latest/linux/server: symbol lookup error: /opt/lotus/notes/latest/linux/libnotes.so: undefined symbol: cerr

The directory is correct and the file, libnotes.so, is there.

What could be wrong?

Thanks!

---

### Post by snakeman on 2005-11-30
Show me the command you are starting Domino With.  I haven't used it since version 5.0.3, one of the first linux releases.




snakeman

---

### Post by Frasir on 2005-11-30
[QUOTE=snakeman]Show me the command you are starting Domino With.  I haven't used it since version 5.0.3, one of the first linux releases.

snakeman[/QUOTE]

Hi,

I use ./server at /opt/lotus/bin

Tks

---

### Post by snakeman on 2005-12-02
Where are the data files located and the notes.ini


Unless something changed you have to start it in the localdata dir



snakeman

---

