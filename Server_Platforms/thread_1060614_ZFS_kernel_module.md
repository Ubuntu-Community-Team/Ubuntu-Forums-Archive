---
title: "ZFS kernel module"
date: 2009-02-04
forum: Server Platforms
---

### Post by Yashiro on 2009-02-04
This is probably a long shot but, have there been any developments on this front or is there any news that the situation may change within the next quarter?

---

### Post by gtdaqua on 2009-02-05
There is a way to port ZFS into linux but not without a performance sacrifice. I think its unlikely ZFS will make into linux without ANY change in ZFS. Of course, this has to be authorised by Sun first.

One more reason why it may not make, and also why you should not bother too, is that btrfs is already making its apperance the 2.6.29 kernel. Currently its not stable, but its open and specifically being developed to compete with ZFS. Let's hope btrfs makes it in time. Initial reports are showing a big gains in filesystem I/O.

---

### Post by Yashiro on 2009-02-05
I'd rather have stuck with Linux for my needs. I'm used to it and it's quirks. 
However, my experiments with ZFS have proven it's really good. 

Sadly it's looking like I'll have to transition my data to this. 
Which means I'll lose my Linux frivolities, be back on Solaris and be feeling like I've gone back to Uni.

---

### Post by ghettofreeryder on 2009-02-05
I do not know how to do it, but google search nexenta.  They have nexenta server going to beta soon, which is ubuntu with ZFS.  They also have nexenta core, and nexentaStor

---

### Post by Yashiro on 2009-02-05
Yeah a friend of mine is testing it at the moment. He tells me he's probably just going to bite the bullet and use Solaris.

---

### Post by gtdaqua on 2009-02-05
> **Yashiro said:**
> Yeah a friend of mine is testing it at the moment. He tells me he's probably just going to bite the bullet and use Solaris.

ZFS rules without a question for now. Btrfs is not mainstream and it will take a while to see this in Linux. As of now, looks like you don't have options.

---

