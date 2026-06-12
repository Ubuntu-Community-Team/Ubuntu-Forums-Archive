---
title: "Deoloying Canonical Openstack (Queens) with TLS endpoint encryption using Juju"
date: 2020-01-23
forum: Ubuntu Cloud and Juju
---

### Post by irathore on 2020-01-23
I am testing Openstack with TLS encryption for internal and external endpoints. I am looking for a document that describes how I can deploy Openstack with Juju/MAAS with TLS. Any help pointers will be appreciated.

---

### Post by irathore on 2020-01-24
This is for one of my customers. They will switch to Canonical openstack if we cane deploy with TLS Everywhere and it is supported.

---

### Post by digikin on 2020-01-27
Juju will not automatically configure TLS you will have to configure it but there is plenty of documentation directly on OpenStacks website:
[https://docs.openstack.org/security-guide/secure-communication/introduction-to-ssl-and-tls.html](https://docs.openstack.org/security-guide/secure-communication/introduction-to-ssl-and-tls.html)

---

