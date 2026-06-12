---
title: "Installing a Virtualbox HDD Directly onto a system"
date: 2009-12-02
forum: Virtualisation
---

### Post by paul_be on 2009-12-02
A friend of mine has been using Windows XP with Ubuntu in a virtual machine.  They have now decided to make Ubuntu their default system and completely remove XP.  They were wondering if it were at all possible to use the Virtualbox HDD and install it directly onto their system.  I have never come accross this situation before so I have some questions.

a) Would it be possible to rsync or scp the entire system to another system and then resize the partition?
b) Has anyone done this before?
c) Is there a better way to accomplish this task?

---

### Post by murderslastcrow on 2009-12-04
I would totally use Reconstructor or Remastersys in the VirtualBox to make an ISO on the host OS and install from that. Remastersys backs up the system as-is, password and all. Reconstructor is basically for programs and the such, but I think it includes files, too. Remastersys will be an exact recreation installable from an ISO.

If you can boot from an external USB device large enough to carry that, this would be an ideal option. Or a DVD if it's got not too much junk.

I'm sure there may be a more complicated yet direct way, but I can't think of one yet. Anyone who cares to shed some light on this is more than welcome, just putting in my two cents.

---

