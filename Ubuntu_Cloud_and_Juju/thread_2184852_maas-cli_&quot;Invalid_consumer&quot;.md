---
title: "maas-cli &quot;Invalid consumer&quot;"
date: 2013-10-30
forum: Ubuntu Cloud and Juju
---

### Post by charlestmackay on 2013-10-30
I am trying to configure and add nodes to my maas system. 
Every time I try to use any of the maas-cli commands, i get "invalid consumer".



~$ maas-cli maas node-groups import-boot-images
Invalid consumer.
~$ maas-cli maas nodes accept-all
Invalid consumer.


What does this error message mean, and how can I fix this?

Thanks.

---

### Post by charlestmackay on 2013-10-31
invalid consumer [key] is what the error message should have said. I generated a new maas key and logged in again. I was then able to issue maas-cli commands to my maas profile

---

