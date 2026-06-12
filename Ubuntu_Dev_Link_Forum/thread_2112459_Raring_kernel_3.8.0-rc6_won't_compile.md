---
title: "Raring kernel 3.8.0-rc6 won't compile"
date: 2013-02-04
forum: Ubuntu Dev Link Forum
---

### Post by zenon222 on 2013-02-04
I'm running Quantal and trying to compile the Raring kernel 3.8.0-rc6 from the git source:
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-raring.git
```
I'm not having success figuring out which module is broken.  
Here is my error output:
```
  CC      lib/reciprocal_div.o
  CC      lib/rwsem.o
  CC      lib/sha1.o
  CC      lib/show_mem.o
  CC      lib/string.o
  CC      lib/timerqueue.o
  CC      lib/vsprintf.o
  AR      lib/lib.a
  CC [M]  lib/test-kstrtox.o
  CC [M]  lib/crc-itu-t.o
  CC [M]  lib/crc7.o
  CC [M]  lib/libcrc32c.o
  CC [M]  lib/crc8.o
  CC [M]  lib/bch.o
  CC [M]  lib/ts_kmp.o
  CC [M]  lib/ts_bm.o
  CC [M]  lib/ts_fsm.o
  CC [M]  lib/notifier-error-inject.o
  CC [M]  lib/cpu-notifier-error-inject.o
  CC [M]  lib/pm-notifier-error-inject.o
  CC [M]  lib/memory-notifier-error-inject.o
  CC [M]  lib/lru_cache.o
  CC [M]  lib/cordic.o
  CC [M]  lib/rbtree_test.o
  CC [M]  lib/interval_tree_test_main.o
  CC [M]  lib/interval_tree.o
  LD [M]  lib/interval_tree_test.o
  CC [M]  lib/asn1_decoder.o
  GEN     lib/oid_registry_data.c
Compiling 49 OIDs
  CC [M]  lib/oid_registry.o
  CC      arch/x86/lib/msr-smp.o
  CC      arch/x86/lib/cache-smp.o
  CC      arch/x86/lib/msr.o
  AS      arch/x86/lib/msr-reg.o
  CC      arch/x86/lib/msr-reg-export.o
  AS      arch/x86/lib/iomap_copy_64.o
  LD      arch/x86/lib/built-in.o
  AS      arch/x86/lib/clear_page_64.o
  AS      arch/x86/lib/cmpxchg16b_emu.o
  AS      arch/x86/lib/copy_page_64.o
  AS      arch/x86/lib/copy_user_64.o
  AS      arch/x86/lib/copy_user_nocache_64.o
  AS      arch/x86/lib/csum-copy_64.o
  CC      arch/x86/lib/csum-partial_64.o
  CC      arch/x86/lib/csum-wrappers_64.o
  CC      arch/x86/lib/delay.o
  AS      arch/x86/lib/getuser.o
  GEN     arch/x86/lib/inat-tables.c
  CC      arch/x86/lib/inat.o
  CC      arch/x86/lib/insn.o
  AS      arch/x86/lib/memcpy_64.o
  AS      arch/x86/lib/memmove_64.o
  AS      arch/x86/lib/memset_64.o
  AS      arch/x86/lib/putuser.o
  AS      arch/x86/lib/rwlock.o
  AS      arch/x86/lib/rwsem.o
  AS      arch/x86/lib/thunk_64.o
  CC      arch/x86/lib/usercopy.o
  CC      arch/x86/lib/usercopy_64.o
  AR      arch/x86/lib/lib.a
  LINK    vmlinux
  LD      vmlinux.o
