---
title: "Problem with VMWare 2.0.2 on Karmic 9.10"
date: 2009-12-12
forum: Virtualisation
---

### Post by rtillsley on 2009-12-12
Hi people

I'm having a problem with VMWare on Karmic.


I run 2 vms, one a DNS server, the other a zimbra mail server. They were working fine on 8.10 until I did a fresh install on the host of 9.10. Both Guests run 6.10.

I followed this guide to get it working, including using the patch:
[http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html)
The install version of vmware was 2.0.2

The symptom I'm suffering is that the mail server powers off between 15 and 30 minutes after being turned on.

In Vmware the log shows the following error:

12/13/09 8:00:31 AM
Severity:InformationTask:Not applicableTask ID:Not applicableObject:stampTriggered By:User
Description:
Message from hosty: VMware Server unrecoverable error: (Worker#16) Unexpected signal: 6. A log file is available in "/data/VMware/Servers/stamp/vmware.log". Please request support and include the contents of the log file. To collect data to submit to VMware support, select Help > About and click "Collect Support Data". You can also run the "vm-support" script in the Workstation folder directly. We will respond on the basis of your support entitlement. 

Initially I was looking at the guest to see if there was a prob. I upgraded the vm hardware, I upgraded the tools and it made no difference. I'm reinstalled vmware, reconfigured it. Disk space was low in the guest so I added a drive and moved the /opt to the new drive.


The last part of the vmware log is as follows:

Dec 13 09:00:24.955: Worker#11| SymBacktrace[12] 00007f557ffcc110 rip=00007f558f525a04 in function (null) in object /lib/libpthread.so.0 loaded at 00007f558f51f000
Dec 13 09:00:24.956: Worker#11| SymBacktrace[13] 00007f557ffcc220 rip=00007f558ee6b7bd in function clone in object /lib/libc.so.6 loaded at 00007f558ed8c000
Dec 13 09:00:24.981: Worker#11| Msg_Post: Error
Dec 13 09:00:24.981: Worker#11| [msg.log.error.unrecoverable] VMware Server unrecoverable error: (Worker#11)
Dec 13 09:00:24.981: Worker#11| Unexpected signal: 6.
Dec 13 09:00:24.981: Worker#11| [msg.panic.haveLog] A log file is available in "/data/VMware/Servers/stamp/vmware.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.vmSupport.windowsOrLinux] 
Dec 13 09:00:24.981: Worker#11| To collect data to submit to VMware support, select Help > About and click "Collect Support Data". You can also run the "vm-support" script in the Workstation folder directly.
Dec 13 09:00:24.981: Worker#11| [msg.panic.response] We will respond on the basis of your support entitlement.
Dec 13 09:00:24.981: Worker#11| ----------------------------------------
Dec 13 09:00:25.366: vmx| VTHREAD watched thread 47 "Worker#11" died
Dec 13 09:00:25.379: Worker#21| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.379: Worker#16| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.379: Worker#3| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.383: Worker#10| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.383: Worker#0| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.383: Worker#13| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.383: Worker#9| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.384: Worker#20| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.386: Worker#18| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.386: Worker#22| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.386: Worker#2| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.386: Worker#12| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.389: Worker#24| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.389: Worker#25| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.389: Worker#6| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.389: Worker#14| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.392: Worker#8| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.393: Worker#7| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.393: Worker#23| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.393: Worker#17| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.393: Worker#19| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.455: mks| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.552: vcpu-0| VTHREAD watched thread 0 "vmx" died
Dec 13 09:00:25.583: Worker#4| VTHREAD watched thread 4 "vcpu-0" died
Dec 13 09:00:25.586: Worker#15| VTHREAD watched thread 4 "vcpu-0" died
Dec 13 09:00:25.590: Worker#5| VTHREAD watched thread 4 "vcpu-0" died
Dec 13 09:00:25.593: Worker#1| VTHREAD watched thread 4 "vcpu-0" died


If anyone can make any suggestions I'd really appreciate it, as I don't particularly want to have to go back to 8.10 or even to 9.04. 

Cheers

Robert

---

### Post by nexus_6 on 2009-12-14
I've got exactly the same problem with a Windows 2003 Guest. I'm seriously thinking about migrating to KVM, considering all the trouble VMware Server 2 has been giving me.

---

### Post by rtillsley on 2009-12-14
I installed vmware on my vista 64 machine and moved the mail server and it works fine, so its something to do with the host for sure. Nexus, I'm glad I'm not the only one.
Its interesting that you are using a w2k3 guest as well. Obviously there is some incompatibility between Karmic and Vmware. The question is, who should a bug be raised with?
I'm also thinking I might try esxi and stick the host system in a vm along with the others.

---

### Post by nexus_6 on 2009-12-14
That is indeed the question. For ESXi, good luck, the list of supported hardware is very, very short. I've had a closer look at the new kvm based cloud features in Karmic, which look very nice (along with the management tools) and set up a rough plan for migration. A solution like that just seems more elegant in the long run. 

It still would be nice to get VMware Server stable in Karmic, even if just for the transitional period.

---

### Post by rtillsley on 2009-12-14
I'd really like to keep using ubuntu as the host, but I need a working box.

My motherboard is a Gigabyte EG45M-DS2H, I think the sata controller will be fine for esxi 4, but I don't know about networking etc. I might try booting from a usb stick to test.

Cheers

Robert

---

### Post by shairozan on 2009-12-15
I agree with Nexus, good luck finding hardware to support ESXI. I was looking at buying a $400 NIC, so I bit the bullet and bought a Dell PowerEdge 2970 and just made sure all of their hardware was VMware certified. ESXI is the way to go though if you can make it work.

---

### Post by nexus_6 on 2009-12-15
[http://communities.vmware.com/thread/242151?tstart=0](http://communities.vmware.com/thread/242151?tstart=0)
might be worth a try as well.

---

### Post by t0ka on 2009-12-20
I have the same issue with Karmic, VMserver 2.0.2 and a win2k3 server.

8.10 with VMserver 2.0.0 was running for a year without any issue. I would go with virtualbox but its not as easy to manage with a headless server :-({|=

---

### Post by nexus_6 on 2009-12-20
The suggestion I posted above actually seems to help, server running for 4 days straight now, no crashes. Absolutely worth trying ;)
I'm still planning a migration though, sick of the trouble with closed-source software. ProxmoxVE (KVM/OpenVZ based) looks very good, they even have a migration video guide VMware -> ProxmoxVE. I'm testing stability & performance at the moment, very promising.

---

### Post by carlosbpf on 2010-01-07
I have been having the same problems, signal 6 after a couple of hours. I am running 3 Virtual machines, and 2 of them are hosting databases. After a little search and some tests, I came to realize that this issue ocurrs when the system is very overloaded, with severe IO. After moving one VM to another VMServer host, the problems stopped. But I am still waiting for a new version of VMServer to be released.

---

### Post by greenrenault on 2010-03-22
Sounds like the same problem with CentOS 5.4 which was a glibc issue. See this post for details and a workaround [http://bugs.centos.org/view.php?id=3884](http://bugs.centos.org/view.php?id=3884) and specifically comment (0010880)

---

