---
title: "Shrink VBox VMDK"
date: 2010-11-20
forum: Virtualisation
---

### Post by afz12 on 2010-11-20
I am wondering how to shrink a Virtual Box vmdk machine in Ubuntu 10.10 as a host with XP as a guest. I have the latest VBox running and it saves vmdk format now (used to be vdi?) - I read this may be like VMware. However the Virtual Box VM has expanded to ~38 GB but the real size is only ~15 GB reported in XP. How can I shrink the VM down to its real size?

I am not familiar with Ubuntu terms etc so a step by step approach would be greatly appreciated.

---

### Post by CharlesA on 2010-11-20
Did you set the virtual hard drive to be a fixed size or dynamic?

I've not run into that problems, but I guess it could happen if you have a lot of snapshots.

Does that VM have any snapshots?

---

### Post by afz12 on 2010-11-20
Hi CharlesA

No, the VM has no snapshots. Also I set it up as 40GB dynamic. Under Ubuntu, the VMDK file reports 34.8 GB. However, when running, XP reports about 14 GB. I would like the two to agree as this error? causes the VM to use hard disk space for no obvious purpose.

I tried using nullfile-1.02.exe in XP and ran it overnight. It was slow and only converted ~5 GB to a file. I stopped it and deleted the file. Then I exported the VM to disk using VBox in Ubuntu 10.10. After some time it finished and the new file now reports  13.7 GB! I might try to import this new file using VBox and replace the original VM. I don't know it nullfile made a difference of course due to the length of the procedure.

Is there a better way to do this? I would have thought VBox could automatically track real VM size up and down as it goes. However VBox is really great in all other respects. This just seems like an oversight.

---

### Post by CharlesA on 2010-11-20
What does the Virtual Media Manager show for the size of the drive?

In the guest, the drive should show as the full size (40GB) the host should only see what space is being used.

---

### Post by afz12 on 2010-11-20
The virtual manager also reports ~35 GB as expected. XP as a guest reports the disk size as ~40 GB (windows never estimates exact size it seems) but only ~14 GB is used. VBox should therefore report the same usage. However, it seems to hang on the largest dynamic size used. After removing files from XP it seems to retain the largest space used rather than shrinking back to the actual space used. 

It seems to be this way as the exported file size agrees quite well with XP's estimate running as a guest. However Ubuntu still reports the original VMDK size as 34.7 GB and the exported version as ~14 GB. Therefore I tend to think that VBox tracks VMDK file size upwards in dynamic mode but maybe not downwards.

---

### Post by CharlesA on 2010-11-20
I've noticed that the size of the image once exported is smaller then the normal image, but I'm not sure what the cause of that is.

Perhaps check over on the virtualbox forums?

---

### Post by afz12 on 2010-11-20
Thanks for your comments CharlesA. I can't say I have a "fix" as yet but I saved the VM to an external hardrive. I tried to import through VBox but at the 11-th hour it moaned about insufficient disk space (even though it had plenty of space on the partition). I decided to bite the bullet and deleted the original VM. The copied VM then imported OK. It now reports its size as

VB Manager Virtual size = 40 GB Actual size = 24.9 GB
VM reported by Ubuntu looking at USB drive = 13.5 GB
XP as guest reports capacity = 39.9 GB, used = 15.7 GB unused =24.2 GB

Ubuntu Disk Analyser Total capacity = 69.2 GB, used = 32.6 GB available = 36.6 GB

So it seems I am back to where I started! VBox refuses to shrink its VM down to its real size. Anyway, if anyone has experienced this behavior first hand, I look forward to any comments.

---

