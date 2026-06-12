---
title: "server upgrade"
date: 2019-12-26
forum: Virtualisation
---

### Post by gian2 on 2019-12-26
hello All,

I have a dedicated virtualizer running Ubuntu server 14.04 with KVM.

Trusty is past end-of-life, so I would like to upgrade it (maybe I should wait for 20.04LTS).

The images are on a dedicated disk partition, mounted on /var/lib/libvirt/images.

I was thinking to upgrade the server to 18.04 over a weekend, office closed, turning off previously all guest machines.

Then I would simply install the host over the original / partition, avoiding (of course!) to format the images' partition.

I probably would need to backup and restore the other folders in /var/lib/libvirt.

Am I making things too simple...?

Thanks for your advice,

best,

Gian

---

### Post by TheFu on 2019-12-26
Yes, you are making it too simple.  Many things have changed and for a server, this upgrade will likely not go smoothly.  Expect issues.  I would backup everything - EVERYTHING.  Then I'd get a fresh VM with 18.04 and slowly migrate each service over to the new VM.

Canonical does provide free (no cost) ESM for 14.04, if you care to put off upgrading for a few more years.

Many base things have changes.  The networking subsystem is all different.  The init system is all different. There are funky changes in both of those.  Newer releases bring more capabilities for the hypervisor, so you might want to consider a few changes with those as well.  Some single-service VMs might be better as Linux Containers, for example.

Last time I attempted a migration like this, it required 5 attempts before it was smooth enough to attempt in production.  For something like this, I always move to new hardware running a newer hypervisor and do 1 VM at a time.  That can be fairly low risk.  Did about 12 VMs last spring that way, but have 1 VM still on the older VM host which will likely lose support in January.  When that happens, I won't need to migrate it at all.  If it doesn't happen, which is highly doubtful, I'll move it over to the newer VM host and expect issues that will take a few hours, minimum, to resolve, assuming that is even possible.

Backup anything you can't afford to lose.  If you aren't positive you can get it back, I'd rethink the backups until I was.

---

### Post by gian2 on 2019-12-27
thanks, TheFu,

I agree with everything.

I also thought to renew the hardware, or at least, drop in new disks, although they look ok (cat /proc/mdstat and SMART).
After all, they have been spinning for 5yrs+.

However, maybe I did not make myself clear, I planned to format the boot partition, so, for all accounts it would be a new install from scratch.
Only the VMs should stay intact, but I would expect them to be independent from the hypervisor, provided that the machine definition is the same.

---

### Post by TheFu on 2019-12-27
> **gian2 said:**
> thanks, TheFu,

I agree with everything.

I also thought to renew the hardware, or at least, drop in new disks, although they look ok (cat /proc/mdstat and SMART).
After all, they have been spinning for 5yrs+.

However, maybe I did not make myself clear, I planned to format the boot partition, so, for all accounts it would be a new install from scratch.
Only the VMs should stay intact, but I would expect them to be independent from the hypervisor, provided that the machine definition is the same.

The boot partition is just the kernel usually. That isn't the entire OS. Really need to wipe everything off any disk that holds anything part of the OS and do a fresh install.  Linux VMs usually migrated easily.  Windows VMs sometimes require a fresh VM install.

---