ubuntu/built-in.o: In function `dm_rh_dec':
(.text+0xd0a0): multiple definition of `dm_rh_dec'
drivers/built-in.o:(.text+0x303630): first defined here
ubuntu/built-in.o: In function `dm_rh_delay':
(.text+0xd440): multiple definition of `dm_rh_delay'
drivers/built-in.o:(.text+0x303250): first defined here
ubuntu/built-in.o: In function `dm_rh_recovery_in_flight':
(.text+0xd410): multiple definition of `dm_rh_recovery_in_flight'
drivers/built-in.o:(.text+0x302df0): first defined here
ubuntu/built-in.o: In function `dm_rh_update_states':
(.text+0xcc90): multiple definition of `dm_rh_update_states'
drivers/built-in.o:(.text+0x303750): first defined here
ubuntu/built-in.o: In function `dm_rh_start_recovery':
(.text+0xd590): multiple definition of `dm_rh_start_recovery'
drivers/built-in.o:(.text+0x302e20): first defined here
ubuntu/built-in.o: In function `dm_rh_mark_nosync':
(.text+0xcba0): multiple definition of `dm_rh_mark_nosync'
drivers/built-in.o:(.text+0x3032d0): first defined here
ubuntu/built-in.o: In function `dm_region_hash_destroy':
(.text+0xca20): multiple definition of `dm_region_hash_destroy'
drivers/built-in.o:(.text+0x302f30): first defined here
ubuntu/built-in.o: In function `dm_rh_region_to_sector':
(.text+0xc760): multiple definition of `dm_rh_region_to_sector'
drivers/built-in.o:(.text+0x302d00): first defined here
ubuntu/built-in.o: In function `dm_rh_dirty_log':
(.text+0xcb00): multiple definition of `dm_rh_dirty_log'
drivers/built-in.o:(.text+0x302d80): first defined here
ubuntu/built-in.o: In function `dm_rh_stop_recovery':
(.text+0xd540): multiple definition of `dm_rh_stop_recovery'
drivers/built-in.o:(.text+0x302ee0): first defined here
ubuntu/built-in.o: In function `dm_rh_bio_to_region':
(.text+0xc780): multiple definition of `dm_rh_bio_to_region'
drivers/built-in.o:(.text+0x302d20): first defined here
ubuntu/built-in.o: In function `dm_rh_recovery_prepare':
(.text+0xd1a0): multiple definition of `dm_rh_recovery_prepare'
drivers/built-in.o:(.text+0x303c80): first defined here
ubuntu/built-in.o: In function `dm_rh_recovery_start':
(.text+0xd2d0): multiple definition of `dm_rh_recovery_start'
drivers/built-in.o:(.text+0x303b10): first defined here
ubuntu/built-in.o: In function `dm_rh_flush':
(.text+0xd420): multiple definition of `dm_rh_flush'
drivers/built-in.o:(.text+0x302e00): first defined here
ubuntu/built-in.o: In function `dm_rh_region_context':
(.text+0xc7a0): multiple definition of `dm_rh_region_context'
drivers/built-in.o:(.text+0x302d40): first defined here
ubuntu/built-in.o: In function `dm_region_hash_create':
(.text+0xc7e0): multiple definition of `dm_region_hash_create'
drivers/built-in.o:(.text+0x3033e0): first defined here
ubuntu/built-in.o: In function `dm_rh_get_region_key':
(.text+0xc7c0): multiple definition of `dm_rh_get_region_key'
drivers/built-in.o:(.text+0x302d60): first defined here
ubuntu/built-in.o: In function `dm_rh_inc_pending':
(.text+0xd050): multiple definition of `dm_rh_inc_pending'
drivers/built-in.o:(.text+0x303b80): first defined here
ubuntu/built-in.o: In function `dm_rh_get_state':
(.text+0xcb10): multiple definition of `dm_rh_get_state'
drivers/built-in.o:(.text+0x303010): first defined here
ubuntu/built-in.o: In function `dm_rh_get_region_size':
(.text+0xc7d0): multiple definition of `dm_rh_get_region_size'
drivers/built-in.o:(.text+0x302d70): first defined here
ubuntu/built-in.o: In function `dm_rh_recovery_end':
(.text+0xd340): multiple definition of `dm_rh_recovery_end'
drivers/built-in.o:(.text+0x303a50): first defined here
make: *** [vmlinux] Error 1

```

---

