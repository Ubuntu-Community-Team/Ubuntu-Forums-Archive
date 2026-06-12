---
title: "Empty /var/run/eucalyptus/net, dhcp not starting"
date: 2011-04-13
forum: Ubuntu Cloud and Juju
---

### Post by Luis Rodero-Merino on 2011-04-13
Hi,

I'm trying to install eucalyptus-cloud and eucalyptus-cc in an ubuntu server machine (10.04). I use MANAGED-NOVLAN mode, but the dhcp is not started. In fact, the /var/run/eucalyptus/net folder is empty, but the log files in /var/log/eucalyptus/cloud* do not show any error message.

Can you give me any clue where to start looking for potential causes for these problems? I'm specially concerned about the fact that /var/run/eucalyptus/net does not contain anything.

Thank you very much for your help and support!

---

### Post by Luis Rodero-Merino on 2011-04-14
Just to clarify, syslog does not provide any clue about possible error causes. It seems to me that it can be a problem with permissions, but I'm not sure. Starting eucalyptus as 'root' user (changing EUCA_USER='root' in /etc/eucalyptus//eucalyptus.conf) does not seem to have any effect.

So, does anyone know who is supposed to create the /var/run/eucalyptus/net/euca-dhcp.conf file? That could give me a clue about what is happening...

---

### Post by Luis Rodero-Merino on 2011-04-14
Side note: the '/' of the machines where I'm trying to install Eucalyptus are mounted through NFS. Could that be a problem?

---

### Post by kim0 on 2011-04-18
Hi there,
Please check the recommended package install instructions at
[https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)
Hope that helps :)

---

