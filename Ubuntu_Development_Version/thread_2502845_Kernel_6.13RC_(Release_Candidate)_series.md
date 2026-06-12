---
title: "Kernel 6.13RC (Release Candidate) series"
date: 2024-12-02
forum: Ubuntu Development Version
---

### Post by Doug S on 2024-12-02
After the release of kernel 6.13-rc1, just starting this thread. The [Ubuntu mainline PPA]("https://kernel.ubuntu.com/mainline/?C=N;O=D") compiles seem to be broken again. There are a few more compile warnings:

```

drivers/net/phy/intel-xway.o: warning: objtool: xway_gphy_led_polarity_set+0x126: stack state mismatch: cfa1=4+8 cfa2=5+16
drivers/net/phy/mxl-gpy.o: warning: objtool: gpy_led_polarity_set+0x126: stack state mismatch: cfa1=4+8 cfa2=5+16
drivers/net/phy/aquantia/aquantia_leds.o: warning: objtool: aqr_phy_led_polarity_set+0x2c: [COLOR="#FF0000"]can't find jump dest instruction[/COLOR] at .text+0x3d5
fs/bcachefs/btree_cache.o: warning: objtool: __bch2_btree_node_get() falls through to next function bch2_btree_node_get()
fs/bcachefs/btree_cache.o: warning: objtool: bch2_btree_node_get() falls through to next function bch2_btree_node_get_noiter()
fs/bcachefs/btree_key_cache.o: warning: objtool: bch2_btree_path_traverse_cached() falls through to next function bch2_btree_insert_key_cached()
fs/bcachefs/btree_update.o: warning: objtool: bch2_trans_update_get_key_cache() falls through to next function flush_new_cached_update()
fs/bcachefs/btree_update.o: warning: objtool: flush_new_cached_update() falls through to next function bch2_trans_update_by_path()

```
I am not understanding why these new compile warnings aren't noted and fixed quickly. A few (it's down to 10) of this type:

```
drivers/net/wireguard/allowedips.c: In function &#8216;root_free_rcu&#8217;:
drivers/net/wireguard/allowedips.c:67:1: warning: the frame size of 1048 bytes is larger than 1024 bytes [-Wframe-larger-than=]
   67 | }
      | ^
```have been there forever.

```
doug@s19:~/kernel/linux$ uname -a
Linux s19 6.13.0-rc1-stock #1290 SMP PREEMPT_DYNAMIC Sun Dec  1 16:50:06 PST 2024 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2024-12-07
Kernel 6.13-RC1 showed up on the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/mainline/v6.13-rc1/") a few days later.
There are a lot of kernel configuration changes (694), mainly additional modules to include, increasing the image size by 6 million bytes:

```

-rw-r--r-- 1 doug doug 149982716 Dec  7 14:36 ../linux-image-6.13.0-rc1-test2_6.13.0-rc1-00337-g7503345ac5f5-1292_amd64.deb
-rw-r--r-- 1 doug doug 143938730 Dec  7 12:14 ../linux-image-6.13.0-rc1-test_6.13.0-rc1-00337-g7503345ac5f5-1291_amd64.deb
                         6043986

```

EDIT: Hmmm... I can look at the Ubuntu mainline compile log for those same warnings I have been seeing:
```

drivers/net/phy/aquantia/aquantia_leds.o: warning: objtool: aqr_phy_led_polarity_set+0x121: [COLOR="#FF0000"]stack state mismatch[/COLOR]: cfa1=4+8 cfa2=5+16
drivers/net/phy/intel-xway.o: warning: objtool: xway_gphy_led_polarity_set+0x11a: stack state mismatch: cfa1=4+8 cfa2=5+16
drivers/net/phy/mxl-gpy.o: warning: objtool: gpy_led_polarity_set+0x11a: stack state mismatch: cfa1=4+8 cfa2=5+16
fs/bcachefs/btree_cache.o: warning: objtool: __bch2_btree_node_get() falls through to next function bch2_btree_node_get()
fs/bcachefs/btree_cache.o: warning: objtool: bch2_btree_node_get() falls through to next function bch2_btree_node_get_noiter()
fs/bcachefs/btree_key_cache.o: warning: objtool: btree_path_traverse_cached_fast() falls through to next function btree_key_cache_fill()
fs/bcachefs/btree_update.o: warning: objtool: bch2_trans_update_get_key_cache() falls through to next function flush_new_cached_update()
fs/bcachefs/btree_update.o: warning: objtool: flush_new_cached_update() falls through to next function bch2_trans_update_by_path()

```O.K. so that's weird, I get can't [COLOR="#FF0000"]find jump dest instruction [/COLOR] there.
But the point is, the warnings are present.

EDIT 2: At least some of the warnings (I didn't check them all) have been flagged by the "kernel test robot". [Example]("https://lore.kernel.org/oe-kbuild-all/202410181554.dT1KnkLl-lkp@intel.com/").

---

### Post by pqwoerituytrueiwoq on 2024-12-28
a rc3 folder appeared in mainline... and there is nothing there
tried to boot rc1 and it was paniced when trying to mount root (nvme ssd) same with 6.12.3

guess i need to learn how to compile the kernel my self...

ugh... things i want to do, things i have time to do, and things i need to do...

---

### Post by Doug S on 2024-12-30
> **pqwoerituytrueiwoq said:**
> guess i need to learn how to compile the kernel my self...

I have left "how to" instructions for the "git" method over on "ask", [here]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662"). Even though those notes started for 15.10, as far as I know, the instructions are up to date, with my last edit dated Nov 11th.
Let me know if you have difficulties and I'll try to help. If you don't use "git", I can't help.

Yes, the mainline PPA has been messed up for quite some time now.

Kernel 6.13-rc5 is availble, and the compile warnings I have been complaining about are gone. I think, but am not sure, it was because of an upgrade to the compiler version for my 24.04.1 server:

```
doug@s19:~/kernel/linux$ scripts/diffconfig .config-6.13-rc4 .config-6.13-rc5
-GCC_ASM_GOTO_OUTPUT_BROKEN y
 CC_VERSION_TEXT "gcc (Ubuntu 13.2.0-23ubuntu4) 13.2.0" -> "gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0"
 GCC_VERSION 130200 -> 130300
