---
title: "KVM - How to remove VM"
date: 2009-07-23
forum: Virtualisation
---

### Post by satimis on 2009-07-23
Hi folks,

KVM

How to remove/delete VM (client) on command line instead of on Virt-manager.

Ex.
$ sudo virsh --connect qemu:///system

virsh # list --all```

 Id Name                 State
----------------------------------
  - vm10                 shut off
  - vm11                 shut off
  - vm13                 shut off

```

I expect to remove vm10 and vm11.  The later was cloned on the former.

Furthermore;

$ apt-cache policy uml-utilities```

uml-utilities:
  Installed: (none)
  Candidate: 20070815-1.1
  Version table:
     20070815-1.1 0
        500 http://ftp.hk.debian.org lenny/main Packages

```

Do I need uml-utilities ?  What will be its use?

TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-07-23
uml utilities are for making a bridged network interface and you need it if you are using bridged networking.

If you do not know what that means I would probably just leave it.

It is a small point, but important. You are not really using kvm, you are using virsh which is a front end to kvm. If it were kvm you simply delete the (virutal) hd

You run kvm with 

```
kvm -hda /path_to/ubuntu.qcow2 -other_options
```For virsh, see man virsh :

[https://help.ubuntu.com/community/KVM/Managing](https://help.ubuntu.com/community/KVM/Managing)

```
virsh # destroy vm10
virsh # destroy vm11
```*note virsh = the vish console not a command to enter.

Edit: the only reason I make the distinction is kvm has a number of options not available to the various front ends and management of teh guests depends on the front end you are using. So IMO better to ask "How to use virsh" rather then "how to use kvm".

---

