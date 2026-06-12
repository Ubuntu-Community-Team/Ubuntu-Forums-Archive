---
title: "Cardinality of JuJu units"
date: 2017-09-23
forum: Ubuntu Cloud and Juju
---

### Post by rbrown4 on 2017-09-23
When Juju deploys a charm it is assigned a unit and unit number of the form  <service>/<id>  where id always increases.  Is there anyway to determine cardinality for charms deployed multiple times? Can I tell which charm was deployed first from within the hook environment? For example, if I have  charm-service/20 and I use juju add-unit charm-service --2, I  end up with charm-service/21, charm-service/22.     Does charm-service/22 know that it is the 3rd (active) instance of the charm?

---

