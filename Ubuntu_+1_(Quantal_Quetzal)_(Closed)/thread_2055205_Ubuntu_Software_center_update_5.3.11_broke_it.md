---
title: "Ubuntu Software center update 5.3.11 broke it"
date: 2012-09-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pnarciso on 2012-09-08
I'm running Xubuntu 12.10 and the latest update of USC made the app to not start.

It opens a window briefly and closes.

I reported the issue in here : [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1047281](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1047281)

---

### Post by wgarcia on 2012-09-10
I'm getting this error too, with exactly the same symptoms (I'm running Ubuntu 12.10). When I try to report it with apport, after the system collects the information it tells me that the bug has already been reported, tries to open the launchpad page for the error, but a page opens saying "page not found". I suspect apport is trying to open a bug which is private and therefore it is not able to open it, but to the user it seems an apport error.

---

### Post by Stinger on 2012-09-10
+1
Have added myself to the bugreport.

---

### Post by Stinger on 2012-09-10
Update !
Alan Pope has made the original bug visible to the public.
You can now report to [Bug#1047295]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1047295") and mark [Bug#1047281]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1047281") as duplicate.

---

### Post by pnarciso on 2012-09-10
A fix was committed regarding bug #1047281, so it should land pretty soon.

---

### Post by Stinger on 2012-09-10
I marked [Bug#1047295]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1047295") is duplicate instead :)

---