+CC_HAS_ASM_GOTO_OUTPUT y
+CC_HAS_ASM_GOTO_TIED_OUTPUT y
+CC_HAS_NAMED_AS_FIXED_SANITIZERS y
```

EDIT: Actually, I just edited the reference in the link I gave, because I now suppress most of the compile time spew of output because I found that real warnings and errors were being lost in the massive piles of output.

---

### Post by pqwoerituytrueiwoq on 2024-12-30
so 
```
git checkout -b k44rc8_stock v4.4-rc8
```

would be this correct?

```
git checkout -b k613rc5_stock v6.13-rc5
```

---

### Post by Doug S on 2024-12-30
> **pqwoerituytrueiwoq said:**
> so 
```
git checkout -b k44rc8_stock v4.4-rc8
```

would be this correct?

```
git checkout -b k613rc5_stock v6.13-rc5
```Yes.

You can confirm things are correct via looking at the commits. Example:

```
doug@s19:~/kernel/linux$ git branch
  check-bad
  k610-rc1
  k610-rc2
  k610-rc2v2
  k610-rc2v3
  k610-rc2v33
  k611
  k611-iowait
  k612
  k612rc3
* master

doug@s19:~/kernel/linux$ git log --oneline | head -5
fc033cf25e61 Linux 6.13-rc5
4099a71718b0 Merge tag 'sched-urgent-2024-12-29' of git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip
6cbc4b29eb0d Merge tag 'x86-urgent-2024-12-29' of git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip
f65832a32f2e Merge tag 'perf-urgent-2024-12-29' of git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip
bcfac5530a78 Merge tag 'objtool-urgent-2024-12-29' of git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip

doug@s19:~/kernel/linux$ git checkout -b k613rc5_stock v6.13-rc5
Switched to a new branch 'k613rc5_stock'

doug@s19:~/kernel/linux$ git log --oneline | head -5
fc033cf25e61 Linux 6.13-rc5
4099a71718b0 Merge tag 'sched-urgent-2024-12-29' of git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip
6cbc4b29eb0d Merge tag 'x86-urgent-2024-12-29' of git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip
f65832a32f2e Merge tag 'perf-urgent-2024-12-29' of git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip
bcfac5530a78 Merge tag 'objtool-urgent-2024-12-29' of git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip

doug@s19:~/kernel/linux$ git branch
  check-bad
  k610-rc1
  k610-rc2
  k610-rc2v2
  k610-rc2v3
  k610-rc2v33
  k611
  k611-iowait
  k612
  k612rc3
* k613rc5_stock
  master


```

EDIT: If you are not going to make any change at all to the kernel source code, then there is no need to make your own branch. You could just compile from the master branch.

---

### Post by pqwoerituytrueiwoq on 2024-12-31
well i compiled it and booted it and both features/changes i wanted to try do not seem to work


* [https://www.phoronix.com/news/Linux-6.12-rc4-MSI-Claw-A1M](https://www.phoronix.com/news/Linux-6.12-rc4-MSI-Claw-A1M) (I have a 2C controller and 4 buttons are not detected...)
* [https://www.phoronix.com/news/Linux-6.13-AMDGPU-Zero-Fan](https://www.phoronix.com/news/Linux-6.13-AMDGPU-Zero-Fan) (was hoping this was a thing for the 5000 series, this should be enabled for cards older than this BTW, i hacked a vbios to disable 0 rpm mode on my RX 580)

---

### Post by Doug S on 2024-12-31
> **pqwoerituytrueiwoq said:**
> well i compiled it and booted it and both features/changes i wanted to try do not seem to work


* [https://www.phoronix.com/news/Linux-6.12-rc4-MSI-Claw-A1M](https://www.phoronix.com/news/Linux-6.12-rc4-MSI-Claw-A1M) (I have a 2C controller and 4 buttons are not detected...)
* [https://www.phoronix.com/news/Linux-6.13-AMDGPU-Zero-Fan](https://www.phoronix.com/news/Linux-6.13-AMDGPU-Zero-Fan) (was hoping this was a thing for the 5000 series, this should be enabled for cards older than this BTW, i hacked a vbios to disable 0 rpm mode on my RX 580)

Thanks for reporting back.
Well, at least you no longer depend on the Ubuntu mainline PPA, which has been unreliable.

I do not know how to help with your issues except to mention to check the kernel configuration that whatever code you need is included or made into a module. And if a module, to make sure it is loaded.

---

### Post by pqwoerituytrueiwoq on 2024-12-31
regarding thread count, does compiling benefit from SMT? or am i better off only using 'real' cores (it took a hour using 5 threads on my R5 3600)

---

### Post by Doug S on 2025-01-01
> **pqwoerituytrueiwoq said:**
> regarding thread count, does compiling benefit from SMT? or am i better off only using 'real' cores (it took a hour using 5 threads on my R5 3600)I think so, but am not certain.

My test server is:
Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
6 cores, 2 Threads per core, 12 CPUs.

A clean compile, using 13 threads, takes about 32 minutes, with my processor going flat out at ~110 watts and 4.8GHz the whole time. My processor does NOT throttle as a function of active cores, which is not the default for this processor.

---

