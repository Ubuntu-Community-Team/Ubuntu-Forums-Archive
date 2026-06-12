---
title: "Paravitual Xen to KVM Migrations"
date: 2011-01-16
forum: Virtualisation
---

### Post by TheFu on 2011-01-16
We have about 10 **Xen paravirtual VMs** running on 8.04 x64 LTS server that we want to **migrate to KVM 10.04 x64 LTS VMs** on a different machine.  All the Xen guests are 8.04 LTS x64 which we'd like to retain on KVM.  We'd like to use virtio network drivers.  The guest disks are full images (not sparse or LVM). 

In searching for migration steps, we've found steps for RHEL - old versions of RHEL - but nothing for Ubuntu Servers.

**Anyone successfully done this paravirtual Xen to KVM VM migration?**  When I say "migration" I really mean move.

Any tips or links?

---

### Post by TheFu on 2011-01-27
Bump?

Perhaps my choice of "migration" is throwing everyone off.  "Move" would have been a better choice.  We have no need to migrate a live running system from Xen to KVM. An hour of downtime is acceptable in this situation.

Thanks for any help or leads.

---

### Post by sh1ny on 2011-01-28
We had a similar situation and we decided to just install fresh KVM vm's and move the services. It was done with minimal downtime, because we had a second/temporary server on which we did the new install, sync'd everything ( mail, samba, websites ) and then just replaced the disks on the old server with the disks from the second server.

There are a couple of guides out there how to "migrate" xen to kvm, but i found them to be too much of a "hassle" under ubuntu. Basicly, you need to install a non-xen kernel, then install grub and everything else that wasn't installed under PV , then shut them down , move them to kvm and *try* to boot. It might work or not.

---

### Post by TheFu on 2011-01-28
> **sh1ny said:**
> We had a similar situation and we decided to just install fresh KVM vm's and move the services. It was done with minimal downtime, because we had a second/temporary server on which we did the new install, sync'd everything ( mail, samba, websites ) and then just replaced the disks on the old server with the disks from the second server.

There are a couple of guides out there how to "migrate" xen to kvm, but i found them to be too much of a "hassle" under ubuntu. Basicly, you need to install a non-xen kernel, then install grub and everything else that wasn't installed under PV , then shut them down , move them to kvm and *try* to boot. It might work or not.

Thanks for spelling out what you did.

That is what I figured.  Guess it is just easier to build new VMs under KVM, migrate the old data and perform an upgrade of the application stack. Not fun, but it has to be done.  I just wish it didn't make the most sense to do Zimbra first.

---

### Post by sh1ny on 2011-01-29
> **TheFu said:**
> Thanks for spelling out what you did.

That is what I figured.  Guess it is just easier to build new VMs under KVM, migrate the old data and perform an upgrade of the application stack. Not fun, but it has to be done.  I just wish it didn't make the most sense to do Zimbra first.

Zimbra should be a breeze. You could just install zimbra on the new vm ( same version as the xen one ), stop both and copy/rsync /opt/zimbra. Works like a charm here, tho you will have some downtime :(

---

