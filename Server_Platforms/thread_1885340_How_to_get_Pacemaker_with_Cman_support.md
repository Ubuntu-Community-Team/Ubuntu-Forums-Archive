---
title: "How to get Pacemaker with Cman support?"
date: 2011-11-23
forum: Server Platforms
---

### Post by beatseed on 2011-11-23
Hello, community.
Ubuntu 11.10
I try to configure Active/Active cluster Cman+Pacemaker, that described there:
[http://www.clusterlabs.org/doc/en-US/Pacemaker/1.1/html/Clusters_from_Scratch/](http://www.clusterlabs.org/doc/en-US/Pacemaker/1.1/html/Clusters_from_Scratch/)
I set Cman, but when i start Pacemaker with this command:
$sudo service pacemaker start
I get this log event:
ERROR: read_config: Corosync configured for CMAN but this build of Pacemaker doesn't support it
I found bug description there:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=639548](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=639548)
Author ask developers build Pacemaker with Cman support.
But there is not answer. 
How can i get Pacemaster with Cman support?

---

