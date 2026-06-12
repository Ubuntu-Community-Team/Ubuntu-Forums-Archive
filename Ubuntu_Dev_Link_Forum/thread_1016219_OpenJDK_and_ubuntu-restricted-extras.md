---
title: "OpenJDK and ubuntu-restricted-extras"
date: 2008-12-19
forum: Ubuntu Dev Link Forum
---

### Post by cb951303 on 2008-12-19
Currently, ubuntu-restricted-extras package depends on sun's java. Is there a reason not to remove this dependency from u.r.e and install openjdk-jre by default?

Thanks

---

### Post by Martje_001 on 2008-12-20
I don't think so:

[http://www.phoronix.com/scan.php?page=article&item=java_vm_performance&num=1](http://www.phoronix.com/scan.php?page=article&item=java_vm_performance&num=1)

see OpenJDK vs Sun JAVA

---

### Post by cb951303 on 2008-12-20
> **Martje_001 said:**
> I don't think so:

[http://www.phoronix.com/scan.php?page=article&item=java_vm_performance&num=1](http://www.phoronix.com/scan.php?page=article&item=java_vm_performance&num=1)

see OpenJDK vs Sun JAVA

not much difference. Much better than windows. it's more than acceptable

---

### Post by Martje_001 on 2008-12-20
For clarity: I did mean to say that (IMO) there isn't a reason to not depend on openJDK.

---

### Post by cb951303 on 2008-12-20
> **Martje_001 said:**
> For clarity: I did mean to say that (IMO) there isn't a reason to not depend on openJDK.

I did get it wrong sorry :popcorn:

---

### Post by xavierorr on 2009-04-28
the openJDK build in jaunty is a waste of time, it is slow and most apps don't work correctly. applets are a disaster, most crashing firefox. ubuntu restricted extras should install the sun java and stop wasting peoples time.

---

