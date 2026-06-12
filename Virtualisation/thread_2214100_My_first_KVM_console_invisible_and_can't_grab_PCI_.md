---
title: "My first KVM: console invisible and can't grab PCI device"
date: 2014-03-30
forum: Virtualisation
---

### Post by sgofferj on 2014-03-30
Hi,

I successfully moved my perimeter firewall from Virtualbox to KVM (converted the VDI via RAW to QCOW2). All works fine - which leaves me a bit relieved as it's my first steps with KVM and some of the philosophies are a bit different. Now I have 2 remaining issues:
1.) After the booting is through, I have no display on the virtual console. I see GRUB and a ton of messages during boot but at some point, the console clears and that's it. No more display. SSH to the KVM works fine, so I'm wondering what might be wrong here.
2.) I was trying to grab the second NIC of the physical machine as PCI device, because after all, it's a perimeter firewall. I don't trust just mactapping the NIC while it's set to some RFC1918-IP on the host... But no matter what, I always get

  internal error Unable to reset PCI device 0000:01:08.0: internal error Active 0000:01:0a.0 devices on bus with 0000:01:08.0, not doing bus reset

I tried pretty much everything. ifdown'ing it (of course), even rmmod'ing the module. Still can't grab it.

-S

---

### Post by JKyleOKC on 2014-04-01
I see that nobody has replied yet, so I'll at least let you know your question isn't being totally ignored.

Unfortunately I've never used kvm so cannot be a lot of help, but it may assist you to know that since ALL virtualization must pass through the host system in order to be processed at all, it's probably not possible to capture any PCI device (or USB either for that matter) before it passes through the physical host system. How else could the signal get from the input connector to the KVM program, since the virtual machine has no physical connections to anything?

I do have a perimeter firewall, but it runs on my host system, not on any virtual machine. My production work is all done on dedicated virtual machines, and their network connections to the outside world go through my LAN, then through the perimeter firewall and out to the wide wide WAN called the Internet. I'm using VirtualBox, and have for the past seven years. The only security mishap during that time was due to my own multiple careless actions which allowed an intruder to log in through my FTP server, then find an unencrypted text file that listed several passwords. Had to reformat all physical drives on two systems, but the production VMs survived because none of them was running at the time of the invasion and I detected it before any of them had powered up. I saved the virtual drives to external disks before the reformat, and checked them closely before putting them back.

---

### Post by sgofferj on 2014-04-02
KVM should allow you to capture PCI devices. Being kernel-based should also makes this much easier :). Anyways, from a security point of view, running a perimeter firewall on a host and all your services in virtual machines on THAT host, is pretty much suicide, because if an attacker manages to get on your perimeter firewall, they immediately have full access to all your VMs!
Of course that data passes through the host on some level, but if a VM captures a device, it's not visible to the host's userland any more and even disappears from the kernel's info structures.
You can try this easily yourself - VirtualBox does support USB capture, so go ahead and capture e.g a USB mouse from the host in your VM. It won't work in the host anymore and it even shouldn't appear e.g. in lsusb on the host.

My perimeter firewall is a stripped down Ubuntu server with little more than the base system and sshd. I even removed ssh (client) from it. The storage is a read-only. The only thing going out is syslog to a syslog-server. Changes in the ruleset are done externally and written to the storage from another system. sshd, of course, only listens on the LAN if. Generally, it drops all packets directed to it from the external if. So even *if* an attacker would manage to compromise one of the nonexistent services, he would still just be sitting in a VM with a read-only file system and without any tools to continue from there - except maybe flooding my syslog server.
The only thing really missing for my perfect happiness is grabbing the NIC on PCI level, so the host OS doesn't see any packets from there any more.

---

### Post by TheFu on 2014-04-03
Got VT-d?
Are the VT-d kernel options compiled in?
[http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM](http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM)

---

### Post by sgofferj on 2014-04-03
It's an AMD Phenom 8650, so no VT-d but I am somewhat certain that it supports the AMD equivalent.

---

### Post by TheFu on 2014-04-03
The previously provided link has tests you can run to determine if that is true.
In 5min of searching, I couldn't find anything that said the CPU had AMD-Vi.  It appears to ahve AMD-v, but that isn't enough.

---

### Post by sgofferj on 2014-04-03
I saw the tests. I'll put them in my start script so I'll get an email with the results on the next reboot.

---

### Post by TheFu on 2014-04-03
> **sgofferj said:**
> I saw the tests. I'll put them in my start script so I'll get an email with the results on the next reboot.

dmesg?

---

### Post by sgofferj on 2014-04-03
home:~ # uptime
 23:29pm  up 144 days  7:19,  7 users,  load average: 1.37, 1.24, 1.24

I have called dmesg -c one time or another in the last 144 days :).

---

### Post by sgofferj on 2014-04-03
Found the solution for the invisible console: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1177772](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1177772)

---

