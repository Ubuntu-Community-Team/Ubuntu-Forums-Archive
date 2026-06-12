---
title: "Looking for help in scsi-target product find and decision"
date: 2012-12-11
forum: Server Platforms
---

### Post by mabra on 2012-12-11
Hello !

I am looking for the "right" scsi-target for my Ubuntu 12.04 (precise).
I am searching for days now and I am finally not able to find a product
with a reasonable documentation. I probaly even do not know, which
products are "ready-to-use" know, and probably, I did'nt find all relevant stuff.

I found "open-scsi", "lio", "scst", "iscsi-target", "iet", "istgt", "tagt" and I am finally completely disoriented ....

Many of them are not in the 12.04 repos ...

Best option would be to support VHD files and beeing based on
kernel-modules ...

The best I found [well documentes, feature rich, kernel-modules] is - so far I imagine - "scst", but I found no "ready-to-use" package. But
I got no answer for my question on their mailing list.

Any help would really be "ultra-great" ;-)

Thanks anyway and
best regards,

++mabra

---

### Post by tenmoi on 2012-12-11
I recommend this
[http://linux-iscsi.org/index.php/LIO-Target](http://linux-iscsi.org/index.php/LIO-Target)

It's production ready and targetcli is the easiest to use as far as I am concerned.

Cheers

On Precise, all you need to do is, 'apt-get install targetcli' and everything is installed and awaiting your administrative skills.

---

### Post by mabra on 2012-12-13
Hi !

Thanks !

LIO is one possibility, but this one has no options. Even
"istgt" can host VHDs, but this is not a kernel module.

Regards,
++mabra

---

### Post by tenmoi on 2012-12-13
> **mabra said:**
> Hi !

Thanks !

LIO is one possibility, but this one has no options. Even
"istgt" can host VHDs, but this is not a kernel module.

Regards,
++mabra

What do you mean with 'but this one has no options'?
Have you looked at this, 'http://linux-iscsi.org/index.php/LIO-Target'?

Please read the BACKSTORES section carefully. Does VHDs mean 'virtual hard disk'? You can use vdfuse to mount them then. 

Cheers.

---

### Post by mabra on 2012-12-14
Hi !

I am currently using "istgt", because it can host my VHDs [yes:virtual hard disk].
See: [http://osdir.com/ml/freebsd-scsi/2012-09/msg00022.html](http://osdir.com/ml/freebsd-scsi/2012-09/msg00022.html)
This works basically, but is not a kernel imlementation and so probably
does not give me high performance, like all FUSe related things are
missing this ...

Thanks for the page to LIO; Knowed it, but - up to now - havent had the
time to read that all.

I was more familar with this:
[http://scst.sourceforge.net/comparison.html](http://scst.sourceforge.net/comparison.html)

It is a shame, that there are two projects at work, but not one
really ready-to-go. What does this tell me about the influence of
the linux community ?? .... Just irritated ... Both have it's pros
and cons.

Will - at next - make a VM with LIO, to see, if it works with
ZFS on boot.

Thanks!
++mabra

---

