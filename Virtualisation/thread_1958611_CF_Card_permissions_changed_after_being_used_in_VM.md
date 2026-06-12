---
title: "CF Card permissions changed after being used in VMware Player ..."
date: 2012-04-14
forum: Virtualisation
---

### Post by marginal39 on 2012-04-14
And the worst thing is, I can't get to change that.
No more way to write on the CF Card in Ubuntu, only in windows under the Virtual Machine.

Please, help ...

---

### Post by dcstar on 2012-04-18
> **marginal39 said:**
> And the worst thing is, I can't get to change that.
No more way to write on the CF Card in Ubuntu, only in windows under the Virtual Machine.

Please, help ...

You probably didn't Unmount it correctly so it is set as a "Dirty" filesystem.

Do a Check on it in Ubuntu or a chkdsk in Windows.

---

### Post by marginal39 on 2012-04-18
> **dcstar said:**
> You probably didn't Unmount it correctly so it is set as a "Dirty" filesystem.

Do a Check on it in Ubuntu or a chkdsk in Windows.
I tried, now I am getting the following error message: "DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending" ...

Thanks.

---

### Post by marginal39 on 2012-04-18
Well, even after checking my backup partition on the HDD (unmounted and mounted after the check), I get a message that it is write protected ...
All those problems started after I installed a VMware ran by the VMware Player ...

Thanks.

---

