---
title: "Ubuntu 20.04 ocfs2 error"
date: 2022-01-25
forum: Server Platforms
---

### Post by sjurchen on 2022-01-25
System: Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-96-generic x86_64) as KVM Qemu Host

Hallo,

we recently got an error with our KVM host and ISCSI storage system (connected via multipath).
The ISCSI volume with an ocfs2 file system was set to read-only at runtime.

Syslog:
```

Jan 20 09:50:56 kvm02 kernel: [19949118.130758] OCFS2: ERROR (device dm-1): ocfs2_commit_truncate: Inode 8257798 has empty extent block at 8257798
Jan 20 09:50:56 kvm02 kernel: [19949118.130852] On-disk corruption discovered. Please run fsck.ocfs2 once the filesystem is unmounted.
Jan 20 09:50:56 kvm02 kernel: [19949118.130891] OCFS2: File system is now read-only.
Jan 20 09:50:56 kvm02 kernel: [19949118.133426] (rm,3474598,3):ocfs2_truncate_for_delete:627 ERROR: status = -30
Jan 20 09:50:56 kvm02 kernel: [19949118.133476] (rm,3474598,3):ocfs2_wipe_inode:794 ERROR: status = -30
Jan 20 09:50:56 kvm02 kernel: [19949118.133511] (rm,3474598,3):ocfs2_delete_inode:1084 ERROR: status = -30

```

We can't find any references to why this happend, no errors before it. (network was not interupted)

Does anybody has any idea?

---

### Post by MAFoElffen on 2022-01-26
> *OCFS2* is often used in high-availability systems. However, *OCFS2* usually converts the *filesystem* to *read*-*only* when encounters an error.
When it is normally r/w, if it gets a number of r/w errors, it transforms to read only mode to try to reduce continuing to degrade the data corruption. 

It's usually a filesystem or physical media problem.

The preferred, recommended fix was in your system log, right after the cause, which was pointed out as
```

On-disk corruption discovered. Please run fsck.ocfs2 once the filesystem is unmounted.

```

---

### Post by sjurchen on 2022-01-27
We have already performed the filesystem test and correction.
But we don't know how it happend and we would like to understand why that happend.

---

### Post by MAFoElffen on 2022-01-28
> **sjurchen said:**
> We have already performed the filesystem test and correction.
But we don't know how it happend and we would like to understand why that happened.

How and why? You want the summarized version of that right? Because I could write a book on that, and there would still be more to tell..

First... Just in the snippet you posted of the syslog, there are breadcrumbs present to follow. You just need to follow them back. That is not to say that you will find an answer there to the "how and why"... But it may narrow it down to a point in time, where, if there is not an indicator of "the problem," you might have a chance to see what was going on "when" it happened. That might not make sense intitially.

SAN Storage Pools have safeguard checks that try to protect from data corruption. One of those on yours was the filesystem crc checks. Your's worked. Now you know to set a threshold and use that threshold to send you a warning if something like that 'begins' to happen again...  

Some of those checks... Disk CRC checks. RAID CRC checks. RAM ECC, Filesystem CRC checks. SAN system advanced CRC checks. Biggest safe guard on disks is use Enterprize grade, instead of nearline. And rotatle them out when their warranty expires. 

iSCSi protocol has it's own CRC checks. It depends how you implement that, to how much that affects performance, The overhead for that is usually about 29%. Of that slice, writes use more resources than reads. Very large file writes up the risks. 

Have you thought about Redundant SAN Storage?

Most of the time when I see data corruption on iSCSI nodes, it is during a very very large file/data transfer. 

Sooner or later, things will happen. That's why we pan for disaster Recovery, do backups, set audits,set thresholds, alarms, do reporting, etc. That is just business.

---

### Post by sjurchen on 2022-01-28
We've traced the syslog 1 day back and can't find any clue.
Our storage system is redundant, we use two Huawei Dorado 3000 v6 and a redundant Network to each KVM Server (connected over iSCSI).
The storage nodes are direct connected to each other.

---

### Post by MAFoElffen on 2022-01-28
According to "Huawei", and their own Trouble Shooting Documentation (Oceanstore Dorado 6.0.0 Trouble Shooting, [https://support.huawei.com/enterprise/en/centralized-storage/oceanstor-dorado-3000-v6-pid-24030129?category=troubleshooting](https://support.huawei.com/enterprise/en/centralized-storage/oceanstor-dorado-3000-v6-pid-24030129?category=troubleshooting)), they consider what happened as a Critical Storage fault, which should have triggered alarms by their management software, that you should collect data to send to them, to help them to be able to determine the root of fault cause of that Critical Storage Fault on their device.

Have you done that? And what did they say might be the cause? And why did their own management system not trigger an alarm on it?

Not playing the Devil's Advocate, but they say they stand behind their products, and say that's their job with what you pay for...

It looks like your company did your due diligence on putting that system in place, for the safe guards they said they could provide. And they say they support storage pools for Virtual Hosting Systems. It appears that  you did everything right, within what you did, and that you should have support for this from them, right?.

---

### Post by sjurchen on 2022-02-02
The Storage is OK.
We have send them the log data, they can't find any problem.
And they can't give us help or support to find hints in the Ubuntu log.

---

### Post by MAFoElffen on 2022-02-04
Yes, they say they need something specific, in the way of information, which is not system logs from an OS, but specific information from their own device and it's own Management System.

Look back at Post #6... Look at the Linked PDF. Look at Appendix A, and chapter 5, on what information you should collect from the Device, before contacting Huawei to submit to their Engineers, for them to find out what went wrong and caused that critical fault. That is their instructions to their customers (you), is it not?If I were you, that is what I would be doing... Using the resources and service they say they provide. Right? That is what their support documentation says, does it not? Just saying what I read there...

I'm just reading what they say from their on troubleshooting documentation on their device, that you have.

---

### Post by sjurchen on 2022-02-04
We gave them the specific files from the Storage Nodes.
And they can't find any problem.

---

### Post by MAFoElffen on 2022-02-04
Then there you go... If their own engineers cannot tell you went on, what more can I hope to tell you.

You could post your syslogs to a pastebin.. But I don't see finding anymore than I said originally. It looked like it was having read errors, which after so many, flipped the read/write mode to read-only. What I saw from that snippet, did not include what else was going on at the same time, where a big system load from other processes might have contributed to that. But you are obsessing on what is already corrected. If you took a packup of the state before it was corrected, they might have had a better picture f what it did (or not).

What i also said was, the past is the past. What happened, happened. I had certain recommendations on what you should do now, to prepare and possibly prevent it from happening again.. To at least prepare that you may have to recover again (or not). But have a plan. Audit what is going on. Set alerts.

Their own Management system, says it can help with that... On auditing and alerts. Did their support have any recommendations?

---

