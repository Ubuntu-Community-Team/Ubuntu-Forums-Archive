---
title: "Hardy as vmware host + hardy guests - Clock Problem."
date: 2008-05-15
forum: Virtualisation
---

### Post by loofi on 2008-05-15
Running Hardy on my HP 8710W laptop with VMware Workstation 6. Guest is running Hardy. The problem is that the clock on the guest is running slow.

I have made these configuration without any luck:

I added these lines to /etc/vmware/config: 
[I]host.cpukHz = 2401000 (Max)
host.noTSC = TRUE 
ptsc.noTSC = TRUE
[/I]
And this to guest .vmx:
[I]MemTrimRate = "0" 
sched.mem.pshare.enable = "FALSE" 
MemAllowAutoScaleDown = "FALSE" 
mainMem.useNamedFile = "FALSE" [/I]

And i am booting the guest kernel with extra parameters:
noapic nolapic apci=off clocksource=acpi_pm elevator=noop 

As far as I can see I am following the guidelines from the forum and VMware: [http://kb.vmware.com/selfservice/viewContent.do?language=en_US&externalId=1420]("http://kb.vmware.com/selfservice/viewContent.do?language=en_US&externalId=1420")

[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1591&sliceId=SAL_Public]("http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1591&sliceId=SAL_Public")

This is frustrating. Any recommendations on this issue?

---

### Post by bobnonn on 2008-05-30
I experienced this exact problem!  I had two VMware images, running side by side.  One image worked well, the clock functioned normally.  But on my older VMware image, the clock would stop moving at times.

Once I did an "Actions->Upgrade Virtual Machine" on the old image, the problem mostly disappeared.  You have to do this with the virtual machine powered off.

Hope this helps.

---

