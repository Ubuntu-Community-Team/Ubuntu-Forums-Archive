---
title: "Postgresql Loses Data on Reboot"
date: 2009-01-26
forum: Server Platforms
---

### Post by deejross on 2009-01-26
I'm having a very strange problem. I'm running Intrepid as a virtual machine inside Parallels. It runs Apache2, PHP5, and PostgreSQL 8.3. I gave it 256MB of ram since it's only a development machine.

Everytime I reboot the virtual machine, any data in the tables disappears. I've checked the postgresql logs and the only thing I see is "LOG: incomplete startup packet". All the tables' structures are fine and the sequences are still intact. As far as I know, I'm not doing any transactions.

Any thoughts? Thanks in advance.

---

