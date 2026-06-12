---
title: "Why to deploy Juju with Ha on manual environment"
date: 2016-10-27
forum: Ubuntu Cloud and Juju
---

### Post by vibol on 2016-10-27
Hello, i install ubuntu 16.04 with juju 2.0(without ppa) and my server is list below

Juju master node 10.0.0.100
first bootstrap node 10.0.0.101

there still 2 machine available x.x.x.102, 103

I also want this next 2 machine to be my second and third controller or bootstrap node.

i have add this 2 machine to my agent node. when i run juju status i see this 2 machine name in machine 0, 1
Where is my first bootstrap machine ? why i got error machine not found when i run ```
juju enable-ha -n 3 --to 0,1 
```

Is there a trick to deploy juju in ha on manual environment or, manual environment don't support ha ?

Thank you!

---

### Post by ajcloud2 on 2016-11-21
Hello,

I encountered the same problem.

The thread is marked as "SOLVED", Could you please share the solution?

Thanks!

---

