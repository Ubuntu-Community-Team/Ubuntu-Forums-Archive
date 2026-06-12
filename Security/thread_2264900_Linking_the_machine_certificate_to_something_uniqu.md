---
title: "Linking the machine certificate to something unique like machine-id"
date: 2015-02-11
forum: Security
---

### Post by pradeep12 on 2015-02-11
Hi,

We have 802.1x configured on the wired ports , and we have an NPS authenticating clients via EAP-TLS.  My Ubuntu 14.04 LTS laptop is part of AD and has a certificate which was manually requested from our enterprise CA, and i'm able to connect successfully to the network.

We are now thinking if anyone can copy the keypair and certificate from one machine to another and can connect to the network.  

1) Is there a way we can make the certificate not exportable like in windows?

2) Also, is there a way to link the certificate with a unique id like “/var/lib/dbus/machine-id”  , so that even if one copies the certificate to his machine it wouldn't work?

Thanks

---

