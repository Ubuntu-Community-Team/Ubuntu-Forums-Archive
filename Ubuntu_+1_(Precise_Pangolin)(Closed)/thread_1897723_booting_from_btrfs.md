---
title: "booting from btrfs?"
date: 2011-12-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by scradock on 2011-12-19
In the course of testing Precise, I tried installing to a btrfs partition. It worked OK, everything runs, and the install is updated to date. 

BUT the install is not found by Grub2 from other installs - it doesn't appear in the grub.cfg, as if os-prober isn't finding it.

Any ideas what I need to do about this?

---

### Post by ranch hand on 2011-12-19
You need a /boot partition in ext4 for grub to see it.  If you do that it will work fine, or at least should.

Hopefully grub will get btrfs support soon.

---

### Post by scradock on 2011-12-20
> **ranch hand said:**
> You need a /boot partition in ext4 for grub to see it.  If you do that it will work fine, or at least should.

Hopefully grub will get btrfs support soon.

OK, that's what is going on. Well, I think I'll wait for grub to catch up...

---

### Post by teh603 on 2011-12-20
I wonder if this issue will ever get fixed. Butter FS has been out for a while now, and GRUB still doesn't support it.

---

### Post by BC59 on 2011-12-20
The main drawback is the lack of a fsck tool. I tried to use BTFRS last year, but with no fsck I had serious problems.

---

### Post by jbicha on 2011-12-20
Also, ext4 will be faster than btrfs. Maybe btrfs will be a better choice for 12.10 or so, but for now ext4 is great.

---

### Post by teh603 on 2011-12-21
> **jbicha said:**
> Also, ext4 will be faster than btrfs. Maybe btrfs will be a better choice for 12.10 or so, but for now ext4 is great.How do we know that ext4 is faster than btrfs? Most of us haven't been able to try it because of the lack of available tools, never mind that its been out a year now.

---

### Post by jbicha on 2011-12-21
ext4 is better than btrfs right now because:
1. ext4 is actually supported (kind of important to me in a file system)
2. You can actually boot from ext4
3. fsck
4. It is faster than btrfs
5. Everyone uses ext4 so it's better tested

#4 might not change because btrfs' features may slow it down slightly. Once #2 and #3 are fixed, #1 and #5 become a little less important so that btrfs would be fine for early adopters.

---

### Post by jbicha on 2011-12-21
Hmm, maybe booting from btrfs is possible now:

[https://lists.ubuntu.com/archives/precise-changes/2011-December/005494.html](https://lists.ubuntu.com/archives/precise-changes/2011-December/005494.html)

---

### Post by BC59 on 2011-12-21
This is true, because they were thinking to use BTFRS as default file system in Fedora 16.

---

### Post by teh603 on 2011-12-21
> **jbicha said:**
> Hmm, maybe booting from btrfs is possible now:

[https://lists.ubuntu.com/archives/precise-changes/2011-December/005494.html](https://lists.ubuntu.com/archives/precise-changes/2011-December/005494.html)Interesting. I'd wondered why I hadn't heard anything about booting off btrfs, and I guess nobody had checked or something.

---

### Post by scradock on 2011-12-22
> **teh603 said:**
> Interesting. I'd wondered why I hadn't heard anything about booting off btrfs, and I guess nobody had checked or something.

Yes, it is possible - I installed Precise to a btrfs partition and it set up GRUB just fine, and would boot OK. 

The problem is that I have a whole mess of different installs, and getting the btrfs install to boot from ANOTHER one was giving me a headache. That would have meant that the latest cutting-edge testing (Precise) with the iffy file system would have been the "GRUB master" that controlled access to everything, and I'm not comfortable with that. 

I try to keep the Grub master a few steps behind cutting edge so I know I can get into the machine.

---

### Post by ranch hand on 2011-12-23
Well, that is interesting.  May have to install something with btrfs.  See what all the hollering is about.

---

### Post by BC59 on 2011-12-23
BTRFS should be a lot faster than ext4. 
That's the whole idea. 
And when I used it I had that feeling. 
Or at least I thought it was...
Placebo effect is stronger than medicines.

---

