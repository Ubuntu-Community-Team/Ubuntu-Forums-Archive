---
title: "Solution for Ubuntu Server to host Thin Clients running Windows Virtual Machines"
date: 2011-05-11
forum: Ubuntu Cloud and Juju
---

### Post by MikeInWA on 2011-05-11
Hi forum. Could anyone advice me of the best way of configure the following:
Instead of using 6 server grade machines I would like to use simpler hardware or Thin Clients to run W2k3 or W2k8 server as Virtual Machine guests (today we run VMWare Player in a WinXP 'stand alone' host environment). This should then be connected to a central host server (running Ubuntu 11.04 server?).
I've browsed the net without finding a short descriptive answer to this so any help is highly appreciated :). At the same time I hope my Q wasn't too blurry!

Cheers, Mike

---

### Post by aromo on 2011-05-11
I don't understand.  You want a thin client to run a virtual server?  I think it's the other way around.  Can you explain your scenario a bit more and what is it that you want to achieve?

---

### Post by kim0 on 2011-05-11
Yeah more details would be great

---

### Post by itfreaksnet on 2011-05-16
You want to use Remote Desktop Connection / TS  functionality by hosting a Win2003/2008 server on Ubuntu Cloud platform ? And connect to it with Thin client ?

br

---

### Post by MikeInWA on 2011-05-17
Well, at the moment here in our learning institution we're using networked stand alone server-grade workstations with W2K3/K8 operative system and our own applications on top. What I'm looking for (if there is any) is a solution where I could centralize a number of virtual machines (KVM, Xen or VMWare?) in one server and use significantly cheaper hardware such as Thin Linux Clients for the students. What could be the options for this?
/Mike

---

### Post by MikeInWA on 2011-05-17
> **itfreaksnet said:**
> You want to use Remote Desktop Connection / TS  functionality by hosting a Win2003/2008 server on Ubuntu Cloud platform ? And connect to it with Thin client ?

br

Yes. Remote Desktop could be a solution or as I commented above, with some kind of multi Virtual Machine environment hosted by the Server?

---

