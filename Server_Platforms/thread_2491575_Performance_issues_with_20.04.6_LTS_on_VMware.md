---
title: "Performance issues with 20.04.6 LTS on VMware"
date: 2023-10-13
forum: Server Platforms
---

### Post by penobscot on 2023-10-13
I have a remote consultant coming in via SSH to set up a mail server. He has complained about performance issues despite 4vCPUs and 16GB. One complaint is that atop shows up to two cores disappearing. Another is that screen echo is very slow.

In running esxtop, this is the only VM with any significant %VMWAIT; the others are usually < 1 and this VM may approach 20 but is typically between 5 and 10. I understand this is a possible [cosmetic issue]("https://kb.vmware.com/s/article/85393"), but would like to get an answer.

I'd like to know what to look for both on this server and in vCenter. We're replacing the modem in case it's contributing to latency, as it's old and this is the only connection that uses it, so we might not have noticed an issue before. This is the only Linux VM on this host; the Windows VMs are all fine. We have Photon and SUSE machines running well on other hosts. 

vCenter is 7.0.3 and open-vm-tools are 11.3.0.

Thanks for any help.

---

### Post by TheFu on 2023-10-13
1. Check the system logs.  Look for warnings and errors.  

2. Providing too many vCPUs and too much RAM on a shared system can be an issue too.  

A typical postfix server doesn't need anywhere near what you've given to the system, but it depends on load.  If you want performance, tune the setup to prevent swapping and use SSDs for storage.  Ensure RAM is sufficient to minimize the required swap ... target less than 500MB for swap. Some swap is needed to enable some kernel features, but you really don't want to have that swap used much.
Use virtio for networking and storage devices too.  Avoid emulating real hardware, though it really shouldn't matter THAT much.
Lastly, if you have a volume manager, those can drastically improve performance compared to file-based VM storage.  I don't know what VMware ESXi supports in this area.

---

### Post by MAFoElffen on 2023-10-13
I do some beta testing on VMware vSphere... and since I do support here, I tend to install and test a lot of Ubuntu VM's in my test cases.

Is open-vm-tools installed in the vm guest? That alone will improve an Ubuntu VM guest on VMware hosts, no matter which product.

Here are some things I do for the VM guest setup to make them faster:

[LIST]
[*]I setup the vmdk storage files to static instead of dynamic. They just perform faster.
[*]I open the virtual machine configuration file and set these options to FALSE: tools.syncTime, tools.synchronize.restore, time.synchronize.resume.disk, tools.syncTime, tools.synchronize.restore, time.synchronize.resume.disk, time.synchronize.continue, time.synchronize.shrink, time.synchronize.continue, time.synchronize.shrink
[/LIST]
 
Not just for Ubuntu, but Linux server VMs in general, sometimes a VMware host wants to fight over who's in charge with I/O scheduling. It's easier to just change the algorythn to FIFO on the guest and like the VMware host take care of it, so there is no time wasted in that coordination between the two. I got these tips from RedHat VM tuning tips, for how to just change the elevator to NOOP scheduling, by adding "noop=elevator" as a kernel boot parameter in the /etc/default/grub file, GRUB_CMDLINE_DEFAULT_LINUX+ line. This works for Ubuntu Server also. Remember to use update-grub to pickup the change. 

You can see what it is set to in the Ubuntu VM via:
```

grep . /sys/block/[s,n][v,d]*/queue/scheduler

```

I try to remove devices that are not needed by the specific VM, leaving only what is needed to do it's job. I keep an eye on the metrics in vCenter under it's loads and adjust as needed. I usually start out with 2vcpu's and what I calc as the RAM needed, then adjust from there.

---

### Post by penobscot on 2023-10-16
Thanks, everyone for the responses. The modem was the source of the latency.

open-vm-tools 11.3.0 is installed. Is there a benefit to going to the current version?

System is specced per the consultant's request with regard to vCPUs, RAM, and no LVM.

What would I look for in the logs? dmesg looks OK. syslog has a lot of errors but they seem tied to two devices consultant asked for that haven't yet been partitioned/formatted/mounted

I'll try @MAFoElffen suggestions.

---

### Post by MAFoElffen on 2023-10-17
Current is 2:12.1.5-3~ubuntu0.22.04.3: [Change Log]("http://changelogs.ubuntu.com/changelogs/pool/main/o/open-vm-tools/open-vm-tools_12.1.5-3~ubuntu0.22.04.3/changelog")

Beside the upgrade and applying patches... It fixed 14 Bugs and applied 2 Security CVO's fixing vulnerabilities. So yes, I would get current on that.

---

### Post by penobscot on 2023-10-18
Forgive the noob question, but how do I do this? 11.3 is the latest available. The repositories are all pointed at [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu). When I add [http://mirrors.kernel.org/ubuntu](http://mirrors.kernel.org/ubuntu) (or anything) and try to update, I get both "403  Forbidden" and a warning that the repository isn't signed. Thanks

---

### Post by MAFoElffen on 2023-10-18
Oh dang... nevermind... I checked the package for 22.0.

Going back to this thread... I just noticed post #1 said 20.04 open-vm-tools (2:11.3.0-2ubuntu0~ubuntu20.04.6)... Those should be backported for Jammy through jammy-backports and security updates. Yes, I see that the CVE's were applied ([http://changelogs.ubuntu.com/changelogs/pool/main/o/open-vm-tools/open-vm-tools_11.3.0-2ubuntu0~ubuntu20.04.6/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/open-vm-tools/open-vm-tools_11.3.0-2ubuntu0~ubuntu20.04.6/changelog))

---

