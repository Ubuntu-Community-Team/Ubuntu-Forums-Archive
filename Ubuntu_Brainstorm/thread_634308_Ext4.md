---
title: "Ext4"
date: 2007-12-07
forum: Ubuntu Brainstorm
---

### Post by atlfalcons866 on 2007-12-07
ext4 should be in hardy. the fedora devs are including it in fedora 9.
[http://fedoraproject.org/wiki/Features/Ext4](http://fedoraproject.org/wiki/Features/Ext4)

new features like extents delayed allocation

---

### Post by 23meg on 2007-12-07
[http://ubuntuforums.org/showthread.php?t=621814](http://ubuntuforums.org/showthread.php?t=621814)

---

### Post by smartboyathome on 2007-12-07
Also, this type of thing is not very good for a long term release. I would expect this to be an 8.10 feature at the earliest.

---

### Post by Archmage on 2008-05-07
May I suggest now to put at least the option to use it (with large warnings, that this is still beta/alpha and you are not responcible for any data lost) in Intrepid?

---

### Post by gnomeuser on 2008-05-08
I have 2 machines both running F9 on ext4, they've been like that since installing onto ext4 became possible. The partitions are also employing dmcrypt. Currently there are no proper userspace tools, but in terms of stability I have yet to see ext4 eat data or cause issues. That being said it feels no different than an ext3 system, and currently the lack of tools to interact with it makes it very unappealing to general users. No way to fsck the partition e.g. is kind of a deal breaker for serious deployment.

---

### Post by quickshade on 2008-05-08
While I agree that it's not ready for general consumption it should be an option for testers.

---

### Post by disturbedite on 2008-05-08
> **atlfalcons866 said:**
> ext4 should be in hardy. the fedora devs are including it in fedora 9.
[http://fedoraproject.org/wiki/Features/Ext4](http://fedoraproject.org/wiki/Features/Ext4)

new features like extents delayed allocation
the linux kernel has supported the use of ext4 for a long time.  you could theoretically use it in any linux distro.

---

### Post by insane_alien on 2008-05-09
...if the kernel is compiled to support it. ubuntu's kernel is not. you'd have to roll your own kernel to get ext4 support. and remember it is still in development nobody but yourself will be responsible for data loss.

---

### Post by quickshade on 2008-05-09
also Grub can't boot a ext4 partition. This is something being work on for GSoC.

---

### Post by disturbedite on 2008-05-09
> **insane_alien said:**
> ...if the kernel is compiled to support it. ubuntu's kernel is not. you'd have to roll your own kernel to get ext4 support. and remember it is still in development nobody but yourself will be responsible for data loss.
i'm not 100% sure about that.  i read an article that stated that ext4 support is there (kernel module? i forget) but is marked experimental still.  the way it stated that seemed as if it was implying that one didn't have to explicitly enable it, but i could be wrong.

---

### Post by articpenguin on 2008-05-09
yup ext4 isnt compiled in ubuntu hardys kernel

> sudo modjohn@john-desktop:~$ sudo modprobe ext4dev
[sudo] password for john:
FATAL: Module ext4dev not found.
john@john-desktop:~$ sudo modprobe ext4
FATAL: Module ext4 not found.
john@john-desktop:~$



---

### Post by disturbedite on 2008-05-09
> **articpenguin said:**
> yup ext4 isnt compiled in ubuntu hardys kernel
well, i stand corrected.

---

### Post by Joeb454 on 2008-05-09
> **disturbedite said:**
> well, i stand corrected.

I'm willing to bet that you're actually sitting down ;)

---

### Post by disturbedite on 2008-05-10
> **Joeb454 said:**
> I'm willing to bet that you're actually sitting down ;)
how did you know that??! :lolflag:

---

### Post by ghindo on 2008-05-11
> **quickshade said:**
> also Grub can't boot a ext4 partition. This is something being work on for GSoC.Incompatibility with GRUB seems to me like a major issue.  

Ext4 doesn't seem especially appealing considering it's still in development.

What about ZFS?

---

### Post by smartboyathome on 2008-05-11
> **ghindo said:**
> What about ZFS?

It can't be used by Linux because there isn't any code for it in the kernel due to licensing restrictions.

---

### Post by insane_alien on 2008-05-11
> **smartboyathome said:**
> It can't be used by Linux because there isn't any code for it in the kernel due to licensing restrictions.

i never understood that one, both bits(kernel +zfs) are open source, why can't they be used together? seems a bit silly to me. then again, i'm an engineer rather than a lawyer.

---

### Post by smartboyathome on 2008-05-11
The license isn't compatible with the GPL, from what I understand. This hinders trying to give support to the Linux kernel.

---

### Post by ghindo on 2008-05-11
From Wikipedia:> Porting ZFS to Linux is complicated by the fact that the GNU General Public License, which governs the Linux kernel, prohibits linking with code under certain licenses, such as CDDL, the license ZFS is released underDarn.  From the sounds of it, though, it sounds like people are working towards making ZFS compatible with Linux.

---

### Post by disturbedite on 2008-05-12
> **quickshade said:**
> also Grub can't boot a ext4 partition. This is something being work on for GSoC.
if grub can't, then i doubt lilo could, right?  also, what about grub2, can it?

---

### Post by Archmage on 2008-05-20
Sorry, but are you sure about this? Since Fendora does have ext4, there should be a way, shouldn't it?

---

### Post by gnomeuser on 2008-05-20
> **Archmage said:**
> Sorry, but are you sure about this? Since Fendora does have ext4, there should be a way, shouldn't it?

In the Fedora community we are dedicated to bringing you the lastest technology. That is why ext4 is included as a technology preview but installation onto ext4 is disabled by default. You have to invoke a magic parameter to the installer to turn it on to keep people out of harms way.

There are no tools to run a file system consistency check or any other fs maintance jobs and grub does not yet support the filesystem (though openSUSE have a GSoC student adding this support so soon this should be on par). Before it can reach most users these things will have to be in place, but I am happy that Fedora have people dedicated to bring us previews and making it easy to work with while the featureset matures.

I write this on my laptop which is running F9 on an encrypted ext4 partition. My desktop also runs on ext4 without any issues and has done so for a long time. I have nothing but praises for it, it works great but you still have to know what you are doing.

---

### Post by -kg- on 2008-12-03
So I would assume that at least the /boot partition would have to be ext2/3 in order for GRUB to access it.  Other than that, ext4 would be usable for the rest of the system.

I was reading up on the new ext4 fs and it sounds like it has several potentially very useful new features, extends among them.  I am particularly interested in the implementation of Persistent de-allocation and delayed allocation to minimize fragmentation, as well as the on-line defragmentation.

I've had much experience with fragmentation and it's problems on DOS and Windows systems, and I understand that under Linux, while the ext(X) fs minimizes this, fragmentation is still an eventuality as the install ages.

I haven't read any "approximations" on how long this might take under Linux (I have rather large, relatively unused partitions for both my installations), but I can understand the eventuality of fragmentation (especially considering dynamic file and directory creation and appending) and the need to address it at such time it becomes an issue.

---

### Post by smartboyathome on 2008-12-03
> **-kg- said:**
> So I would assume that at least the /boot partition would have to be ext2/3 in order for GRUB to access it.  Other than that, ext4 would be usable for the rest of the system.

I was reading up on the new ext4 fs and it sounds like it has several potentially very useful new features, extends among them.  I am particularly interested in the implementation of Persistent de-allocation and delayed allocation to minimize fragmentation, as well as the on-line defragmentation.

I've had much experience with fragmentation and it's problems on DOS and Windows systems, and I understand that under Linux, while the ext(X) fs minimizes this, fragmentation is still an eventuality as the install ages.

I haven't read any "approximations" on how long this might take under Linux (I have rather large, relatively unused partitions for both my installations), but I can understand the eventuality of fragmentation (especially considering dynamic file and directory creation and appending) and the need to address it at such time it becomes an issue.

Either Grub legacy be on an ext2/3 partition, Grub legacy be patched to work with ext4, or we go with Grub2 (which works with ext4).

---

