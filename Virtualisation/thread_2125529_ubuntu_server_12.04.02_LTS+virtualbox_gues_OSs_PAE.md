---
title: "ubuntu server 12.04.02 LTS+virtualbox gues OSs PAE cpu"
date: 2013-03-14
forum: Virtualisation
---

### Post by binary_dreamer on 2013-03-14
i am running an Ubuntu server 12.04.02 and i do have virtualbox on it to guest OSes for different services.
i am running in problem with some OSes when creating the machine and try to install it, it says that it has PAE CPU and i have to get a different version....
did anybody came across a similar issue?

---

### Post by TheFu on 2013-03-14
Which guest OSes are working?
Which guest OSes are NOT working?
Which exact model CPUs are involved?
How much RAM is on the hostOS and allocated to each guestOS?

Please be specific.

A guess is more than 4+GB of RAM is allocated to the GuestOS or you are trying to install a 64-bit OS on a 32-bit system.  Choosing the correct CPU architecture for the OS  is important.

---

### Post by ibjsb4 on 2013-03-14
Do you have a PAE cpu?

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

If so have you enabled it?

[ATTACH=CONFIG]240170[/ATTACH]

---

### Post by binary_dreamer on 2013-03-15
thanks a lot ibjsb4
it solved the problem

---

### Post by ibjsb4 on 2013-03-15
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

