---
title: "Running Windows installed as dual boot from Linux"
date: 2010-03-11
forum: Virtualisation
---

### Post by pmatos on 2010-03-11
Hi all,

I am not even sure this is considered virtualization but here it goes nonetheless.
I have windows installed as a dual-boot to Ubuntu. I would like to run the Windows (the one installed on the other partition) from Ubuntu. How can I do this?

I know I can use something like VirtualBox to have a virtual machine but I don't think this is exactly the same, because the windows is already installed and living in a separate partition.

However, it seems to be this ought to be possible.

Any tips?

Cheers,

PMatos

---

### Post by dcstar on 2010-03-11
> **pmatos said:**
> Hi all,

I am not even sure this is considered virtualization but here it goes nonetheless.
I have windows installed as a dual-boot to Ubuntu. I would like to run the Windows (the one installed on the other partition) from Ubuntu. How can I do this?

I know I can use something like VirtualBox to have a virtual machine but I don't think this is exactly the same, because the windows is already installed and living in a separate partition.

However, it seems to be this ought to be possible.


It is possible to "run" existing physical partitions as VMs but it is essentially insane.

All PC operating systems work on the assumption that they have exclusive and sole control of any resources - like direct attached disk storage.

When a host PC boots up, it controls these resources and any VM software has to access these resources indirectly via the host OS, so the "rule" that the host OS has exclusive access holds.

If you allow a VM to bypass the host OS and access a disk partition, then you now have two running OSs believing that they **both** have exclusive control of this single resource - I will leave it to you to ponder the possible issues this may case to the data on that disk.

Yes it is possible, but like so many other things it is a really bad way to do things.

---

