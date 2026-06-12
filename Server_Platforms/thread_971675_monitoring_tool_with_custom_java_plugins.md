---
title: "monitoring tool with custom java plugins"
date: 2008-11-05
forum: Server Platforms
---

### Post by ufis on 2008-11-05
Hi,

I am looking for a network/services monitoring tool (like nagios) that will enable me to easily plug in existing java classes.

I currently have some java classes that I use to test various parts of our system. If I can easily feed the results from these into an existing monitoring tool (like nagios) it will be great.

The one big problem I am foreseeing is system resources. When finished, there may be as much as 50 tests that must be performed. If these are to be checked every minute it would mean 50 jvm's being created and destroyed every minute.
The solution must provide a way to sidestep this problem.

The tool must be able to accommodate *java*. Some of these checks use various custom and commercial jars to access various parts of the system.

Any ideas?

---

