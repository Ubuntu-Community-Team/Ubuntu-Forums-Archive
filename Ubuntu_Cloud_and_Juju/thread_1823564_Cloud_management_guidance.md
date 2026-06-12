---
title: "Cloud management guidance"
date: 2011-08-12
forum: Ubuntu Cloud and Juju
---

### Post by NigelRen on 2011-08-12
Hi
I've got through some of the technical things with building my own cloud using UEC, but I'm stuck with a more basic - and more generic cloud issue.
If I'm running a set of servers ( e.g. 3 Apache web servers ) which will each have their own log files generated relating to requests etc. and I want to ensure these log files are not lost when an instance is terminated.  Where would I store these log files?  This applies to any files like this which are needed beyond the lifespan of an instance.  Also in case of failure of a node, would also need to be recoverable.
Should they be stored in the storage controller or are they better mounted on a remote volume?  I was hoping there would be some sort of configuration guide that would give some guidance on these sorts of issues, but I haven't found one yet. So any pointers would be great.

Thanks

---

### Post by kim0 on 2011-08-12
In case of logging specifically, you can configure remote syslog on a more permanent machine

However more generally, as you mentioned it should be mounted from a remote persistent disk

---

