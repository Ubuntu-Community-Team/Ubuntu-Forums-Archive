---
title: "Ubuntu 18.04.4 KVM PCI Passthrough Stopped Working"
date: 2020-02-24
forum: Virtualisation
---

### Post by quadphile on 2020-02-24
Above all: it had historically worked, hopefully someone out there knows which stones to squeeze for useful logs to find what broke.

The problem I now face is that if I use virt-manager to add a PCI device for passthrough the VM no longer starts, and the host has something hang which prevents the machine shutting down indefinitely.  Each time I try something I now must "yank the cord" because it won't turn off which is infuriating. A dirty reboot then scans for errors during boot and before long each test takes 20+minutes.  virsh and virt-manager become unresponsive after a failed VM start attempt.

System:
Intel e3-1245g
Ubuntu 18.04 originally installed
Uses ZFS for VM datastore

Using KVM, virt-manager and attempting to pass the network card to the guest (host has 4 identical Intel NICs)

Problems began approximately when Ubuntu 18.04.4 was released but I hadn't installed any updates yet, it had been working in early Feb 2020.
[LIST]
[*]started with 18.04.?3? and all was working
[*]guest performance dropped catastrophically for unknown reasons
[*]performed update/upgrade
[*]VM guests with NIC passthrough stopped working
[*]troubleshooted it for day 1, trying to find relevant logs
[*]gave up, formatted after the repeated cord yanks killed the original installation
[*]installed 18.04.4
[*]installed KVM with the 18.10 instructions thinking that would align with the newer 18.04.4 release: [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)
[*]still faced with the same problem, attempting to start the VM while with PCI passthrough of the desired NIC does not work, no apparent problems in libvirtd logs, and host machine won't turn off.  If VM start is not attempted it will turn off.
[/LIST]
I noticed that before this problem, the extra NIC would disappear gracefully from the host when starting the guest, I presume that what is hanging is that the guest can't get control of the NIC for passthrough like it used to which is why virsh then stops working and the system can't shut down.

I will try vfio to hijack the NIC from the host, but it did not need that extra effort before.


[LIST]
[*]journalctl has been used for libvirtd logs
[*]I looked at the ones mentioned here [https://blogs.oracle.com/oda/kvm:-troubleshooting-with-log-files](https://blogs.oracle.com/oda/kvm:-troubleshooting-with-log-files)
[*]the client log doesn't exist, so its hanging before the client VM starts, the host doesn't crash completely, it remains responsive
[*]I was unable to manually unbind the host's driver from the desired NIC but I'm not familiar with that process, its using the igb driver, I wrote the address to its unbind file like I saw in other forums and no success
[/LIST]

Where should I be looking for logs to determine what's hung when a guest VM attempts to start, doesn't and causes some unknown process to block indefinitely, and the NIC doesn't disappear on the host as expected?

Thank you for your assistance,

---

### Post by quadphile on 2020-03-07
For others' sanity, after all manner of reinstalling old 18.04 LTS (that used to work) and hitting the same problem, I eventually found that there was a General Protection Fault occurring when the igb driver attempts to unbind.  It was found by watching an unfiltered system log and starting the VM.  That finally found what is likely the smoking gun.  "-u" can be used to filter it to libvirtd if you're looking for something similar but not the same issue.

**journalctl -f**

References:
On 18.04 with no intentional updates, I have the same Kernel as this unfortunate person, and it has the same hanging "doesn't turn off" behavior:
[https://bugs.launchpad.net/ubuntu/+source/linux-signed/+bug/1865280](https://bugs.launchpad.net/ubuntu/+source/linux-signed/+bug/1865280)

Someone at Intel seems to have detected the problem in early January, which I assume was why 18.04.4 originally died since the fix is in Kernel 5.5 (or later?), I'm not familiar with how widespread the commit would be either (ie did the flaw hit Kernel 4 as well as 5?) and I assume that whatever is getting downloaded during the clean install of 18.04 with no intentional updates is putting the flaw back:
[https://lore.kernel.org/netdev/3d2bd09735dbdaf003585ca376b7c1e5b69a19bd.camel@intel.com/](https://lore.kernel.org/netdev/3d2bd09735dbdaf003585ca376b7c1e5b69a19bd.camel@intel.com/)

---

### Post by quadphile on 2020-03-15
My issue can be considered resolved.

In case someone else hits the same problem, I was unsuccessful to use the methods others describe to capture the NIC by the vfio -pci driver before the igb driver due to the relative timing of when the .conf files are acted on and when the igb driver latches onto the NIC.

What ended up working was to put "blacklist igb" into /etc/modprobe.d/blacklist.conf

Then later, when vfio-pci is inserted by a *.conf file in the folder /etc/modprobe.d/, a script gets called and puts the text "vfio-pci" into only the intended NIC cards' /sys/bus/pci/devices/$DEV/driver_override (where $DEV is a list of the PCI addresses) file.  My underlying problem is one of four identical NICs was for the host to use, the other three were for the VM guests and therefore using manufacturer and model to determine whether vfio was the correct driver would have left the host without a network card.  That call to the script is in the arbitrarily named /etc/modprobe.d/local.conf file, containing the text "install vfio-pci /sbin/vfio-pci-override-nic.sh".

Inside the script after setting the driver_override files, it runs:

modprobe -i vfio-pci
modprobe igb

Interestingly the blacklist method succeeds keeping igb down long enough to manually put it back later using the script to take over control of the NICs that it was desired to attach to.

In the end all my troubles were caused by:
[LIST]
[*]a failing disk drive plugging up the system but not being declared as amiss by ZFS (high iowait % in top)
[*]then problems caused by the 5.3.0-40generic Kernel update preventing the igb driver from unbinding due to a protection fault (seen in dmesg when starting the VM).  Its symptoms were VMs not working, and the system being unable to shutdown after hitting the problem.  When the VM was to start, it would try to take the NIC and then that was the point of no return, would not start, host no longer able to shut off.  This problem is noted and to my knowledge still won't be fixed when Ubuntu 20.04 comes around.
[*]preventing igb driver from binding was also fraught with issue because it was binding before the normally described methods used for graphics cards to assign vfio were occurring after igb had bound.
[/LIST]

Hopefully that's enough to find the blogs I used as reference, I can't say I'm an expert on these matters enough to help someone. **Knowing the igb driver can't unbind in 5.3.0.40-generic kernel and to try to use the modprobe blacklist I think are the key takeaways **compared to other content you may stumble upon.

---

