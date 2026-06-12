---
title: "BIND9 Restart Failed."
date: 2012-07-11
forum: Server Platforms
---

### Post by LiftedTurbo on 2012-07-11
):p

---

### Post by cconstantine on 2012-07-11
your .options file has a syntax error; You've a close-curly right after listen-on ... that closes the options {} block.

Move that close-curly to the bottom, so your "forwarders" section is actually within your options section.

---

### Post by LiftedTurbo on 2012-07-11
Removed...

---

