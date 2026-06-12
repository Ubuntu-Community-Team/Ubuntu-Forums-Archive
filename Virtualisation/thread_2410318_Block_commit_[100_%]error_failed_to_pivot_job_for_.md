---
title: "Block commit: [100 %]error: failed to pivot job for disk"
date: 2019-01-14
forum: Virtualisation
---

### Post by totla on 2019-01-14
Hi,

i have a problem with my VM backups.

I have a script that automatically backups .qcow2 images of running VM's everynight via external snapshots, but lately few of my larger servers have started failing on making backups successfully.

Here is my backup process:
backup for guests with guest-agent:
```
virsh snapshot-create-as --domain "$DOMAIN" --name backup --no-metadata --atomic --quiesce --disk-only $DISKSPEC >/dev/null
```
and for guests without:
```
virsh snapshot-create-as --domain "$DOMAIN" --name backup --no-metadata --atomic --disk-only $DISKSPEC >/dev/null
```

Then i proceed to copy the base.image....

```
virsh blockcommit "$DOMAIN" --active --wait --pivot
```

And here is where it gets stuck with the error :```
[B]Block commit: [100 %]error: failed to pivot job for disk sdb 
error: block copy still active: disk 'sdb' not ready for pivot yet[/B]
```

The guest in question has 2 .qcow2 disks, the blockcommit is successful for the first disk image (**sda**) but not for the other (**sdb**).

I tried fixing the problem by manyally aborting the blockjob, which is successfull, but then i get the same error on blockcommit.

```
root@server1:/var/lib/libvirt/images/Domain1# virsh blockjob Domain1 sdb --abort

root@server1:/var/lib/libvirt/images/Domain1# virsh blockcommit Domain1 sdb --wait --active --verbose --pivot
Block commit: [100 %]error: failed to pivot job for disk sdb
error: block copy still active: disk 'sdb' not ready for pivot yet
```

Any help on this is appreciated, thanks.

---

