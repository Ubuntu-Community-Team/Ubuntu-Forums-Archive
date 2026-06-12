---
title: "easiest way to get SMP in a guest Ubuntu?"
date: 2009-04-02
forum: Virtualisation
---

### Post by jdrodrig on 2009-04-02
I was hoping you could point me toward the easiest implementation of having two cores available to a guest Ubuntu inside Vista.

so far, what I understand is that VBox wont do it, right? I am, as we speak, going to try VMWare Workstation but before spending 189 or so bucks, I was wondering if there are other alternatives

(I want to do some software development in fortran inside ubuntu, and I would like to have the two cores of my laptop available to the compiler.)

---

### Post by dcstar on 2009-04-02
> **jdrodrig said:**
> I was hoping you could point me toward the easiest implementation of having two cores available to a guest Ubuntu inside Vista.

so far, what I understand is that VBox wont do it, right? I am, as we speak, going to try VMWare Workstation but before spending 189 or so bucks, I was wondering if there are other alternatives

(I want to do some software development in fortran inside ubuntu, and I would like to have the two cores of my laptop available to the compiler.)

The (free) VMWare Server will allow you to assign multiple cores to guests - but there are performance issues with the 1.x version AFAIK.

---

### Post by James_Lochhead on 2009-04-03
> **jdrodrig said:**
> I was hoping you could point me toward the easiest implementation of having two cores available to a guest Ubuntu inside Vista.

so far, what I understand is that VBox wont do it, right? I am, as we speak, going to try VMWare Workstation but before spending 189 or so bucks, I was wondering if there are other alternatives

(I want to do some software development in fortran inside ubuntu, and I would like to have the two cores of my laptop available to the compiler.)

Easy and free way:

1) Install the 1 month Workstation trial

2) Create a VM, install VMware tools on guest and back it up - make sure you get configs right

3) Uninstall Workstation

4) Install and use VMware player (propriety but free)

It is not actually necessary to have Workstation to use the VMs it creates. I actually have Workstation and mostly use the player as I can launch VMs from a launcher.

---

### Post by jdrodrig on 2009-04-03
> **James_Lochhead said:**
> Easy and free way:

1) Install the 1 month Workstation trial

2) Create a VM, install VMware tools on guest and back it up - make sure you get configs right

3) Uninstall Workstation

4) Install and use VMware player (propriety but free)

It is not actually necessary to have Workstation to use the VMs it creates. I actually have Workstation and mostly use the player as I can launch VMs from a launcher.

This make sense. Thanks a lot.

I am now in day 2 out of 33, so I guess I can do some trial-and-error steps going from Workstation to player back and forth..

---

