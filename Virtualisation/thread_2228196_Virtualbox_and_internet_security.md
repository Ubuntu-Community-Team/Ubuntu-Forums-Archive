---
title: "Virtualbox and internet security"
date: 2014-06-06
forum: Virtualisation
---

### Post by gillfarmer3 on 2014-06-06
I have got Windows7 running in Virtualbox on Ubuntu 14.04 solely so I don't have to keep changing drives for iTunes.

Do I need to look at getting internet security?

---

### Post by brantcgardner on 2014-06-06
Yes, if you are referring to an antiviral/antispyware/antimalware solution.  A virtualized copy of Windows is just as vulnerable as a non-virtualized copy and all the protections you need still apply.

---

### Post by nknwn on 2014-06-06
It depends I think on how you use the Virtual machine.
If you regularly roll back your Guest OS (in your case Win7) to a Snapshot then you probably don't need anti virus
If you don't roll back your Guest OS to a Snapshot regularly then you probably should use anti virus in Windows 7.

When you roll back your Guest OS to a Snapshot you lose all the changes in it including the user files you have created or modified. 

However, if you save your user files in the Ubuntu side, in a shared folder, accessible from your Guest OS, that is one way to be able to refresh your guest OS to a Snapshot without losing the user files you have have created. (Because they are safe and sound on the Ubuntu side).

---

### Post by TheFu on 2014-06-06
Yes, unless the VM is never on any network. Best to remove the networking subsystem.  Otherwise YES!!!! You need all the security you can get! It is Windows, afterall, which is the largest target for all the nastiness out there.

---

### Post by gordintoronto on 2014-06-06
Install Microsoft Security Essentials and keep it up to date.

---

