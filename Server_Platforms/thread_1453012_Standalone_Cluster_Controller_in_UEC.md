---
title: "Standalone Cluster Controller in UEC"
date: 2010-04-12
forum: Server Platforms
---

### Post by kjordan2001 on 2010-04-12
I'm trying to create a separate cluster controller from a cloud controller since I may create more than one cluster in the future.  However, it seems that eucalyptus-cc and eucalyptus-sc depend on eucalyptus-cloud to run (not to mention the fact that the installer doesn't let you make just a cluster controller).  And I can get to the point that I can add my cluster to the other cloud controller, but then I get errors that the eucalyptus-cloud service on my cluster controller can't connect to its hsql database (or possibly the other controller's database).  Is it possible to do this currently through UEC or the Ubuntu server packages?  I know it's possible to do this through regular Eucalyptus, but I wanted ease of setup (which this is actually turning into a bigger pain if I want to do it this way through UEC).

Also, I'm wondering why it defaults to MANAGED-VLAN on the controller if MANAGED-VLAN needs a bridge, which isn't set up by default.

---

