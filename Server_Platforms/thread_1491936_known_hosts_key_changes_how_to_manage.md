---
title: "known_hosts key changes how to manage"
date: 2010-05-24
forum: Server Platforms
---

### Post by tapas_mishra on 2010-05-24
Hi,
I am running some experiment with my kvm based Virtual Machines.I have deleted them and re installed from scratch.The problem is each time I do so the known_hosts on my laptop change and I delete this file from ~/.ssh/known_hosts
is there a way to avoid this and save the identity of rest of the computers on network whose identity I have.Its not possible to connect to them again and again to add their keys.
If my question is not clear let me know.

---

### Post by wojox on 2010-05-24
just go in and delete it. :)

---

### Post by koenn on 2010-05-24
you will usually get a reference to the 'offending' key, with a number. 
you can just go count them in known_hosts and delete it. If you have to do it a lot (lost of reinstalling virtual servers, ...), it may be convenient to memorize this  command :

```
sed -i 5d  ~/.ssh/known_hosts
``` deletes line/key #5 from known_hosts

---

