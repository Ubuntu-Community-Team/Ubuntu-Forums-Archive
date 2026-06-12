---
title: "Separate CLC and CC euca_conf --list-nodes"
date: 2011-03-24
forum: Ubuntu Cloud and Juju
---

### Post by Ric_ on 2011-03-24
If I have separate CLC and CC servers, should I be able to run 

```
euca_conf --list-nodes
```

On either the CLC or CC

Currently I get nothing on the CLC and on the CC I get:

> ERROR: cannot locate eucalyptus database, try logging in through the admin web interface.

Is there something simple I'm missing here?

---

### Post by Rusty au Lait on 2011-03-24
Just my 2¢

Run euca_conf on the CLC only. EUC is not the most verbose of packages so I would not find it unusual for a command to return nothing. I would try
sudo euca_conf --descover-nodes
on the CLC and see what comes up.

---

### Post by Ric_ on 2011-03-25
> **Rusty au Lait said:**
> Just my 2¢

Run euca_conf on the CLC only. EUC is not the most verbose of packages so I would not find it unusual for a command to return nothing. I would try
sudo euca_conf --descover-nodes
on the CLC and see what comes up.

root@c4p-uec01:/var/lib/eucalyptus# euca_conf --discover-nodes
New node found on 192.168.92.40; add it? [Yn] y
New node found on 192.168.92.41; add it? [Yn] y
New node found on 192.168.93.40; add it? [Yn] y
New node found on 192.168.93.41; add it? [Yn] y
ERROR: you need to be on the CC host and the CC needs to be running.

Which makes sense, however on the CC:

root@c4p-uec03:/var/lib/eucalyptus# euca_conf --list-nodes
ERROR: cannot locate eucalyptus database, try logging in through the admin web interface.

---

### Post by Ric_ on 2011-03-25
As the CLC can't see the nodes I don't seem to be able to start a instance :(

Does Anyone have any clues?

---

### Post by Rusty au Lait on 2011-03-25
Sorry.
How about euca_conf --list-clusters from the CLC. If there's anything there I'd try --deregister-cluster and
--register-cluster.

---

