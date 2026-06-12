---
title: "Ubuntu 14.04 LTS 64bit guest OS kernel panic on start up"
date: 2016-05-16
forum: Virtualisation
---

### Post by galapogos on 2016-05-16
Hi,

I have a Ubuntu 14.04 LTS 64bit guest OS running on VMWare Workstation 12 Player on a Windows 10 host. I was running Eclipse for a while recently when it got really slow despite multiple Eclipse restarts, so I decided to reboot the guest OS. It froze on the GUI desktop either shutting down or booting up, so I rebooted down using VMWare. After this, I kept getting kernel panics with the following errors:

run-init: /sbin/init: No such file or directory
Target filesyste doesn't have requested /sbin/init
run-init: /sbin/init: No such file or directory
run-init: /etc/init Permission denied
run-init: /bin/init: No such file or directory

I think my filesystem must have been corrupted somehow. How do I fix this problem?

Edit:

I tried to boot into a Live DVD by loading the 14.04 DVD ISO as the DVD drive and checking "Connect at power on". I then started the VM and selected the DVD drive in the boot menu. However, it still booted up from my hard drive. Interestingly, there's a + sign next to the hard drive and not next to the DVD drive. Does that mean anything?

---

### Post by galapogos on 2016-05-16
Is there any other way of accessing the guest OS file system? Perhaps by mounting the disk image which is probably somewhere in the VM files?

---

### Post by MAFoElffen on 2016-05-16
Since you are posting this, we can assume that you don't have a recent snap-shot to fall back to. Before you try anything, you might want to clone you VM so you at least have a copy of where you are at now. That way you don't go worse-off.

It sounds as if, when you did a system forced restart, from within the VM Manager, that it saved the state of the corrupted / blown out session. A forced reboot is different than a forced shutdown (shut off). But you need to ensure that the system settings are not saving the session state when you do so. That way the system can start fresh from a cold boot.

On you not being able to start from a LiveCD iso, you first need to do a shutdown of the VM, then change the boot up order setting in the VM settings... Either way, you need to completely shutdown the VM.

On mounting a VMware disk to a Win Host system, the pre-req is still to first completely shutdown the VM:
[https://pubs.vmware.com/workstation-9/index.jsp?topic=%2Fcom.vmware.ws.using.doc%2FGUID-896E61F5-0865-4D3B-975E-DE476AFC7168.html](https://pubs.vmware.com/workstation-9/index.jsp?topic=%2Fcom.vmware.ws.using.doc%2FGUID-896E61F5-0865-4D3B-975E-DE476AFC7168.html)

---

