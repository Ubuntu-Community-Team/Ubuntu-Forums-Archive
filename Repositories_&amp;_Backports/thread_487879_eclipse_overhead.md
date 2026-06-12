---
title: "eclipse overhead"
date: 2007-06-29
forum: Repositories &amp; Backports
---

### Post by DLGandalf on 2007-06-29
While the java environment (from sun) is out for a while under real opensource, the eclipse package still has dependencies to the IBM java environment gcj and all kinda stuff.

Is this the kind of place to "complain" about that. If not where should I go

thanks

---

### Post by tribaal on 2007-06-29
This should be changed indeed, I agree.

Meanwhile, I just used the .jar file from the eclipse website, the only downside to this is that you'll have to create the main menu link yourself.. Which isn't such a hassle :)

- trib'

---

### Post by mlind on 2007-06-29
> **DLGandalf said:**
> While the java environment (from sun) is out for a while under real opensource, the eclipse package still has dependencies to the IBM java environment gcj and all kinda stuff.

Is this the kind of place to "complain" about that. If not where should I go

thanks

file a bug against sun-java6 package (not sure about java 1.5's license) that it should get promoted from multiverse to main. Then file a bug against eclipse.

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/](https://bugs.launchpad.net/ubuntu/+source/sun-java6/)
[https://bugs.launchpad.net/ubuntu/+source/eclipse/](https://bugs.launchpad.net/ubuntu/+source/eclipse/)

---

