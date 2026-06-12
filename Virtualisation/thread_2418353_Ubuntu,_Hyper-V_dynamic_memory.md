---
title: "Ubuntu, Hyper-V dynamic memory"
date: 2019-05-05
forum: Virtualisation
---

### Post by xrstokes on 2019-05-05
Having trouble with Ubuntu server 18.04 and dynamic memory. I have some Debian 9 servers and ubuntu servers running on Hyper-V. The Debian servers perform as expected with dynamic memory and jump around between 512mb and 2gb of memory. My ubuntu servers seem to jump straight to the max memory available about 15seconds after a reboot. I believe it's all in cache but I'm not an expert in Linux. Flushing the cache it fills up again before the memory shrinks anyway. Can I get some pointers in chasing this down, A lot of work involved changing these newer servers back to Debian.

Thanks in advance. 

```
#free
              total        used        free      shared  buff/cache   available
Mem:        4026308     1558392     1478392       73488      989524     2331652
Swap:       2097148         780     2096368

```
```
#slabtop
  OBJS ACTIVE  USE OBJ SIZE  SLABS OBJ/SLAB CACHE SIZE NAME
116466 111417   0%    0.19K   2773       42     22184K dentry
 83820  83820 100%    0.13K   1397       60     11176K kernfs_node_cache
 66630  65980   0%    1.06K   2221       30     71072K ext4_inode_cache
 63616  63171   0%    0.50K    994       64     31808K kmalloc-512
 55808  54321   0%    0.06K    872       64      3488K pid
 48009  48009 100%    0.10K   1231       39      4924K buffer_head
 44733  44148   0%    0.20K   1147       39      9176K vm_area_struct
 35351  34589   0%    0.59K    667       53     21344K inode_cache
 31808  31211   0%    0.25K    497       64      7952K filp
 30314  29997   0%    0.09K    659       46      2636K anon_vma
 28928  28928 100%    0.03K    226      128       904K kmalloc-32
 25856  25420   0%    0.06K    404       64      1616K kmalloc-64
 18522  18522 100%    0.19K    441       42      3528K cred_jar
 16408  15088   0%    0.57K    293       56      9376K radix_tree_node
 14790  14790 100%    0.04K    145      102       580K ext4_extent_status
 13312  13312 100%    0.02K     52      256       208K kmalloc-16
 11264  11264 100%    0.01K     22      512        88K kmalloc-8
 10608   9571   0%    0.66K    221       48      7072K proc_inode_cache
 10416   9761   0%    0.09K    248       42       992K kmalloc-96
  9920   9483   0%    0.25K    155       64      2480K kmalloc-256
  7084   7040   0%    0.69K    154       46      4928K sock_inode_cache
  6970   6970 100%    0.02K     41      170       164K lsm_file_cache
  5460   5460 100%    0.19K    130       42      1040K kmalloc-192
  4704   4449   0%    1.00K    147       32      4704K kmalloc-1024
  4335   4335 100%    0.05K     51       85       204K ftrace_event_field
  3818   3493   0%    0.70K     83       46      2656K shmem_inode_cache
  3264   3090   0%    0.12K     51       64       408K kmalloc-128
  3264   3264 100%    0.12K     51       64       408K eventpoll_epi
  3128   3128 100%    0.69K     68       46      2176K files_cache
  2912   2912 100%    0.07K     52       56       208K eventpoll_pwq
  2368   2311   0%    2.00K    148       16      4736K kmalloc-2048
  2336   2336 100%    1.00K     73       32      2336K signal_cache
  1920   1920 100%    0.06K     30       64       120K kmem_cache_node
  1848   1848 100%    0.38K     44       42       704K kmem_cache
  1472   1472 100%    0.09K     32       46       128K trace_event_file
  1410   1410 100%    2.06K     94       15      3008K sighand_cache
  1218   1218 100%    0.38K     29       42       464K mnt_cache
  1215   1215 100%    2.06K     81       15      2592K mm_struct
  1115   1006   0%    5.81K    223        5      7136K task_struct
  1088   1088 100%    0.94K     32       34      1024K RAW
  1064   1064 100%    0.14K     19       56       152K ext4_groupinfo_4k
   730    730 100%    0.05K     10       73        40K nsproxy
   592    576   0%    8.00K    148        4      4736K kmalloc-8192
   588    588 100%    1.12K     21       28       672K RAWv6
   560    560 100%    0.20K     14       40       112K file_lock_cache
   512    512 100%    0.03K      4      128        16K fscrypt_info
   496    458   0%    4.00K     62        8      1984K kmalloc-4096
   408    408 100%    0.31K      8       51       128K nf_conntrack

```

---

