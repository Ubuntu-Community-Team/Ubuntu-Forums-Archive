---
title: "Kernel 6.12 RC (Release Candidate) series"
date: 2024-10-16
forum: Ubuntu Development Version
---

### Post by Doug S on 2024-10-16
The kernel 6.12 cycle started a few weeks ago, and is already up to 6.12-rc3.
I do not know what is going on with [the Ubuntu Mainline PPA]("https://kernel.ubuntu.com/mainline/?C=N;O=D"), which seems to have stopped doing anything since about mid September.

```
doug@s19:~$ uname -a
Linux s19 6.12.0-rc3-stock #1278 SMP PREEMPT_DYNAMIC Wed Oct 16 07:46:47 PDT 2024 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mezaway on 2024-10-20
I've not seen any updates for 6.12 rc series either. Been wondering what's up with that, and if it has anything to do with the change in kernel availability in future Ubuntu releases..

---

### Post by corradoventu on 2024-10-21
The builders are being moved to a different data center. Mainline builds will show up again once they're up and running. 

[https://lists.ubuntu.com/archives/kernel-team/2024-October/154532.html](https://lists.ubuntu.com/archives/kernel-team/2024-October/154532.html)

---

### Post by 1fallen on 2024-10-21
My last mail inculcated this:
> Expect kernel 6.12 to stay in various release candidate versions through  October and November, with a likely full release around the first of  December.
If you want to compile it: [https://www.kernel.org/](https://www.kernel.org/)

---

### Post by Doug S on 2024-10-22
> **corradoventu said:**
> The builders are being moved to a different data center. Mainline builds will show up again once they're up and running. 

[https://lists.ubuntu.com/archives/kernel-team/2024-October/154532.html](https://lists.ubuntu.com/archives/kernel-team/2024-October/154532.html)Agh. Thank you.

---

### Post by Doug S on 2024-10-22
> **1fallen2 said:**
> My last mail inculcated this:

If you want to compile it: [https://www.kernel.org/](https://www.kernel.org/)I have "how to" notes [here]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662"). Since Ubuntu mainline PPAs are not currently available, I would just steal the kernel configuration from the most recent Ubuntu mainline PPA ([6.11]("https://kernel.ubuntu.com/mainline/v6.11/")) and use it.

---

### Post by 1fallen on 2024-10-22
> **Doug S said:**
> I have "how to" notes [here]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662"). Since Ubuntu mainline PPAs are not currently available, I would just steal the kernel configuration from the most recent Ubuntu mainline PPA ([6.11]("https://kernel.ubuntu.com/mainline/v6.11/")) and use it.

Thanks Doug  S I Stole that recipe a long time ago, but it is one I still use to this day, :)

I'm on ZFS so I'll just wait for it to come in, if I break this system it will the last Ubuntu install this machine will ever see.

I'm still waiting for Canonical to find their way back to sanity.....LOL
I like it so far on Arch though>>>[FONT=monospace][COLOR=#000000]uname -r [/COLOR]
6.12.0-rc4-1-gcc
[/FONT]

---

### Post by Doug S on 2024-10-28
Kernel 6.12-rc5 is available.
```
doug@s19:~$ uname -a
Linux s19 6.12.0-rc5-stock #1279 SMP PREEMPT_DYNAMIC Sun Oct 27 18:16:45 PDT 2024 x86_64 x86_64 x86_64 GNU/Linux
```

I was running kernel 6.12-rc3 when I compiled it, and it took almost twice as long as normal to compile, with some unusual warnings:
```

doug@s19:~/kernel/linux$ [COLOR="#FF0000"]time make -s -j13 olddefconfig bindeb-pkg LOCALVERSION=-stock[/COLOR]
...
fs/bcachefs/btree_cache.o: warning: objtool: __bch2_btree_node_get() falls through to next function bch2_btree_node_get()
fs/bcachefs/btree_cache.o: warning: objtool: bch2_btree_node_get() falls through to next function bch2_btree_node_get_noiter()
fs/bcachefs/btree_key_cache.o: warning: objtool: bch2_btree_path_traverse_cached() falls through to next function bch2_btree_insert_key_cached()
fs/bcachefs/btree_update.o: warning: objtool: bch2_trans_update_get_key_cache() falls through to next function flush_new_cached_update()
fs/bcachefs/btree_update.o: warning: objtool: flush_new_cached_update() falls through to next function bch2_trans_update_by_path()
...
[COLOR="#FF0000"]real    60m21.634s[/COLOR]
user    656m57.230s
sys     56m34.672s
```

EDIT: I did a clean compile using 6.12-rc5, and the time was normal:

```
[COLOR="#FF0000"]real    32m16.444s[/COLOR]
user    351m55.224s
sys     29m31.062s
```

---

### Post by 1fallen on 2024-10-28
Doug S sorry but I'm curious of your findings with "bcachefs", I use it on one install so far.

Also has anyone really heard about what they are doing with the RT patch?
[https://documentation.ubuntu.com/real-time/en/latest/](https://documentation.ubuntu.com/real-time/en/latest/)

---

### Post by Doug S on 2024-10-28
> **1fallen2 said:**
> Doug S sorry but I'm curious of your findings with "bcachefs", I use it on one install so far.


I might be mistaken, but I do not recall seeing those compile warnings in previous 6.12 RC compiles. I did miss 6.12-RC4.

Anyway, I looked at the tags for the most recent commits for all of the files involved, from which I suspect "fs/bcachefs/btree_update.c" because it only has the 6.12-RC5 tag on the latest commit:

```

