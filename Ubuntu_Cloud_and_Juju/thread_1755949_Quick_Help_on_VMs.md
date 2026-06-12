---
title: "Quick Help on VMs"
date: 2011-05-11
forum: Ubuntu Cloud and Juju
---

### Post by daredevil29041989 on 2011-05-11
Hi all ,,,
This is my graduation project and i've installed UEC on my pcs ... the idea of the project is to use all the nodes to run an application process on the cloud and reduce the processing time and make it faster than running the same application process on single PC .

My question is : Can i make one VM of all node controller (i mean just one VM on all NCs ) to run my application on it  ? or there is another way to do it ?


Hint : there is a Research Assistant in our University told me that i can make any number of VM on every single node but he didn't try to make a big VM on all nodes .

---

### Post by kim0 on 2011-05-13
As per my understanding, you cannot make "one big VM across many nodes". You can however run a program on many VMs, if that program is designed to make use of multiple machines (say by exchanging messages). If you're going to reply to this thread, please mention more detail to exactly what you need

---

