---
title: "Dell PowerEdge R515: iDRAC6 support"
date: 2012-10-02
forum: Server Platforms
---

### Post by FlyboyData on 2012-10-02
Hello,
 
I have successfully installed Ubuntu 12.04 server onto a Dell Poweredge R515 server (which is on the Ubuntu hardware compatibility guide). Of course, Dell doesn't consider Ubuntu a supported OS...
 
My issue is this: in the iDRAC6 built into the server (enterprise version, for anyone keeping count, with version 1.80 of the firmware), the iDRAC isn't showing operating system boots in the logs, and shows a huge blank on the "Currently running operating system" in the iDRAC. I can get a console through the IDRAC, though...
 
Any way to get the OS to interact with the iDRAC a little better? It would be nice if we were logging boots and graceful shutdowns...;)

---

### Post by hasan.akgoz on 2012-10-02
IDRAC is operating system independent. I do not think the problem is from ubuntu. Can you try with a different web browser such as chrome, like firefox.

---

### Post by FlyboyData on 2012-10-03
It has nothing to do with the browser I'm using.  I tried alternate browsers and OS'es.  Somehow, Windows is nice enough to tell the iDRAC the operating system version, and when the system boots and reboots.  I'm sure Red Hat or SuSE would, too as they are both supported by Dell.  I wish that I knew how to make Ubuntu communicate with the iDRAC...just wondering if it's an optional package or two that I need to install (probably not that simple...).

---

### Post by hasan.akgoz on 2012-10-04
very interesting. I wondered. Would you share a screenshot? Many Dell server installed. I've never seen such a thing.

---

