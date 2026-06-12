---
title: "Save/Restore libvirt guest on shutdown/boot"
date: 2008-10-20
forum: Virtualisation
---

### Post by Speedster on 2008-10-20
I searched the forums and Googled for a solution for this but could not come up with one... so I created the solution myself! :)

Basically this emulates what CentOS/RHEL does with Xen domains should the management OS reboot - saves the domain state to a file and restores it next boot. You might be wondering why it has to try three times to restore the domain - I'm not sure why it fails to restore but if you attempt it again after a few seconds it works fine.

the scripts are listed in this [HOWTO]("http://docs.google.com/Doc?id=drjq7vn_0ctn8k3dd") at section 5.2.

Comments welcome.

---

### Post by neilblue on 2008-10-26
Thanks Speedster,

I was suffering from the vm hdd becoming corrupt from abrupt shutdowns.

Cheers
Neil

---

