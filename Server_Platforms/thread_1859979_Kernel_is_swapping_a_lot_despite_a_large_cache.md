---
title: "Kernel is swapping a lot despite a large cache"
date: 2011-10-14
forum: Server Platforms
---

### Post by 2smooth on 2011-10-14
I'm facing performance problems lately. And i noticed that kernel is swapping a lot although half of the memory is being used as buffer cache. I would expect the system to reduce the size of the buffer in favor of other running processes. In this case mysql and apache.

```

Output Atop:


CPU | sys 3% | user 13% | irq 0% | idle 95% | wait 690% |
cpu | sys 1% | user 4% | irq 0% | idle 35% | cpu002 w 60% |
cpu | sys 0% | user 1% | irq 0% | idle 0% | cpu003 w 99% |
cpu | sys 0% | user 2% | irq 0% | idle 0% | cpu000 w 98% |
cpu | sys 1% | user 1% | irq 0% | idle 33% | cpu004 w 64% |
cpu | sys 0% | user 2% | irq 0% | idle 17% | cpu001 w 81% |
cpu | sys 0% | user 1% | irq 0% | idle 0% | cpu005 w 99% |
cpu | sys 0% | user 2% | irq 0% | idle 0% | cpu006 w 98% |
cpu | sys 0% | user 1% | irq 0% | idle 10% | cpu007 w 89% |
CPL | avg1 9.50 | avg5 8.55 | avg15 6.11 | csw 2424 | intr 2654 |
MEM | tot 7.8G | free 50.0M | cache 5.8G | buff 0.8M | slab 67.5M |
SWP | tot 7.4G | free 6.0G | | vmcom 12.8G | vmlim 11.4G |
PAG | scan 7968 | stall 0 | | swin 4679 | swout 562 |
DSK | sda | busy 96% | read 804 | write 14 | avio 4 ms |
DSK | sdb | busy 0% | read 3 | write 7 | avio 2 ms |
NET | transport | tcpi 122 | tcpo 91 | udpi 0 | udpo 0 |
NET | network | ipi 122 | ipo 94 | ipfrw 0 | deliv 122 |
NET | eth0 0% | pcki 122 | pcko 135 | si 33 Kbps | so 214 Kbps |

PID SYSCPU USRCPU VGROW RGROW RDDSK WRDSK ST EXC S CPU CMD 1/3
1864 0.00s 0.10s -1280K -748K 28K 0K -- - S 2% apache2
2628 0.06s 0.00s 416K 416K 32K 0K -- - R 1% atop
2548 0.01s 0.03s 0K 2208K 1672K 0K -- - S 1% apache2
1954 0.00s 0.03s 0K 0K 0K 0K -- - S 1% apache2
2545 0.01s 0.02s 768K 448K 0K 0K -- - S 1% apache2
1940 0.00s 0.03s 0K 2868K 2824K 0K -- - S 1% apache2
75 0.03s 0.00s 0K 0K 0K 0K -- - S 1% kswapd0
1853 0.00s 0.02s 0K 0K 0K 0K -- - S 0% apache2
2096 0.00s 0.02s 0K 0K 0K 0K -- - S 0% apache2
1851 0.00s 0.02s 0K 8K 32K 0K -- - S 0% apache2
2344 0.00s 0.02s 0K 4K 0K 0K -- - S 0% apache2
1870 0.00s 0.02s 0K 0K 0K 0K -- - S 0% apache2
1924 0.00s 0.02s 1024K 692K 0K 0K -- - S 0% apache2
1992 0.00s 0.02s 0K 0K 0K 0K -- - S 0% apache2
1963 0.00s 0.02s 0K 340K 572K 0K -- - S 0% apache2
1922 0.00s 0.02s 0K 0K 0K 0K -- - S 0% ap

```

How come the kernel is keeping on swapping while their is so much cache memorye available(cache 5.8G)?

MEM | tot 7.8G | free 50.0M | **cache 5.8G **| buff 0.8M | slab 67.5M |
SWP | tot 7.4G | free 6.0G | | vmcom 12.8G | vmlim 11.4G |
PAG | scan 7968 | stall 0 | | **swin 4679** | **swout 562** |

---

### Post by matt_symes on 2011-10-14
Hi

What is your swappiness set to ?

```
cat /proc/sys/vm/swappiness
```

Kind regards

---

### Post by 2smooth on 2011-10-14
60

But i've already played with this one.

I'd decrease this to 10, but to no avail? :-(

---

### Post by 2smooth on 2011-10-17
I've found the cause. :-)

Some file of the apache module mod-security had grown excessively. 

```

:lsof -p 26064

apache2 26064 www-data   15u   REG              252,4     536576      56 /var/log/modsecurity/data/resource.dir
apache2 26064 www-data   16u   REG              252,4 6238929920      57 /var/log/modsecurity/data/resource.pag

```

