---
title: "Landscape/juju - App/Unit of landscape is shown as blocked"
date: 2024-04-04
forum: Ubuntu Cloud and Juju
---

### Post by hillpig on 2024-04-04
Hi,


I deployed the Landscape service via the Juju charm. Recently, the app/unit is shown as blocked when I run juju status.


Then I checked the unit using the following CMDs.
---------------------------------------------------------------------
in Unit:

1. journalctl -x
2. lsctl status
3. systemctl list-units --no-pager


out of Unit:

juju debug-log --replay --no-tail --include landscape-server/0
---------------------------------------------------------------------


But no luck, every service seems to be working well, and I cannot figure out the cause of the blocked status.


I would appreciate any advice you can offer. Thank you!

---

