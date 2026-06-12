---
title: "Hot plug cpu core/memory document"
date: 2021-10-07
forum: Virtualisation
---

### Post by rramaiah on 2021-10-07
I'm looking for standards/document for cpu core/memory addition/deletion from virtual machine perspective. Hot plug cpu core and memory addition is available in many VMs. I'm looking for the document which could guide about implementation needs.

---

### Post by MAFoElffen on 2021-10-07
This is *not* widely "available in many VM's" as you imply.

The only one I know of that supports that is VMware vSphere, This was made available for vSphere at Version 6.5 and newer. 

That is well documented, explained and many how too's on. So I',\m not sure I understand your question(?)

There is also some pro's and cons to it. It is default for very large, resource intensive VM's, but... Using it turns off vNUMA when used. Other factors. So yes, is well documented in the VMware vSphere and ESXi docs.

---

### Post by rramaiah on 2021-10-08
Hi MAFoElffen,

Thanks for the reply. My answers inline at #rramaiah#


> **MAFoElffen said:**
> This is *not* widely "available in many VM's" as you imply.

The only one I know of that supports that is VMware vSphere, This was made available for vSphere at Version 6.5 and newer. 

That is well documented, explained and many how too's on. So I',\m not sure I understand your question(?)


There is also some pro's and cons to it. It is default for very large, resource intensive VM's, but... Using it turns off vNUMA when used. Other factors. So yes, is well documented in the VMware vSphere and ESXi docs.

#rramaiah#: I looked in to the ESXi docs. I could only find the user manual for hot addition of cpu cores. I couldnt get the actual implemenation document describing how to implement this feature. Also additionally is this information provided by intel or linux docs? Please provide the links incase if you find one. Thanks very much for your help.

---

### Post by MAFoElffen on 2021-10-09
[How to hot-add RAM and hot-plug vCPUs to your vSphere VMs in different environments]("https://www.vmwareblog.org/hot-add-ram-hot-plug-vcpus-vsphere-vms-different-environments/"), VMware Blog.
[Change the Number of Virtual CPUs]("https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-76FC7E9F-8037-4C8E-BEB9-91C266C1EA9A.html"), VMware Documentation
[Virtual CPU Configuration]("https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-3CDA4DEF-3DE0-4A64-89C7-F31BB77222CB.html"), VMware Documentation
[Enable CPU Hot Add]("https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-285BB774-CE69-4477-9011-598FEF1E9ACB.html"), VMware Documentation
[Virtual Memory Configuration]("https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-EC6B0727-A692-4CC3-8439-164E6D8BAC19.html"), VMware Documentation
[Virtual CPU Limitations]("https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-13AD347E-3B77-4A67-B3F4-4AC2230E4509.html"), VMware Documentation

etc, etc, etc. A well as more youtube vdeo's than you would ever watch.

Note that there are limitations... Just because the host can do that, doesn't mean the VM Guest can do it. For example, BSD does not recognize any changes in vcpu or memory changes. Debian branched OS'es (that includes Ubuntu) will recognize changes in hot adding vCPU's, but will not recognize hot adding memory, until it is rebooted. Windows, Linux RHEL and SUSE Branched OS'es recognize changes in both.

And outside of a Blade Server, with around 20 plus blades, or a Cloud Platformed Environment, who has the number of cores/threads to get close to allocating 128 to 768 vCPU's per VM?

And to really look at that, just how many people are going to use that outside of a Datacenter? Even then. Most server's sit idle, trudging on. Most people over-allocate their resources. If you analyze your management reports and see that you are less than 35-45%, then maybe you should give up 50% of the resources to use elsewhere.

Where it does come in handy is when a Dev is in a heavy compile, and the resources are pegged for what seems like forever. You are sitting there hoping it doesn't crash before it's done... And if it does, then you have to allocate more, and run it again. Resource intensive jobs like that.

---

### Post by rramaiah on 2021-10-18
Hi MafoElfeen,

Sorry I couldnt respond to you earlier. Thanks very much for the links.

The links explain how to configure and use the vCPU/memory. But Im looking for is "Implementation details about consuming the vCPU/Memory".

>> [COLOR=#000000]Debian branched OS'es (that includes Ubuntu) will recognize changes in hot adding vCPU's, but will not recognize hot adding memory, until it is rebooted. Windows, Linux RHEL and SUSE Branched OS'es recognize changes in both.

As you have mentioned ubuntu recognizes vCPU hot addition, how is this feature implemented? is there any intel or linux docs available explaining about the implementation details.

Thanks !![/COLOR]

---

### Post by MAFoElffen on 2021-10-18
I do not know. 

I (personally) care only of what I can or can not do. Sometimes (well, a heck of a lot more frequently) I will try on my own to see what those limits are and if I can push them beyond what it said is the limits and boundaries... But I have no control of those beyond that. I am testing KVM 6.x versions, but haven't really seen a change in that, that I noticed specifically.

Those internal behaviors and limitations are beyond the scope of what I can change as a User or Administrator of a system.

 *** 
My curiosity now is why are you asking for those kinds of details? If you are thinking of supporting those kinds of things, and/or enhancing them, then maybe you should be talking to someone at VMware to see what they do... But... (LOL)

I am a dev tester for vSphere and ESXI (as well as for KVM). VMware is proprietary, not opensource. They will not likely share those details, as that kind of thing is part of their competitive edge over others. As a Beta Tester for vSphere, I had to sign a NDS about things VMware, but even then, I know they do not share those kinds of things even with us. It's just here are new features to test and play with. Try to use or break them.

---

### Post by rramaiah on 2021-10-19
Thanks MAfoElfeen for the reply.

---

