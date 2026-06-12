---
title: "No client powerdown"
date: 2008-10-03
forum: Server Platforms
---

### Post by fut on 2008-10-03
Hi

I`m running XUbuntu (Hardy) as a little network (WLAN) with one Server an two fat clients.
For this reason NIS and NFS is in use.
NIS is configured to export users and groups with a ID over 10000 only.
For system administrations one user with a ID under 10000 are registered at the clients.

All in all every thing is running but users exported with NIS can`t power down the clients.
More exactly: NIS-users can shout down the clients but clients will stay on halt and the hardware don`t power off.

Local registered users on client site can do this, also experimental users without admin rights.

To my surprise the same problem found out of GDM:
Was the last graphical logged out user exported from NIS shout down from GDM will stay at halt without power off.
Was the last graphical logged out user a local one power down out of GDM works fine.


The last configuration of this network runs with dapper without this problems.
From there I believe that it hangs to rights of access at client site.
But experiments with groups, policykid and hal brought no solution.

Maybe somebody can help me with this problem.

Thanks

---

