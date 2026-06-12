---
title: "[SUGGESTION] in-kernel ZFS module"
date: 2007-06-11
forum: The Cafe
---

### Post by emparq on 2007-06-11
One of the reasons that Ubuntu is my distro of choice is because Canonical does a pretty good job of balancing the legal and ethical problems of integrating non-free software in with its distro. This indicates to me that Canonical has a pragmatic decision-making policy, and that it aims to benefit its **end-users** the most, even if it has to stray somewhat from the FOSS philosophy to do it.

This being the case, I'd like to suggest an idea that I think would tremendously benefit the linux community, and that I feel Canonical has the greatest chance at making a reality: in-kernel ZFS.

Of course, one would ask that with the multitude of free and robust file-systems out there that Linux has to offer, why ZFS? First, let's go over some of the practical benefits. From my reading [[1]]("http://www.sun.com/software/solaris/faqs/zfs.xml")[[2]]("http://en.wikipedia.org/wiki/ZFS"), here's my understanding of some of the touted features about ZFS that make it attractive (in no particular order):

 - ZFS offers functionality of the LVM layer, effectively eliminating the need for it
 - ZFS has online on-the-fly data-corruption repair (ie. offline 'fsck'-ing wouldn't be required much, and potentially not at all)
 - time and space costs for snapshots are cheap (this is probably a driving force behind [Apple's OS X Leopard's 'time machine' feature]("http://www.apple.com/macosx/leopard/timemachine.html"))
 - ZFS offers RAID-Z (ie. RAID-5, but with transactional assurance that drive recovery is guaranteed to either entirely succeed or entirely fail)
 - dynamic-striping (ie. RAID-0) automatically takes advantage of new devices added to the zpool (a zpool is analogous what LVM considers a 'volume group')
 - ZFS offers transparent compression (ie. automatically compressing data where possible), saving disk costs

I'm sure that there are other features and innovations that ZFS brings to the table, but this list is just a few of the more notable ones. And while these features seemingly target IT admins in businesses (which btw, should already be a compelling enough reason to do it), end-users would also benefit greatly from this. Even if the only feature they ever really gained from is the fact that their data has more guards against corruption, end-users will find their linux experience to be more pleasant. This in itself is a huge win for the linux community, and could potentially help spread the word and win even more people over.

So ok, that all sounds pretty compelling, so what's keeping the linux community from reaping the benefits of ZFS? Implementation-wise, ZFS-on-FUSE is showing real promise [[3]]("http://zfs-on-fuse.blogspot.com/"), and the author of the project claims that it shouldn't be a problem to do at the kernel layer. So what then, is the real problem?

Well, for those of us that haven't followed this story, it basically boils down to this: Sun has licensed ZFS under the CDDL (Common Development and Distribution License), which is ok for OpenSolaris, ok for the BSD OS's, but not ok for linux. Most if not all of the linux kernel pretty much falls under GPLv2, which disallows incompatibly-licensed modules to be redistributed with it.

It **does not**, however, prohibit end-users from linking a GPLv2-incompatible module with the kernel (NVIDIA's and ATI's drivers are a good example of this). This means that ZFS could still be offered as a choice to linux users, as long as it were maintained outside of, and distributed seperately from, the mainline kernel. But who then, has the resources that could accomplish this, that would also be **willing** to do this for the linux community? Enter Canonical.

Canonical, as I mentioned earlier, has demonstrated that they are willing to make tough decisions in the interest of benefiting end-users, even if they have to stray outside of the FOSS philosophy to accomplish this (eg. proprietary NVIDIA/ATI drivers to enable 3D desktop effects). What's more, they've also demonstrated that they're willing to blaze new trails if they deem it a worthwhile endeavor (eg. re-inventing the boot initialization process with 'Upstart').

The question that remains then *'is this worth doing?'* I strongly believe so for the following reasons:

1 - technical benefits (see the list mentioned above)
2 - like it or not, ZFS has significant public mindshare and is seen as a 'killer feature' (especially now that Apple is plugging it), and that mindshare makes a difference to decision-makers (especially in businesses)
3 - while currently viewed as unlikely, there is the possibility that ZFS's and the linux kernel's licenses may one day find common ground in the GPLv3 (whose final version is to be released in either end of June or July 2007). Linus Torvalds, in fact just stated today (June 10, 2007) [[4]]("http://lkml.org/lkml/2007/6/10/148"):

> Btw, if Sun really _is_ going to release OpenSolaris under GPLv3, that 
_may_ be a good reason. I don't think the GPLv3 is as good a license as 
v2, but on the other hand, I'm pragmatic, and if we can avoid having two 
kernels with two different licenses and the friction that causes, I at 
least see the _reason_ for GPLv3. As it is, I don't really see a reason at 
all.

I personally doubt it will happen, but hey, I didn't really expect them to 
open-source Java either(*), so it's not like I'm infallible in my 
predictions.


So what do you all think? Whether you agree or disagree, I'm interested in hearing your thoughts on why. Also if you agree, please chime in on what we can do to further this goal. There's already a spec on Launchpad.net [[5]]("https://launchpad.net/ubuntu/+spec/zfs-filesystem"), is there anything else we can do? Thanks for taking the time to read this.


[1] [http://www.sun.com/software/solaris/faqs/zfs.xml]("http://www.sun.com/software/solaris/faqs/zfs.xml")
[2] [http://en.wikipedia.org/wiki/ZFS]("http://en.wikipedia.org/wiki/ZFS")
[3] [http://zfs-on-fuse.blogspot.com/]("http://zfs-on-fuse.blogspot.com/")
[4] [http://lkml.org/lkml/2007/6/10/148]("http://lkml.org/lkml/2007/6/10/148")
[5] [https://launchpad.net/ubuntu/+spec/zfs-filesystem]("https://launchpad.net/ubuntu/+spec/zfs-filesystem")

---

### Post by runningwithscissors on 2007-06-11
Whay all this praise for ZFS? As far as I know, volume management and software RAID support are standard on any Linux distro.

And the capacities that it claims to support aren't used by desktop machines at least at the present time. And servers hardly ever use software RAID.

---

### Post by prizrak on 2007-06-11
ZFS uses a much more transparent volume management and RAIDing. From the description it's quite a bit more efficinent than what we have right now. If it gets GPL'ed it'll get integrated into kernel by some distros, all other GPL compatible filesystems are.

---

### Post by KingArthur10 on 2007-06-13
My biggest reason for wanting ZFS would be the snapshotting (might help keep my disk usage to a minimum when I back up...I tend to have several versions of various files), on-the-fly data-corruption correction (I HATE it when I have to muck through w/o X11....I know, I'm not 7337 (or however that is)), and compression (I loved this about NTFS......usually it could save a couple hundred megs for my partitions which on a 40GB laptop HD is a loved feature).

---

### Post by pheaver on 2007-06-13
I desperately want to see zfs in Linux.  I tried out zfs-fuse and loved how easy it was to use.  Anyone who claims that LVM and Raid are perfectly fine... you need to try zfs.

Yes, due to the licensing issues, it seems much more likely that zfs would be a kernel module (like nvidia) instead of builtin.  That said, I don't really care if I can boot a zfs partition, so a kernel module is fine by me!

- Phil

---

### Post by tageiru on 2007-06-13
> **pheaver said:**
> Yes, due to the licensing issues, it seems much more likely that zfs would be a kernel module (like nvidia) instead of builtin.  That said, I don't really care if I can boot a zfs partition, so a kernel module is fine by me!
It doesn't matter if it is builtin or a module (which really are the same thing). The root filesystem is mounted through a initramfs which loads whatever module is necessary.

---

### Post by tehkain on 2007-06-13
Tell sun to license it to the gpl3. Then maybe it might happen if linux goes dual license or makes the switch. Sun purposely did not GPL it because linux is a competing product. People are saying sun is going to gpl3 OpenSolaris but I really doubt it that will happen or that if it does ZFS will be included. So I say we go with what linus suggested and try to push NetApp to release WAFL.

PS the FUSE approach is not an alternative.

---

### Post by BassKozz on 2007-06-24
> **tehkain said:**
> PS the FUSE approach is not an alternative.

Why not?

p.s. 1st post newb on-board, plz go easy on me :)

---

### Post by tehkain on 2007-06-24
> **B/-\ssKozz said:**
> Why not?

p.s. 1st post newb on-board, plz go easy on me :)

Because of stability and consistency. There are many negatives with using the fuse system. In no way would I trust important core data(which is the reason I would be using zfs) to NTFS using NTFS-3g. There is a decent chance of corruption with these modules due . There is also a speed and performance issue. Now You would be better off using one of the FS in the kernel. Hopefully we will get Netapp to give us their FS.

If windows migration was not so important I doubt NTFS3g would be used or worth the risk.

---

### Post by thisllub on 2007-06-24
Initially an Automatix style utility to recompile ZFS into the kernel might be the best option.
Otherwise those more interested in getting it could compile it in themselves. If you  know you want it you probably know how to compile it in anyway.

---

### Post by kripkenstein on 2007-06-24
> **emparq said:**
> It **does not**, however, prohibit end-users from linking a GPLv2-incompatible module with the kernel (NVIDIA's and ATI's drivers are a good example of this).

Many people - some Linux kernel devs, in particular! - would disagree with you on this one. NVidia binary drivers being legally linkable with the kernel is much-disputed.

It would be best to not get into this legal hassle. Sure, ZFS is wonderful, but it isn't crucial enough to be worth dividing the community over legal matters.

Let ZFS mature a bit. Meanwhile the legal problems may go away if it is licensed otherwise (and/or Linus changes his mind on the GPL3).

---

