---
title: "Automatically generated Drop rules in iptables"
date: 2010-12-07
forum: Security
---

### Post by Hykis on 2010-12-07
I'm having an issue wherein Ubuntu 9.10 running Squid is automatically generating drop entries on the Input and Forward chains.  It appears to be caused by high traffic.  I know I can reproduce it when performing an OS install on another system and using the Squid server as the proxy for updates.

I've searched high and low but am unable to identify what process/kernel setting is causing this.

Can anyone provide suggestions on where to look?

Proxy Server Details:
  * Kernel: 2.6.31-20-server
  * iptables v1.4.4
  * Squid Cache (Version 2.7.STABLE6)

---

### Post by bodhi.zazen on 2010-12-07
Are you sure it is squid doing this? that sounds unusual, do you have psad, ossec, fail2ban or some other service doing this ?

Can you post the rules and perhaps any information from the logs ?

---

### Post by Hykis on 2010-12-08
No, I doubt it's Squid.  It may be OSSec... I'll check there.  I know OSSec is running.  I didn't know it took an active role in that manner.  I suspect there's a high probability OSSec is the culprit.  I know I've check the logs several times.  I'll check the logs on the OSSec server.  Thanks for the thought provoking question.  I'll post a follow-up with the results or more info.

---

### Post by bodhi.zazen on 2010-12-08
OSSEC is the culprit =)

Check the logs and see if you might wish to modify a few of the ossec rules.

---

