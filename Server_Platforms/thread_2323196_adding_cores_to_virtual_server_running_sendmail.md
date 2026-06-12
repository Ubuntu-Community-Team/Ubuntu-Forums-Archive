---
title: "adding cores to virtual server running sendmail"
date: 2016-05-03
forum: Server Platforms
---

### Post by ghughes on 2016-05-03
Good morning, all!
I am tuning a new set of mail servers running Ubuntu 14.04 LTS and sendmail.  These are virtual machines in a VMware vSphere 5.5 environment.

I may need to add CPUs, either cores or virtual sockets, to these VMs.  Is there any tuning necessary in the operating system to successfully integrate the changed CPU settings?

Thanks to all for looking!

Gregg

---

### Post by ajgreeny on 2016-05-03
Is it a 32 or 64 bit Ubuntu VM?

I have not managed to get a 32 bit VM of Ubuntu to use more than a single core of my quadcore machine.
I do not know if this is simply because it is 32 bit, or if it is because I have not changed some setting or other in VBox, but it is only single core and if I try to add other cores in the VM settings manager it shows an "Invalid setting" error.

---

### Post by darkod on 2016-05-03
I wouldn't say you need anything special for the OS to see all cores you present to it. Also, virtualization is designed to be transparent, and I would expect that especially from vmware.

In reference to what ajgreeny said above, I know I have 32bit CPU on my HP Microserver and I just checked how many cores it sees, and it does see both cores (it's 32bit ubuntu server). Of course, this is a physical machine, not a VM. But I would expect to see all cores on VBox too. Will have to do a test when I have more time... :)

---

### Post by ajgreeny on 2016-05-03
> **darkod said:**
> <snip>In reference to what ajgreeny said above, I know I have 32bit CPU on my HP Microserver and I just checked how many cores it sees, and it does see both cores (it's 32bit ubuntu server). Of course, this is a physical machine, not a VM. But I would expect to see all cores on VBox too. Will have to do a test when I have more time... :)

In view of darkods comment above I have just played around with my 32 bit VMs and after a bit of fiddling with the settings I have found that if select **Enable I/O APIC** in the Extended features of the Motherboard in the system tab, I can raise the number of cores to my total 4 cores with no error message.

I had never even considered this before as it is a VM I use merely to test Xubuntu-core, but it does mean that I, and hopefully others have learned something new.  Also it allows my Windows XP 32 bit system to use more than a single core.

As I say, you live and learn!

---

