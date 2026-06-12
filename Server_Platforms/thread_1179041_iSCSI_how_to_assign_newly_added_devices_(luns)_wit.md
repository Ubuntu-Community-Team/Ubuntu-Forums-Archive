---
title: "iSCSI how to assign newly added devices (luns) without interupting active session"
date: 2009-06-05
forum: Server Platforms
---

### Post by TheR on 2009-06-05
I know how to dinamicaly add new device (lun) to iscsi target with ietadm. 

But how do I recognise and assign this device on initiator without droping active sessions.  /etc/init.d/open-iscsi restart  or  /etc/init.d/open-iscsi restarttargets breaks active sessions. At least on my machine. I am playing with KVM on Ubuntu 9.10 alpha and live sessions get interrupted.

by
TheR

---

### Post by TheR on 2009-06-06
I don't belive that this is not possible. How should be done then. It might be a bug.

by
TheR

---

