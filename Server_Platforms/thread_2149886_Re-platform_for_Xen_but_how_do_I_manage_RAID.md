---
title: "Re-platform for Xen but how do I manage RAID"
date: 2013-05-30
forum: Server Platforms
---

### Post by KillerKelvUK on 2013-05-30
Hi, I have a small home server running 12.04 as a single install and I've just configured my services on-top (still learning linux and best practice...).  I have 4x2TB (with lvms) disks in a RAID 10 configuration which serve via samba to my linux and windows clients primarily for media streaming but also as my primary file server and I use a small msata SSD for boot and config.

I've just started playing around with Xen to understand its benefits and I currently have in mind using VMWare Zimbra (open edition) as my mail, calendar, task solution...I've played around with this in a VirtualBox VM and the best practice I'm reading is that Zimbra should be installed either as an VM appliance or as a clean install on-top of a dedicated server OS.  This is therefore why I'm thinking of using Xen and having a separate DomU for Zimbra, another DomU for my file server and finally the Dom0 which I believe is best to leave just for the Xen management and config.

Would appreciate comments/peoples experience on the above also but my primary reason for posting was to understand how I should approach the RAID configuration to ensure the data is safe throughout this process.  I will of course backup separately, pending capex approval from my better half on some external storage ;), but was ideally looking to preserve it through to the conclusion of this process.


[TABLE="class: outer_border, width: 800"]
[TR]
[TD]**Dom**[/TD]
[TD]**OS**[/TD]
[TD]**OS Install**[/TD]
[TD]**File Storage**[/TD]
[/TR]
[TR]
[TD]0[/TD]
[TD]Ubuntu Server 12.04[/TD]
[TD]mSata SSD[/TD]
[TD]n/a[/TD]
[/TR]
[TR]
[TD]U[/TD]
[TD]Ubuntu Server 12.04 - File Server[/TD]
[TD]mSata SSD[/TD]
[TD]LV1 on RAID10[/TD]
[/TR]
[TR]
[TD]U[/TD]
[TD]Ubuntu Server 12.04 - VMWare Zimbra[/TD]
[TD]mSata SSD[/TD]
[TD]LV2 on RAID10[/TD]
[/TR]
[/TABLE]

So do I bring the RAID online within Dom0 and then assign an LV to a DomU e.g. for File Serving?  Are there any preparatory steps I need to take with the RAID other then deactivating it appropriately before OS changes?  I like reading around/researching things myself but am unsure of the language/phrases to use to define my challenge?

Thanks in advance.

K

---