doug@s19:~/kernel/linux$ [COLOR="#FF0000"]git log --oneline fs/bcachefs/btree_update.c[/COLOR]
a0d11feefb19 bcachefs: Don't use commit_do() unnecessarily
32ed4a620c54 bcachefs: Btree path tracepoints
.
.
.
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]git tag --contains a0d11feefb19[/COLOR]
[COLOR="#FF0000"]v6.12-rc5[/COLOR]

```
I wasn't planning on doing any more with this, unless you want me to. I was planning on just waiting until the next RC to see if it gets fixed. This is not a kernel area I know at all.

---

### Post by 1fallen on 2024-10-29
> **Doug S said:**
> 
I wasn't planning on doing any more with this, unless you want me to. I was planning on just waiting until the next RC to see if it gets fixed. This is not a kernel area I know at all.

No Sir I'm good, and Thanks for the offer Doug S
All is good for a Desktop as a Normal user, but my back-up strategy fails as a production system.

Might be a mix of ZFS, and BTRFS, I'm still looking for the failures though.

---

### Post by Doug S on 2024-10-29
It turns out that the one 6.12-RC5 commit I found earlier was part of [a bigger set of commits]("https://lore.kernel.org/all/dctt3tf65qsvwyr5exvee7bkmwh6aejqcd4t7uwfzvjiowqtzk@fncmtmgdbg5b/T/").
[This article]("https://www.phoronix.com/news/Bcachefs-Fixes-Two-Choices") is also worth a look.

---

### Post by 1fallen on 2024-10-29
> **Doug S said:**
> 
[This article]("https://www.phoronix.com/news/Bcachefs-Fixes-Two-Choices") is also worth a look.

He sure gets a beating, and just dose not quite understand, there are video's out there that show the arguments back and forth.
I won't link them here though, it's very non-productive. If he dose not get it together soon  that project will vanish.
Nice Link Doug  S

---

### Post by Doug S on 2024-11-01
The bcachefs patch set for 6.12-RC6 has been merged, however those compile warnings are still present:

```

doug@s19:~/kernel/linux$ [COLOR="#FF0000"]git log --oneline[/COLOR]
17fa6a5f93fc (HEAD -> master, origin/master, origin/HEAD) Merge tag 'vfs-6.12-rc6.iomap' of gitolite.kernel.org:pub/scm/linux/kernel/git/vfs/vfs
d56239a82e37 Merge tag 'vfs-6.12-rc6.fixes' of gitolite.kernel.org:pub/scm/linux/kernel/git/vfs/vfs
6b4926494ed8 Merge tag 'for-6.12-rc5-tag' of git://git.kernel.org/pub/scm/linux/kernel/git/kdave/linux
[COLOR="#FF0000"]7b83601da470 Merge tag 'bcachefs-2024-10-31' of git://evilpiepirate.org/bcachefs[/COLOR]
6c52d4da1c74 Merge tag 'for-linus' of git://git.kernel.org/pub/scm/linux/kernel/git/rdma/rdma
5635f189425e Merge tag 'bpf-fixes' of git://git.kernel.org/pub/scm/linux/kernel/git/bpf/bpf
```

and:

```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]time make -s -j13 olddefconfig bindeb-pkg LOCALVERSION=-test[/COLOR]
...
fs/bcachefs/btree_cache.o: warning: objtool: __bch2_btree_node_get() falls through to next function bch2_btree_node_get()
fs/bcachefs/btree_cache.o: warning: objtool: bch2_btree_node_get() falls through to next function bch2_btree_node_get_noiter()
fs/bcachefs/btree_key_cache.o: warning: objtool: bch2_btree_path_traverse_cached() falls through to next function bch2_btree_insert_key_cached()
fs/bcachefs/btree_update.o: warning: objtool: bch2_trans_update_get_key_cache() falls through to next function flush_new_cached_update()
fs/bcachefs/btree_update.o: warning: objtool: flush_new_cached_update() falls through to next function bch2_trans_update_by_path()
...
```

---

### Post by 1fallen on 2024-11-01
I'm not sure how he got my email.....Grrrr not cool...

Doug S have you seen this yet: [https://lkml.org/lkml/2024/10/22/1352](https://lkml.org/lkml/2024/10/22/1352)

---

### Post by Doug S on 2024-11-02
> **1fallen2 said:**
> 
Doug S have you seen this yet: [https://lkml.org/lkml/2024/10/22/1352](https://lkml.org/lkml/2024/10/22/1352)Yes, that was the patch set that introduced the compile warnings in 6.12-RC5, and that I referenced in an earlier post. I was expecting that if there were any patches for 6.12-rc6, that the compile warnings would be fixed. So far, they haven't been.

---

### Post by 1fallen on 2024-11-02
> **Doug S said:**
> So far, they haven't been.

It's going to be a long hard road for Mr Overstreet, I'm glad your hanging in there with bcahefs.

I will admit it's getting a wee bit better, but still a long road in front of him....
Thanks Doug S and you really don't expect me to read all posts in a thread do you? :lolflag: 
Peace
```
 Host: cachyos-bcachefs Kernel: 6.12.0-rc5-2-cachyos-rc arch: x86_64 bits: 64
  ID-1: / size: 434.48 GiB used: 10.05 GiB (2.3%) fs: bcachefs dev: /dev/sda3
  ID-2: /boot size: 1.9 GiB used: 950.9 MiB (48.9%) fs: ext4 dev: /dev/sda2
  ID-3: /boot/efi size: 511 MiB used: 1.3 MiB (0.3%) fs: vfat dev: /dev/sda1
