---
title: "PXE Error.  First client worked, second &quot;Can't open /tmp/net-eth0.conf&quot;"
date: 2008-03-03
forum: Server Platforms
---

### Post by jtzl on 2008-03-03
Greetings,

I setup a PXE netboot server largely following the instructions found [here]("http://www.xs4all.nl/~rjb/fatclient.html").  The PXE server is a Dell Inspiron 530 (new one), and the first client machine was an eMachines that worked fine.  I successfully booted into the PXE server multiple times and even rebooted and tried again to make sure it was working properly.

Now, trying to use another Dell Inspiron 530, I'm unable to boot off the LAN.  Instead, I get the following error message during boot:

> "NET:  Registered protocol family 17
ipconfig: eth0: SIOCGIFINDEX:  No such device
ipconfig:  no devices to configure
/init: .: 1: Can't open /tmp/net-eth0.conf
kernel panic - not syncing:  Attempted to kill init!"

From what I've read, this issue is related to the NIC drivers not being detected, but I don't see anything in interfaces or modules that is apparently special.  Moreover, I can boot into Ubuntu and simply be online without having to install drivers after I install using the LiveCD..

Is anybody familiar with this problem and its workaround or solution?

Thanks in advance!

---

