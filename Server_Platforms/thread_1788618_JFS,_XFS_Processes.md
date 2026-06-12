---
title: "JFS, XFS Processes"
date: 2011-06-22
forum: Server Platforms
---

### Post by Maurd. on 2011-06-22
Hi,

After an update recently I noticed that my process count jumped up quite a bit. Somehow it doesn't seem related (it was an apt update I believe), but I'll just throw it out there.

All of the extra processes seem to be related to XFS and JFS file system kernel processes, but none of my file systems use XFS nor JFS, just EXT3 & EXT4.

Is there any safe/easy way to kill off these processes and prevent them from re-spawning? I don't find having irrelevant idle processes to be beneficial nor efficient.

Thank you to anyone, I appreciate it. :)

It's using Ubuntu 10.04 64-bit. Only active file systems are EXT4 and EXT3.

```
24458	0.0 %	Jun17	[xfs_mru_cache]
24459	0.0 %	Jun17	[xfslogd/0]
24460	0.0 %	Jun17	[xfslogd/1]
24462	0.0 %	Jun17	[xfslogd/2]
24463	0.0 %	Jun17	[xfslogd/3]
24464	0.0 %	Jun17	[xfslogd/4]
24465	0.0 %	Jun17	[xfslogd/5]
24466	0.0 %	Jun17	[xfslogd/6]
24467	0.0 %	Jun17	[xfslogd/7]
24468	0.0 %	Jun17	[xfsdatad/0]
24469	0.0 %	Jun17	[xfsdatad/1]
24470	0.0 %	Jun17	[xfsdatad/2]
24471	0.0 %	Jun17	[xfsdatad/3]
24472	0.0 %	Jun17	[xfsdatad/4]
24473	0.0 %	Jun17	[xfsdatad/5]
24474	0.0 %	Jun17	[xfsdatad/6]
24475	0.0 %	Jun17	[xfsdatad/7]
24476	0.0 %	Jun17	[xfsconvertd/0]
24477	0.0 %	Jun17	[xfsconvertd/1]
24478	0.0 %	Jun17	[xfsconvertd/2]
24479	0.0 %	Jun17	[xfsconvertd/3]
24480	0.0 %	Jun17	[xfsconvertd/4]
24481	0.0 %	Jun17	[xfsconvertd/5]
24482	0.0 %	Jun17	[xfsconvertd/6]
24483	0.0 %	Jun17	[xfsconvertd/7]
24486	0.0 %	Jun17	[jfsIO]
24487	0.0 %	Jun17	[jfsCommit]
24488	0.0 %	Jun17	[jfsCommit]
24489	0.0 %	Jun17	[jfsCommit]
24490	0.0 %	Jun17	[jfsCommit]
24491	0.0 %	Jun17	[jfsCommit]
24492	0.0 %	Jun17	[jfsCommit]
24493	0.0 %	Jun17	[jfsCommit]
24494	0.0 %	Jun17	[jfsCommit]
24495	0.0 %	Jun17	[jfsSync]
```

---

### Post by Gyokuro on 2011-06-24
Which kernel release are you using? After a quick google search it seems you are not alone (have a look at: [https://answers.launchpad.net/ubuntu/+question/146528](https://answers.launchpad.net/ubuntu/+question/146528)) however on Ubuntu 10.04.02 and kernel 2.6.32-32 such a behaviour does not occur.

---

### Post by dtfinch on 2011-06-24
I have servers with 2.6.32-27, same as in the linked question, on 10.04 64-bit server, and none of them have those processes, nor does my desktop.

---