```

---

### Post by Doug S on 2024-11-04
Kernel 6.12-rc6 has been released:

```
doug@s19:~/kernel/linux$ uname -a
Linux s19 6.12.0-rc6-stock #1287 SMP PREEMPT_DYNAMIC Sun Nov  3 22:14:03 PST 2024 x86_64 x86_64 x86_64 GNU/Linux
```

As mentioned in an earlier post, I am still getting those compile warnings. If I look into it, for example this one:
```
fs/bcachefs/btree_cache.o: warning: objtool: __bch2_btree_node_get() falls through to next function bch2_btree_node_get()
```
It doesn't appear to me as though the code has a fall through path at all:

```

static struct btree *__bch2_btree_node_get(struct btree_trans *trans, struct btree_path *path,
                                           const struct bkey_i *k, unsigned level,
                                           enum six_lock_type lock_type,
                                           unsigned long trace_ip)
{
        struct bch_fs *c = trans->c;
        struct btree_cache *bc = &c->btree_cache;
        struct btree *b;
        bool need_relock = false;
        int ret;

        EBUG_ON(level >= BTREE_MAX_DEPTH);
retry:
        b = btree_cache_find(bc, k);
.
.
.
        if (unlikely(btree_node_read_error(b))) {
                six_unlock_type(&b->c.lock, lock_type);
                return ERR_PTR(-BCH_ERR_btree_node_read_error);
        }

        EBUG_ON(b->c.btree_id != path->btree_id);
        EBUG_ON(BTREE_NODE_LEVEL(b->data) != level);
        btree_check_header(c, b);

        [COLOR="#FF0000"]return b;[/COLOR]
}

```So, I'm not sure what is going on. (I should just ignore it, but am my own worst enemy.)

---

### Post by corradoventu on 2024-11-10
[https://kernel.ubuntu.com/mainline/](https://kernel.ubuntu.com/mainline/) is up again with v6.12-rc1 ..  v6.12-rc3

---

### Post by Doug S on 2024-11-11
> **corradoventu said:**
> [https://kernel.ubuntu.com/mainline/](https://kernel.ubuntu.com/mainline/) is up again with v6.12-rc1 ..  v6.12-rc3Interesting, but the builds are all failing.

Anyway 6.12-RC7 is out, but [the Ubuntu mainline PPA]("https://kernel.ubuntu.com/mainline/v6.12-rc7/") build failed.
```
doug@s19:~$ uname -a
Linux s19 6.12.0-rc7-stock #1288 SMP PREEMPT_DYNAMIC Sun Nov 10 17:09:23 PST 2024 x86_64 x86_64 x86_64 GNU/Linux
```

I still get the compile warnings I mentioned that last couple of weeks.

EDIT: I compiled the kernel using a 24.10 desktop VM, just to see if a newer version of the kernel would still have those warning messages. It did.

---

### Post by Doug S on 2024-11-28
Kernel 6.12 has been released. It was many days ago, but I got behind. The [Ubuntu mainline PPA ]("https://kernel.ubuntu.com/mainline/v6.12/")build worked, Yippie. So, this is the first time in a long time that I have been able to steal the Ubuntu kernel configuration. There are 71 kernel configuration differences between what I have been using, which was last sync'd with Ubuntu as of 6.11-RC6, and the Ubuntu one.

The compile warnings are still present:
```
fs/bcachefs/btree_cache.o: warning: objtool: __bch2_btree_node_get() falls through to next function bch2_btree_node_get()
fs/bcachefs/btree_cache.o: warning: objtool: bch2_btree_node_get() falls through to next function bch2_btree_node_get_noiter()
fs/bcachefs/btree_key_cache.o: warning: objtool: bch2_btree_path_traverse_cached() falls through to next function bch2_btree_insert_key_cached()
fs/bcachefs/btree_update.o: warning: objtool: bch2_trans_update_get_key_cache() falls through to next function flush_new_cached_update()
fs/bcachefs/btree_update.o: warning: objtool: flush_new_cached_update() falls through to next function bch2_trans_update_by_path()
```

---

