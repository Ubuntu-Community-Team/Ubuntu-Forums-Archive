---
title: "VirtualBox for Kiosk purpose"
date: 2010-06-05
forum: Virtualisation
---

### Post by anantshri on 2010-06-05
Hi All,

I am looking to build a VirtualBox Setup to be used in Kisok mode.

I want people to have RDP / VNC connection to my Virtualbox machine. and then they can login / logout but would not be able to shutdown the machine.


My Host would be Ubuntu 10.04 LTS or CentOS.

Guest would be Ubuntu 10.04, CentOS, Fedora.

Please guide me on how to configure the guest to attain above mentioned behaviour.

Users should be able to use system fully but not have any 
administrative capacities.


Note : I tried searching but was short of keywords to search for it.if such discussion is already going on would be happy to jump on to it.


MORE update on the same.

I am able to get the RDP on remote machine but current settings of UBuntu or any os allows it to be shutdown graphically so was stuck at that point how can i make my machine non shutdownable.

Hope you got my point.

---

### Post by BoneKracker on 2010-06-05
<deleted>

---

### Post by anantshri on 2010-06-05
Details updated.


I am more interested towards modifying the Ubuntu / Fedora / Centos to work in kiosk mode coz my RDP functionality or rather VNC functionality works great. but remote users are able to shutdown my machine which i don't want to happen.

---

### Post by BoneKracker on 2010-06-05
In normal *nix environments, normal users cannot shut down or reboot the system.  Doing so requires special privileges.  You can figure our how Ubuntu grants those privileges to normal users and revert them.

One thing you may want to consider if you are using Gnome is Pessulus, which provides an easy way to lock down an instance of Gnome.

Another thing you may want to consider, if an experimental approach is acceptable and you have the background, is LxC (Linux Containers), which is very similar to Virtualbox, but provides containment/contextualization on more dimensions (i.e., it should theoretically be much more secure).  LxC is still pretty experimental and poorly documented.

---

### Post by anantshri on 2010-06-07
Linux container looksgood but i failed to get setup for X11 in it.

secondly i would like to keep this as last option as neither i have resources nor time to work on this one.

Any more suggestions on howto lockdown the users.

---

