---
title: "controlling the folder's disk quota with setgid"
date: 2008-08-14
forum: Server Platforms
---

### Post by gustavolinux on 2008-08-14
Folks, I need to limit the size of a folder shared in the network, no matters who have access and  write to it... in other words, think about a folder that every user have to access and possibly write, but the size of this folder has to be under a size limit...

In my concern, there is no configuration mecanism especially made to this task, right? I think that the proper feature should come from the filesystem...

But, anyway, I thought about a solution using group quotas. I guess that when you enable the  folder's setgid bit, everything that is copied to that folder becames owned by the folder's group owner. If I create a group of users, let's say named "Control", and put every network user in this group (but as a secondary group - "Control" won't be the main group of no user), do you think that the "Control"s group disk quota (properly configured) will limit the size of the folder (without limiting no user's quota)...

Is there a chance that this idea work? Is there a better choice?

Thanxs in advance....

---

### Post by kidders on 2008-08-15
Hi there & welcome,

I think your idea should work well. The only issue I can see is that circumventing the quota would be trivial, but it would at least provide your users with a *suggested* disk usage limit.

You could impose a stricter cap by mounting a small filesystem into the shared folder. That way, not even root would be able to exceed your maximum directory size. For example ...```
dd if=/dev/zero of=shared.img bs=1M count=10
mkfs.ext2 shared.img
mkdir test
sudo mount -o loop shared.img test
```

The down-side of that approach is that changing the quota would be awkward.

What do you think?

---

### Post by gustavolinux on 2008-08-18
thank you kidders

I think it's a good idea, thanks for it, and for the commands..

could you explain how the quota can be subverted please?

[]'s

---

### Post by kidders on 2008-08-18
Sorry... A little more detail would have been helpful!

Any user with "control" in his supplementary groups list could chgrp a file to his initial group (assuming, of course, he owned the file). For example, imagine you have a 10M group quota ...

```
# Dump 9 megabytes of garbage into the shared directory
dd if=/dev/urandom of=/mnt/shared/big_file bs=1M count=9

# Remove the "control" group ownership from the file
chgrp `whoami` /mnt/shared/big_file

# Create another big file
cp /mnt/shared/big_file /mnt/shared/another_big_file
```Your shared directory would now have 18M in it.

Any time you want to cap the amount of space available for a particular purpose, it's often best to confine the files in their own filesystem. That way, remote users can't accidentally break your Linux by filling its root filesystem up with junk. You also get the opportunity to use a different filesystem type. For example, Ext2 is fast, but too unreliable to store your whole OS on. The other extreme might be encrypted XFS on RAID, which would be secure & reliable, but way too slow for system-wide use.

Incidentally, if you do decide to put your shared directory in a filesystem by itself, remember to add it to /etc/fstab. I forgot to mention that in my last post.

I hope that helps.

---

### Post by gustavolinux on 2008-08-19
just to give a feedback: a loop device was a really good idea... to every folder that I want to limit its size I create an image of a file system with the right size... []'s

---

### Post by Keymaster on 2008-10-09
> **kidders said:**
> 

The down-side of that approach is that changing the quota would be awkward.

What do you think?

That helped me out a lot, but by saying "it would be awkward" I'm curious as to the method.  Is it simply copying the files into a replacement container, and then deleting the old one?

---

### Post by gustavolinux on 2008-10-09
I think this is enough... it is not that hard, but also isn't just a matter of "set size=newsize"...


[]'s

---

### Post by Keymaster on 2008-10-09
Well I have no idea how to do it, but I'm not too worried.  I think a 20GB folder Samba shared as Public is enough ;)

---

### Post by lifsuchy on 2009-10-28
I have actually run into the problem of needing to resize a image device I mounted in this method.   Can anyone give me some ideas of how to begin to attempt this.
 
It is currently a 300GB ext3 share.img that I need to double in size.

---