This is how the output of atop now looks like:

```

ATOP - www                2011/10/17  14:31:19                4 seconds elapsed
PRC | sys   0.13s | user   1.84s | #proc    230 | #zombie    1 | #exit      4 |
CPU | sys      3% | user     45% | irq       0% | idle    752% | wait      1% |
cpu | sys      1% | user      8% | irq       0% | idle     91% | cpu005 w  0% |
cpu | sys      1% | user     10% | irq       0% | idle     89% | cpu000 w  0% |
cpu | sys      0% | user      8% | irq       0% | idle     92% | cpu003 w  0% |
cpu | sys      0% | user      8% | irq       0% | idle     92% | cpu006 w  0% |
cpu | sys      0% | user      5% | irq       0% | idle     95% | cpu001 w  0% |
cpu | sys      0% | user      4% | irq       0% | idle     95% | cpu002 w  1% |
cpu | sys      0% | user      3% | irq       0% | idle     97% | cpu004 w  0% |
cpu | sys      0% | user      0% | irq       0% | idle    100% | cpu007 w  0% |
CPL | avg1   0.23 | avg5    0.20 | avg15   0.17 | csw     1704 | intr    1920 |
MEM | tot    7.8G | free    3.6G | cache   1.1G | buff  300.9M | slab   97.0M |
SWP | tot    7.4G | free    5.0G |              | vmcom   7.5G | vmlim  11.4G |
DSK |         sdb | busy      1% | read       4 | write     13 | avio    1 ms |
DSK |         sda | busy      0% | read       0 | write      6 | avio    0 ms |
NET | transport   | tcpi     340 | tcpo     248 | udpi       0 | udpo       0 |
NET | network     | ipi      366 | ipo      248 | ipfrw      0 | deliv    340 |
NET | eth0     0% | pcki     335 | pcko     348 | si   97 Kbps | so  643 Kbps |
NET | lo     ---- | pcki      32 | pcko      32 | si    5 Kbps | so    5 Kbps |

  PID  SYSCPU  USRCPU  VGROW  RGROW  RDDSK  WRDSK  ST EXC S  CPU CMD     1/2
 1605   0.00s   0.31s     0K     0K    16K    52K  --   - S   8% mysqld
29632   0.00s   0.21s   256K    96K     0K     0K  --   - S   5% apache2
29584   0.00s   0.16s     0K     0K     0K     0K  --   - S   4% apache2
29686   0.00s   0.15s    68K   348K     0K     0K  --   - S   4% apache2
29636   0.01s   0.11s  -448K  -364K     0K     0K  --   - S   3% apache2
29633   0.00s   0.12s     0K    40K     0K     4K  --   - S   3% apache2
29693   0.01s   0.10s  -256K  -236K     0K     4K  --   - S   3% apache2
29570   0.00s   0.10s   768K   768K     0K     0K  --   - S   2% apache2
29601   0.01s   0.06s     0K     0K     0K     0K  --   - S   2% apache2
29624   0.01s   0.06s     0K     0K     0K     0K  --   - S   2% apache2
29503   0.00s   0.06s     0K     0K     0K     0K  --   - S   1% apache2
29676   0.00s   0.06s   256K   256K     0K     0K  --   - S   1% apache2
29620   0.00s   0.06s     0K     0K     0K     8K  --   - S   1% apache2
29611   0.01s   0.05s     0K     0K     0K     0K  --   - S   1% apache2
29684   0.01s   0.05s  -448K  -380K     0K     0K  --   - S   1% apache2
29564   0.00s   0.05s  -768K  -768K     0K     0K  --   - S   1% apache2
29695   0.00s   0.04s     0K     0K     0K     0K  --   - S   1% apache2
29483   0.00s   0.03s     0K     4K     0K     0K  --   - S   1% apache2
29689   0.00s   0.03s     0K     0K     0K     0K  --   - S   1% apache2
29384   0.03s   0.00s     0K     0K     0K     0K  --   - R   1% atop
29535   0.02s   0.00s  -0.3G -19.1M     0K     0K  --   - Z   0% apache2
29648   0.00s   0.01s     0K     0K     0K     4K  --   - S   0% apache2
29690   0.00s   0.01s     0K     0K     0K     0K  --   - S   0% apache2



```

---

### Post by mtphr on 2012-07-10
Hi,
How did u exactly determine which process was eating it all up?
I'm having a similar situation, my vmcom exceeds vmlim and i can't find why. (ubuntu 12.04)

---

### Post by matt_symes on 2012-07-11
Hi

> **mtphr said:**
> Hi,
How did u exactly determine which process was eating it all up?
I'm having a similar situation, my vmcom exceeds vmlim and i can't find why. (ubuntu 12.04)

I think he used ```
lsof
```

Kind regards

---

