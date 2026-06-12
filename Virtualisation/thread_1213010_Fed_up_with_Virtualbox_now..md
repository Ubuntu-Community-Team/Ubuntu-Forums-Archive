---
title: "Fed up with Virtualbox now."
date: 2009-07-14
forum: Virtualisation
---

### Post by kneewax on 2009-07-14
I have been having real problems with VirtualBox 2.2.4 for weeks now.

I use Vbox for a single XP Pro machine and have been using it for 18-months without major issue.

However the past month or so has been nightmare.

It started with a 'Delayed Write Error' in the Guest OS, this I tried to work around, initially by updating Vbox to the latest release - then when that didn't help, I found an article in this forum about shared drives on the host machine, so I disconnected all my shares.  This has not helped.

Twice now I have the guest OS crash only to discover on restart that Vbox has reverted to an old snapshot and lost all my changes.

I started to wonder if it was just a problem with this particular Guest, so I tried to build a second XP machine that I could migrate too.  This has consistently failed during XP installation.  

As a result I began to wonder if the issue was related to a bad sector where Vbox I was saving the Machine, but I have attempted telling Vbox to save on a different HDD / Partition and get the same issue - crashed installations.

Please can anyone help me diagnose what is killing my Virtual Machines.  It is costing me wqay too much time to do those simple tasks that I need Windoze for (two pieces of software that won't run with Wine, but that I need for work).

---

### Post by bodhi.zazen on 2009-07-14
Ouch, sorry you are having problems.

Which version of VirtualBox ? OSE or PUEL ?

You might want to try updating your VirtualBox , VBox is on version 3.0.2 right now.

If that does not help, try the VirtualBox forums.

I have found guests to become unstable in the past and backing up your data and re-installing Windows should help. Then take a snapshot (keeps windows nice and fresh) and keep your data of a flash drive. 

From my recollection, windows installs tend to self destruct after a while, so may not have anything to do with virtualbox.

If you want an alternate, VMware Server is freely available (I would stay with version 1.x and stay away from 2.x). VMWare can be tricky to install and maintain though.

If you have the hardware, check out KVM (I find Fedora's version of Virt-manager and KVM is a bit more up to date then Ubuntu).

---

