---
title: "intel_pstate mainline testing"
date: 2014-07-13
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2014-07-13
Thread Objective:
[LIST]
[*]Determine if intel_pstate is acting correctly (correctly needs to be defined) 
[*]Determine if intel_pstate should be used by default on supported CPUs (sandy bridge and later) 
[/LIST]

Previous thread - [http://ubuntuforums.org/showthread.php?t=2151440](http://ubuntuforums.org/showthread.php?t=2151440)
Script to generate a frequencies chart: [http://pastebin.com/PYj4wwCj](http://pastebin.com/PYj4wwCj) requires [php5-cli]("apt:php5-cli") be installed
Script to generate a system report - [http://pastebin.com/Z7fsU5TC](http://pastebin.com/Z7fsU5TC)
I have attached my results to this post, chart was made using
```
script -d .1 -t 600
```
[FONT=courier new]-d .1[/FONT] makes it poll the cpu 10 times a second
[FONT=courier new]-t 600[/FONT] makes it check it 600 times
600 * 0.1 seconds = 60 seconds
i ran mprime (prime95 for linux) to see how the system responded to high core loads for 1,2,3, and 4 core in use

Please also mention if your CPU temps have gone up/down compared to ondemand with both the performance and powersave governors, if you have a battery mention if it last longer or shorter
To change from  performance to powersave run this command
```
echo powersave | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```
to revert to performance run this
```
echo performance | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

I noticed in performance mode all of my cores stayed in there turbo frequency range the entire time and never once went to 3.5Ghz, thought cooling is not a issue as i have Noctua NH-D14 cooling it in a room with air conditioning,
Is turbo even designed to run all cores above the base clock speed all at the same time, even when running prime my clock speeds stay at 3.7Ghz, i have a max turbo of 3.9 and a base clock of 3.5 Ghz

---

### Post by Doug S on 2014-07-22
pqw...,

I suggest that we might want to wait before doing a bunch of testing on the intel_pstate driver.
The driver has already been enabled by default. See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1333322"). While the bug report mentions "it has improved in stability over the past several kernel releases", that actually isn't true. There was a significant regression in or around kernel 3.14, and while it has now been fixed there is some energy that could possibly be saved and a lot of work is going into finding a solution that both saves the energy but doesn't cost much, if any, performance.

You might have observed a few changes in kernel 3.16 RC5. There will also be several changes in kernel 3.17 RC1 (I think 11 patches). It hasn't been decided yet when any significant algorithm change will be introduced.

By the way, thanks for your off forums help with some tests using your new haswell processor.

---

### Post by startas on 2014-07-24
And what will happen if i will try it to use on first gen core i processors (arrandale) ?

---

### Post by pqwoerituytrueiwoq on 2014-07-24
i believe it is only enabled on 2ed gen sandy bridge through 5th gen haswell
@Doug S no problem, just let me know if you want to run any test on my Pentium B970 (2.3Ghz Sandy bridge dual core)

---

### Post by Doug S on 2014-08-01
> **pqwoerituytrueiwoq said:**
> I noticed in performance mode all of my cores stayed in there turbo frequency range the entire time and never once went to 3.5Ghz, thought cooling is not a issue as i have Noctua NH-D14 cooling it in a room with air conditioning,
Is turbo even designed to run all cores above the base clock speed all at the same time, even when running prime my clock speeds stay at 3.7Ghz, i have a max turbo of 3.9 and a base clock of 3.5 GhzI finally remembered how you can check this for your processor. Use turbostat with the -v option. Example:```
doug@s15:~/temp$ [COLOR=#ff0000]sudo ./turbostat -v[/COLOR]
turbostat v3.7 Feb 6, 2014 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
CPUID(6): APERF, DTS, PTM, EPB
RAPL: 690 sec. Joule Counter Range, at 95 Watts
cpu0: MSR_NHM_PLATFORM_INFO: 0x100070012200
16 * 100 = 1600 MHz max efficiency
34 * 100 = 3400 MHz TSC frequency
cpu0: MSR_IA32_POWER_CTL: 0x0004005d (C1E auto-promotion: DISabled)
cpu0: MSR_NHM_SNB_PKG_CST_CFG_CTL: 0x1e008403 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=3: pc6)
[COLOR=#ff0000]cpu0: MSR_NHM_TURBO_RATIO_LIMIT: 0x23242526
35 * 100 = 3500 MHz max turbo 4 active cores
36 * 100 = 3600 MHz max turbo 3 active cores
37 * 100 = 3700 MHz max turbo 2 active cores
38 * 100 = 3800 MHz max turbo 1 active cores[/COLOR]
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a1003 (0.125000 Watts, 0.000015 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x01e002f8 (95 W TDP, RAPL 60 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x800087f8001487f8 (locked)
...
```

---

### Post by pqwoerituytrueiwoq on 2014-08-04
```
~$ sudo Desktop/turbostat -v
turbostat v3.7 Feb 6, 2014 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:3c:3 (6:60:3)
CPUID(6): APERF, DTS, PTM
RAPL: 2979 sec. Joule Counter Range, at 88 Watts
cpu0: MSR_NHM_PLATFORM_INFO: 0x80838f3012300
8 * 100 = 800 MHz max efficiency
35 * 100 = 3500 MHz TSC frequency
cpu0: MSR_IA32_POWER_CTL: 0x0000005d (C1E auto-promotion: DISabled)
cpu0: MSR_NHM_SNB_PKG_CST_CFG_CTL: 0x1e000400 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, UNlocked: pkg-cstate-limit=0: pc0)
[COLOR=#ff0000]cpu0: MSR_NHM_TURBO_RATIO_LIMIT: 0x25262727
37 * 100 = 3700 MHz max turbo 4 active cores
38 * 100 = 3800 MHz max turbo 3 active cores
39 * 100 = 3900 MHz max turbo 2 active cores
39 * 100 = 3900 MHz max turbo 1 active cores[/COLOR]
cpu0: MSR_RAPL_POWER_UNIT: 0x000a0e03 (0.125000 Watts, 0.000061 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x000002c0 (88 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x421f4000149f40 (UNlocked)
cpu0: PKG Limit #1: ENabled (1000.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (1000.000000 Watts, 0.002441* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00641400 (100 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x88410800 (35 C)
cpu0: MSR_IA32_THERM_STATUS: 0x88450800 (31 C +/- 1)
cpu1: MSR_IA32_THERM_STATUS: 0x88470800 (29 C +/- 1)
cpu2: MSR_IA32_THERM_STATUS: 0x88440800 (32 C +/- 1)
cpu3: MSR_IA32_THERM_STATUS: 0x88430800 (33 C +/- 1)
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      78    2.01    3868    3499       0    2.41    0.86    0.37   94.35      32      34    0.00    0.00    0.00    0.00    5.92    1.11    0.00
       0       0     122    3.13    3880    3499       0    1.10    0.71    0.19   94.87      31      34    0.00    0.00    0.00    0.00    5.92    1.11    0.00
       1       1      75    1.94    3867    3499       0    1.43    0.89    0.50   95.23      29
       2       2      54    1.41    3851    3499       0    2.13    1.30    0.25   94.92      32
       3       3      60    1.56    3859    3499       0    4.98    0.55    0.52   92.38      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      61    1.57    3859    3499       0    4.54    0.79    0.24   92.86      32      35    0.00    0.00    0.00    0.00    5.79    0.89    0.00
       0       0      52    1.35    3857    3499       0    8.04    0.97    0.18   89.46      30      35    0.00    0.00    0.00    0.00    5.79    0.89    0.00
       1       1      59    1.52    3860    3499       0    6.85    0.77    0.33   90.54      29
       2       2      57    1.47    3853    3499       0    2.52    0.91    0.37   94.73      32
       3       3      76    1.96    3864    3499       0    0.75    0.53    0.07   96.70      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      59    1.52    3866    3499       0    4.04    1.01    0.26   93.17      32      35    0.00    0.00    0.00    0.00    5.77    0.86    0.00
       0       0      52    1.34    3865    3499       0    4.82    1.87    0.33   91.64      30      35    0.00    0.00    0.00    0.00    5.77    0.86    0.00
       1       1      62    1.60    3870    3499       0    6.75    0.35    0.24   91.06      29
       2       2      63    1.63    3863    3499       0    3.72    1.08    0.28   93.29      31
       3       3      58    1.51    3867    3499       0    0.88    0.74    0.20   96.67      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      61    1.58    3864    3499       0    2.03    0.78    0.29   95.31      32      34    0.00    0.00    0.00    0.00    5.42    0.83    0.00
       0       0      57    1.48    3860    3499       0    0.82    0.86    0.34   96.50      29      34    0.00    0.00    0.00    0.00    5.42    0.83    0.00
       1       1      56    1.44    3867    3499       0    3.08    1.08    0.48   93.93      29
       2       2      63    1.64    3861    3499       0    3.09    0.61    0.22   94.44      31
       3       3      69    1.78    3868    3499       0    1.15    0.57    0.13   96.37      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      62    1.61    3864    3499       0    4.38    0.76    0.26   92.99      32      35    0.00    0.00    0.00    0.00    5.66    0.90    0.00
       0       0      53    1.38    3860    3499       0    2.58    0.89    0.10   95.05      30      35    0.00    0.00    0.00    0.00    5.66    0.90    0.00
       1       1      66    1.69    3872    3499       0   11.54    0.67    0.35   85.75      29
       2       2      69    1.79    3860    3499       0    1.82    0.73    0.26   95.40      32
       3       3      61    1.58    3863    3499       0    1.57    0.76    0.33   95.76      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      96    2.47    3871    3499       0    3.64    0.74    0.25   92.91      32      36    0.00    0.00    0.00    0.00    6.55    1.40    0.00
       0       0      91    2.34    3871    3499       0    4.59    1.08    0.37   91.62      31      36    0.00    0.00    0.00    0.00    6.55    1.40    0.00
       1       1      73    1.90    3862    3499       0    1.86    0.55    0.22   95.47      28
       2       2     115    2.98    3875    3499       0    6.42    0.41    0.12   90.07      31
       3       3     103    2.65    3871    3499       0    1.70    0.91    0.28   94.46      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      62    1.60    3866    3499       0    3.01    0.79    0.28   94.31      32      36    0.00    0.00    0.00    0.00    5.81    0.90    0.00
       0       0      66    1.71    3869    3499       0    4.12    1.32    0.18   92.66      31      36    0.00    0.00    0.00    0.00    5.81    0.90    0.00
       1       1      55    1.42    3863    3499       0    3.29    0.52    0.34   94.43      29
       2       2      63    1.63    3863    3499       0    2.11    0.72    0.23   95.32      32
       3       3      64    1.66    3868    3499       0    2.54    0.62    0.37   94.82      31
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      56    1.44    3862    3499       0    4.28    0.85    0.24   93.18      32      36    0.00    0.00    0.00    0.00    6.04    0.87    0.00
       0       0      60    1.54    3865    3499       0    3.54    1.07    0.36   93.49      30      36    0.00    0.00    0.00    0.00    6.04    0.87    0.00
       1       1      60    1.54    3869    3499       0   11.56    0.74    0.24   85.92      28
       2       2      54    1.41    3857    3499       0    1.41    0.85    0.27   96.06      31
       3       3      49    1.27    3854    3499       0    0.63    0.75    0.09   97.27      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      60    1.55    3859    3499       0    3.98    0.90    0.26   93.30      32      35    0.00    0.00    0.00    0.00    5.52    0.84    0.00
       0       0      58    1.51    3861    3499       0    1.92    1.19    0.35   95.03      29      35    0.00    0.00    0.00    0.00    5.52    0.84    0.00
       1       1      52    1.35    3852    3499       0    4.32    0.77    0.15   93.41      29
       2       2      78    2.02    3866    3499       0    4.45    1.31    0.32   91.89      32
       3       3      50    1.31    3853    3499       0    5.26    0.34    0.23   92.87      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      75    1.94    3866    3499       0    3.41    0.94    0.33   93.39      32      35    0.00    0.00    0.00    0.00    6.02    1.09    0.00
       0       0      56    1.45    3854    3499       0    2.96    0.66    0.20   94.74      30      35    0.00    0.00    0.00    0.00    6.02    1.09    0.00
       1       1      82    2.11    3872    3499       0    5.74    0.56    0.19   91.40      29
       2       2      86    2.22    3869    3499       0    2.34    2.02    0.60   92.82      31
       3       3      77    1.99    3865    3499       0    2.59    0.50    0.32   94.59      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -      98    2.54    3849    3499       0    9.85    1.33    0.61   85.66      35      35    0.00    0.00    0.00    0.00    8.24    1.77    0.00
       0       0     121    3.14    3856    3499       0   10.54    1.40    0.67   84.25      30      35    0.00    0.00    0.00    0.00    8.24    1.77    0.00
       1       1      75    1.97    3838    3499       0    7.93    0.86    0.59   88.65      30
       2       2     109    2.83    3854    3499       0   14.31    1.78    0.62   80.45      31
       3       3      86    2.23    3842    3499       0    6.60    1.28    0.58   89.30      35
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -     369    9.52    3874    3499       0   17.93    3.29    1.98   67.27      33      35    0.00    0.00    0.00    0.00   15.91    6.28    0.00
       0       0     307    7.95    3868    3499       0   22.10    3.38    2.74   63.84      30      35    0.00    0.00    0.00    0.00   15.91    6.28    0.00
       1       1     380    9.82    3872    3499       0   22.31    3.89    1.74   62.25      30
       2       2     639   16.46    3884    3499       0   19.09    3.47    1.24   59.73      33
       3       3     149    3.87    3849    3499       0    8.24    2.40    2.22   83.28      33
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -     334    8.62    3880    3499       0   12.33    2.26    1.13   75.67      33      35    0.00    0.00    0.00    0.00   13.68    5.36    0.00
       0       0     225    5.82    3869    3499       0   14.43    2.58    1.21   75.96      31      35    0.00    0.00    0.00    0.00   13.68    5.36    0.00
       1       1     374    9.62    3883    3499       0   14.09    2.05    1.01   73.23      32
       2       2     381    9.82    3880    3499       0   10.70    2.91    1.36   75.21      33
       3       3     357    9.21    3882    3499       0   10.10    1.51    0.92   78.27      33
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -     155    3.99    3881    3499       0    7.13    0.87    0.36   87.65      32      35    0.00    0.00    0.00    0.00    8.76    2.40    0.00
       0       0     133    3.42    3878    3499       0    5.12    0.88    0.20   90.37      31      35    0.00    0.00    0.00    0.00    8.76    2.40    0.00
       1       1     302    7.77    3889    3499       0   17.03    0.80    0.28   74.12      31
       2       2     123    3.18    3875    3499       0    4.82    0.81    0.58   90.61      31
       3       3      62    1.60    3856    3499       0    1.54    0.99    0.39   95.48      32
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt 
       -       -     136    3.53    3849    3499       0    7.30    2.05    0.80   86.32      32      35    0.00    0.00    0.00    0.00    8.29    2.20    0.00
       0       0     166    4.30    3854    3499       0    5.36    1.86    0.62   87.87      30      35    0.00    0.00    0.00    0.00    8.29    2.20    0.00
       1       1     153    3.97    3855    3499       0   14.75    2.28    1.43   77.58      29
       2       2     125    3.26    3845    3499       0    3.93    2.10    0.67   90.04      31
       3       3     100    2.60    3836    3499       0    5.15    1.95    0.50   89.80      32
```

---

