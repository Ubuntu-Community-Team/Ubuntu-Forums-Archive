---
title: "Ubuntu 12.04 MySQL User"
date: 2012-08-16
forum: Server Platforms
---

### Post by Monkey Nuts on 2012-08-16
Hi,

I'm looking for a bit of help creating an Ubuntu user account (not a MySQL user account) to remotely administer MySQL from MySQL Workbench.

Workbench uses SSH to initiate admin commands and the setup wizard specifies that:

*This account needs write access to the my.cnf database config file, read access to the database logs and privileges to start/stop the database daemon.*

I'm currently running the MySQL Ubuntu box as a VM, so i've enabled the root account for this purpose and that's working fine. However, I want to move MySQL to a more potentially vulnerable location and would like to do things properly.

Any suggestions?

---

