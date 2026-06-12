---
title: "Please bump ZFS to 2.2.1! - This is now fixed"
date: 2024-02-06
forum: Server Platforms
---

### Post by sfjuocekr-r on 2024-02-06
From:

[https://github.com/openzfs/zfs/releases/tag/zfs-2.2.1](https://github.com/openzfs/zfs/releases/tag/zfs-2.2.1)
[https://github.com/openzfs/zfs/issues/15526](https://github.com/openzfs/zfs/issues/15526)

There is a bug in ZFS 2.2.0 regarding block-cloning, I feel like this should be addressed.

---

### Post by ian-weisser on 2024-02-06
Bugs should be reported to the bug tracker (whom we are not).

---

### Post by CharlesA on 2024-02-07
In addition to the above, Debian has backports that include 2.2.2. I don't know if they work with Ubuntu, however.

Your best bet if you do not want to build it yourself (see below) is to open a bug report, as suggested. You can do that from here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

You can even login with your Ubuntu One username and password.

If you need to build ZFS from source, see the following doc:
[https://openzfs.github.io/openzfs-docs/Developer%20Resources/Custom%20Packages.html#debian-and-ubuntu](https://openzfs.github.io/openzfs-docs/Developer%20Resources/Custom%20Packages.html#debian-and-ubuntu)

---

### Post by MAFoElffen on 2024-02-07
**[SIZE=3][COLOR=#ff0000]SOLVED.[/COLOR][/SIZE]**

Thank you for your concern, but... We have already addressed this,  and it is taken care. We were busy at work on it for a while now. 1fallen and I tested the fixes for Ubuntu.

It was already taken care of in a Bug Report: [https://bugs.launchpad.net/ubuntu/mantic/+source/zfs-linux/+bug/2044657](https://bugs.launchpad.net/ubuntu/mantic/+source/zfs-linux/+bug/2044657)

The release is already in Dev Noble. The fixes/backports are already committed for For Mantic, Jammy & Focal. Those fixes should hit soon. 

Jammy & Focal will not see 2.2.1, but the update contains all the necessary backports of the fixes. 

EDIT: Be aware of another ZFS Bug Report... Do not snapshot bpool on pre-Noble until this is resolved:
[https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999](https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999)
They are working on it. 1fallen and I are pushing the for the fix. I have 3 recovery work-arounds worked out for it for those affected with that other issue. Right now, all 3 work-arounds come with disclaimers. But they work. We are ahead of OpenZFS with their reported Issue efforts, and will report it back upstream when we have our end worked out for us.

We are on it. LOL. I take pride in Ubuntu, the Members here, us Users. We take care of each other. (Sometimes behind the scenes with the Keebler Elves...)

If you understand that, and all that has answered your "question", then you are free to mark this thread as "Solved"...

To avoid confusion, you may want to edit the first post, by adding a line saying "EDIT: It was addressed", and referring to a link to this post, so that it doesn't scare other Users thinking this has not been addressed (Please).

---

### Post by #&amp;thj^% on 2024-02-07
> **MAFoElffen said:**
> **[SIZE=3][COLOR=#ff0000]SOLVED.[/COLOR][/SIZE]**

We are on it. LOL. I take pride in Ubuntu, the Members here, us Users. We take care of each other. (Sometimes behind the scenes with the Keebler Elves...)

If you understand that, and all that has answered your "question", then you are free to mark this thread as "Solved"...

**_To avoid confusion, you may want to edit the first post, by adding a line saying "EDIT: It was addressed", and referring to a link to this post, so that it doesn't scare other Users thinking this has not been addressed (Please)_**.

+1 and another Please add that to your thread title...
We need good information related to all....
Thanks

---

### Post by CharlesA on 2024-02-07
Great work on getting that patched. I've edited the title to note that this has been addressed, but not marked it as solved.

---

