---
title: "KVM Storage"
date: 2015-05-20
forum: Virtualisation
---

### Post by Sreejith_P on 2015-05-20
Hello All,

I have added a second storage pool to KVM.

[ATTACH=CONFIG]262091[/ATTACH]

But when i try to create a vm there are no options to chose a different storage pool. It chooses the default storage pool

[ATTACH=CONFIG]262093[/ATTACH]


[ATTACH=CONFIG]262092[/ATTACH]


Please let me know how can i change the storage path for the vms harddisk like what we can do in virtualbox or vmware player

Thanks,
Sreejith P

---

### Post by KillerKelvUK on 2015-05-20
Hey, your first screenshot only shows that you've created the pool it doesn't show its active.  Assuming it is active and you have that covered then the 2nd screen show shows that you are just creating vm's as per the default settings...as you have a 'default' storage pool thats what the default vm create wizard will use.  What you need to do is "select managed or other existing storage" (on your 2nd screen shot) which will bring up your storage pools and allow you to manually provision a vm against the available pools

---

### Post by TheFu on 2015-05-21
I haven't looked at this too hard, but ...

You can always manually edit the XML file created by libvirt **virsh edit {vmname}** and put in the correct path.
Or
You can create softlinks to the new location. Both of these methods mean you probably made the virtual HDD file manually, perhaps using QCOW2 sparse allocations.

---

