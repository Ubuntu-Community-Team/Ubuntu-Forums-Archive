---
title: "Virt-sparsify first use... questions"
date: 2019-09-19
forum: Virtualisation
---

### Post by orthoducks on 2019-09-19
I'm not running a virtualized system, but I'm trying to use virt-sparsify and this seems to be the only place it's discussed. If there's a better place to post, please point.

I'm trying to sparsify an image of my system disk. I'm running Ubuntu 18.04 from a live DVD with the system disk on sda. I used dd to create an image of the disk on sdb1 (a 1TB ext4 partition, otherewise empty, mounted on /mnt.)

The first time I ran v-s it warned me that I had very little temporary file space... not surprising since it only had RAM. I set TMPDIR=/mnt and tried again. V-s displayed this:

    ```
    [   0.7] Create overlay file in /tmp to protect source disk
    [   0.7] Examine source disk
    virt-sparsify: error: libguestfs-error: /usr/bin/supermin exited with error status 1.
```

It said that to get more information I'd have to export a couple of environment variables and run the program again, then go to a web site to help me understand what I got.

So I exported the variables and ran the program again, and got exactly the same thing. No more information, just instructions to export the variables. What's the next step?

(It's reasonable to wonder whether the variables really got exported. I entered `env | grep <var...>`, and it displayed them, so apparently they did.)

*A couple of other questions while I'm here:*

When I get this working I'll want to run dd and v-s concurrently, with v-s consuming data as dd produces it. Is there an elegant way to do that? V-s doesn't have an option to read stdin, so I don't see how I can simply pipe it. I'm planning to create a named pipe and then write to it with dd in one terminal, then read the named pipe with v-s in another terminal, but that seems pretty awkward.

Second: What will happen when I restore a sparsified image? Will I get an exact copy of my original device? Or will the restored partitions be only as large as the partitions in the sparsified image? If the latter, what becomes of the unused part of the target device? Is it simply unallocated space that I can utilizeby re-inflating the partitions with GParted?

---

