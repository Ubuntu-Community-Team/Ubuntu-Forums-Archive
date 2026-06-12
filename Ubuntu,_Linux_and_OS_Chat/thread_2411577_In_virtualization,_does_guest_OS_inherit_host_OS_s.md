---
title: "In virtualization, does guest OS inherit host OS security?"
date: 2019-01-31
forum: Ubuntu, Linux and OS Chat
---

### Post by him610 on 2019-01-31
I don't have in virtual systems installed, but there is something I have been wondering about...
If you install Windows 7 as a guest OS in a virtual system: KVM, Virtualbox, VMware, etc, does the host OS, *buntu, provide any security to the guest OS. 
Does the guest OS inherit host OS security?

---

### Post by TheFu on 2019-02-01
Sorta, but not really.  

The hostOS has features that can make Windows easier to recover after pwnage, like LVM snapshots.
Also, the host networking can be configured in different ways to protect the guests or not.

We treat all our KVM guests like physical machines and don't make use of much hypervisor-specific capabilities for any purposes.  If I need a remote desktop into a desktop VM, I setup x2go inside the VM.  The VM host doesn't know anything about that.  When we do backups, the backup server connects to each VM (and the host) like they are each physical machines and does the "pull" backups nightly.  We have been playing with sheepdog for backend, redundant, storage replicated across multiple nodes and that is tied to KVM specifically, but that's the only thing I think we do specific to the hypervisor.  I wasted about 4 yrs trying to get solid, fast, efficient, backups working treating the VMs like they were VMs. In the end, that was a waste of time and just too slow.  I suppose some smarter people may have found a way to use the hypervisor features to accomplish daily, versioned, fast, efficient with storage backups, but I've never seen any.

All hypervisors are not created equal.  Each has strengths and weaknesses that you'll want to decide during or before you deploy based on your needs.

---

### Post by mastablasta on 2019-02-01
> **him610 said:**
> 
If you install Windows 7 as a guest OS in a virtual system: KVM, Virtualbox, VMware, etc, does the host OS, *buntu, provide any security to the guest OS. 
Does the guest OS inherit host OS security?
it doesn't inherit. in fact an infected windows in VM can (potentially) influence files in Ubuntu. the only thing that is worth mentioning here is that os in VM can be sand boxed/ jailed / closed off. so you can infect the WM but not Ubuntu for example.

---

### Post by TheFu on 2019-02-01
It is worth noting that VMs aren't 100% protection for the host and definitely not for the LAN. 

[https://www.techrepublic.com/article/10-new-vm-escape-vulnerabilities-discovered-in-virtualbox/](https://www.techrepublic.com/article/10-new-vm-escape-vulnerabilities-discovered-in-virtualbox/) is about virtualbox, but every hypervisor has had VM breakout issues.

What we each should do and the level of our concerns for these risks depends on what is at stake.

---

### Post by him610 on 2019-02-03
TheFu and mastablasta, thanks for the advice. 

I have one seldom used legacy machine that dual boots LTS 16.04 and Win7. The only application I use with Win7 is tax software once a year to do my taxes. I was considering donating the legacy machine (along with other computers that I need to get rid of) and rehosting Win7 in a virtual machine on a newer computer, and wanted to get an idea of what risks can be expected.

---

### Post by SeijiSensei on 2019-02-03
If you're only going to use the VM once in a while, like to do taxes, I don't see much of a threat.

---

### Post by TheFu on 2019-02-04
The danger in using Windows comes from open access to the internet and by sharing infected files on the LAN.  If you only use Windows for specific purposes, like taxes, and it is only used to retrieve data for that program, then I wouldn't worry about it.  

Just don't do high risk activities with it, like reading email or using a browser.  This is is advice for any Windows user, IMHO.

---

### Post by jdeca57 on 2019-02-05
A problem is that support for Windows 7 goes to jan 2020 and then it ends. And that there is still a huge user base so that exploits may be found and circulate on the internet. I wouldn't use 7 in 2020 but then again I don't use it now.

---

### Post by mastablasta on 2019-02-06
> **jdeca57 said:**
> A problem is that support for Windows 7 goes to jan 2020 and then it ends. And that there is still a huge user base so that exploits may be found and circulate on the internet. I wouldn't use 7 in 2020 but then again I don't use it now.

meh, 3rd parties still make good security software (antivirus, firewall, various unwanted app blocking...) for winXP... sometimes you need to pay for it but it still makes the OS safe to use. 

so win7 and 3rd party support for it, is definitely going to linger around for a while. particularly with some currently exposed win 10 upgrades issues. so while it wont be the safest OS option out there, it will be good enough to so some taxes on it maybe even play a game or two. :)


i am *a WindowsXP user. *but lately it get's fired up only on weekends for a game or two. and even this is not every week lately (discovering steam and the tricks and traps of linux gaming)
and tax report this year was really smooth under linux (they even prepared us a .deb file, and nice install instructions for signing component). now if all our government agencies and such could move to this tool it would make life a lot easier.

---

### Post by TheFu on 2019-02-06
If you don't use the OS on the internet, no browsing, no emails, no hinky things, and your LAN doesn't spew viruses, there isn't much risk for using an unpatched OS.

AV is only 50% effective. [https://www.csoonline.com/article/3146996/malware-vulnerabilities/is-antivirus-software-dead-at-last.html](https://www.csoonline.com/article/3146996/malware-vulnerabilities/is-antivirus-software-dead-at-last.html) It provides a false sense of protection that doesn't exist.  Viruses are self-modifying as they replicate to avoid detection.  I haven't used AV since 2012-ish.  But I don't do high risk activities with Windows.  From 2008 - 2012, only had AV running due to contractual mandates for E&O Professional Insurance.  It never found anything.

BTW, I was hacked in 2016 ... through bluetooth ... on a fully patched Ubuntu while at a conference. I've had Linux installs hacked a few times prior to that, but not recently. Nothing teaches more about security than being hacked.  2002 and 1993-ish are when the other two hacks happened.

---

### Post by lammert-nijhof on 2019-02-09
No inheritance, but you can make your whole setup more safe and secure. 

I do all my financial stuff like banking and Paypal in a virtual machine (VM) and that has the following advantages:
- Use the VM for that purpose exclusively. No other browsing means no chance on contamination.
- You system is only online for minutes per day.
- Your firewall can block all inbound traffic.

I test all new Apps and other stuff first in a Test-VM. So if something goes wrong, I roll back to a previous snapshot or restore the VM from a backup.

If I have any problem with Windows, I can roll back to a previous snapshot or restore the Windows-VM from a backup.

I wanted to re-apply an old Pentium as PC for visitors, mostly children of family and friends. I wanted to use BTRFS with two IDE disks in Raid-0 and LZO compression, to speed up the disk IO. BTRFS was completely new for me, so I could try out the whole setup of that Pentium in a VM.

I use the Host facilities to keep my Virtual Machines in good shape.
- I use ZFS to store my Virtual Machines (VM) and I use ZFS to snapshot and back them up weekly. ZFS only adds the changed blocks to the backup, so my backup of 200 GB of 15 Virtual Machines to an USB-2 HDD takes mostly less than 30 minutes. ZFS has many other advantages like; efficient compression (lz4); memory and SSD caching; never anymore corrupted files due to power-fails or system crashes. 
- If you use ext4, you could also use Virtualbox to create the snapshots and use rsync or grsync to back them up. Probably the best way to start, concentrate on one problem first.
- You could also use BTRFS and except SSD caching it would give you the same facilities as ZFS.

---

### Post by him610 on 2019-02-17
To everyone who responded to the discussion, thank you.
You all have given me several ideas to consider

---

