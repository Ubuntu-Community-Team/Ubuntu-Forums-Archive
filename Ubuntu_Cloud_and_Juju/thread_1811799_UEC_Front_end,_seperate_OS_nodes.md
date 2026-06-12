---
title: "UEC Front end, seperate OS nodes?"
date: 2011-07-25
forum: Ubuntu Cloud and Juju
---

### Post by Dori922 on 2011-07-25
Im testing/learning Cloud in a lab and ive run into a few problems!! :o

Ive set up my front end fine with UEC but my node is giving me problems because the CPU on that pc doesnt support VT!! I tried installing Xen but ran into problems with the "make tools" command.

Frustrated like WOAAAHHH DIE PC DIIIIIEEE!! so thinking of solutions

Ideas i have are rescripting  the makefile script(learning the skills of scripting while im at it!! :P), or installing a seperate cloud OS on the nodes(Maybe Debian or Xen)..

Havent looked into what new OS to use but would a UEC front end communicate with a non-UEC node?

---

### Post by Rusty au Lait on 2011-07-25
Your only hope is to find a CPU with VT. If the CLC machine has a CPU w/ VT you could switch machines.

---

### Post by kim0 on 2011-07-27
Since ubuntu cloud is switching to openstack, you might want to experiment with nova under virtualbox [http://wiki.openstack.org/NovaVirtually](http://wiki.openstack.org/NovaVirtually)

---

