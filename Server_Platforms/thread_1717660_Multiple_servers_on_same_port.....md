---
title: "Multiple servers on same port...."
date: 2011-03-30
forum: Server Platforms
---

### Post by Xeneth on 2011-03-30
Just wondering, what happens when you have multiple server softwares listening to the same port?  will it be able to distinguish which service to use by the protocol information, or is it setting it up for failure?

IE: http and ssh both listening to port 80.

---

### Post by BkkBonanza on 2011-03-30
You can't do that. The process that gets there first will deny the second one from being able to bind to the port.

You would have to create a second IP address on a virtual interface and then use that one to bind to the same port, different IP. This is easy to do but not configured by default.

---

### Post by SeijiSensei on 2011-03-30
Just assign one service to a port above 1023.

---

