---
title: "How to backup my virtual OS for Hardy?"
date: 2008-03-09
forum: Virtualisation
---

### Post by timzak on 2008-03-09
I plan on installing Hardy from scratch in May sometime.  I also plan to switch from 64bit to 32bit, so a fresh install is essential.  How do I migrate my Virtualbox Windows install?  Are there certain files/folders that I can just backup and restore into my new Hardy installation?

Thanks.

---

### Post by fifth on 2008-03-09
> **timzak said:**
> I plan on installing Hardy from scratch in May sometime.  I also plan to switch from 64bit to 32bit, so a fresh install is essential.  How do I migrate my Virtualbox Windows install?  Are there certain files/folders that I can just backup and restore into my new Hardy installation?

Thanks.

When i re-install, the only file I usually keep is the disk image. So just make sure you backup up the vdi file. The virtual machine can be easily re-created and then just use the existing disk image.

The easiest way to manage these kind of things is to use a seperate partition for /home. That way you wouldn't have to worry about backing up before an upgrade/change.

---

### Post by timzak on 2008-03-09
Thanks.  Yeah, I have a separate /home partition, but I guess I'm just not clear enough on the concept.  So I just reinstall without having to backup?  I knew you could do that but for some reason I thought that because I'm going from 64 bit to 32 bit that would change things.

---

### Post by fjgaude on 2008-03-09
I don't think so... I've gone from 32 to 64-bit without issue, even taken the vm of about 14GB, that's the whole vmx directory, to another computer and it worked, even though one computer was Intel and the other AMD. Wow! Crazy man, crazy!

---

### Post by himagain on 2008-08-15
> **fjgaude said:**
> I don't think so... I've gone from 32 to 64-bit without issue, even taken the vm of about 14GB, that's the whole vmx directory, to another computer and it worked, even though one computer was Intel and the other AMD. Wow! Crazy man, crazy!
Hi Frank,
Just got here late! :-)
I need to do this too.  
How did you actually do it? 
(REAL newby here so type slowly....)

Cheers!

---

