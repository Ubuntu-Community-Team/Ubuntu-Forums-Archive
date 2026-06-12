---
title: "[ask] problem install snort_inline on ubuntu 9.04"
date: 2009-06-24
forum: Server Platforms
---

### Post by m42h31 on 2009-06-24
hii all..
i was install snort_inline-2.6.1.5 on ubuntu 9.04, i found several error when compiling *(sudo make)* :
```
flowps_snort.c: In function ‘FlowPSInit’:
flowps_snort.c:254: warning: pointer targets in passing argument 2 of ‘FlowPSParseArgs’ differ in signedness
flowps_snort.c: In function ‘flowps_newflow_callback’:
flowps_snort.c:735: warning: pointer targets in passing argument 6 of ‘flowps_score_entry’ differ in signedness
flowps_snort.c: In function ‘score_entry_sprint’:
flowps_snort.c:932: warning: pointer targets in passing argument 1 of ‘snprintf’ differ in signedness
flowps_snort.c:955: warning: pointer targets in passing argument 1 of ‘snprintf’ differ in signedness
flowps_snort.c: In function ‘flowps_mkpacket’:
flowps_snort.c:1017: warning: assuming signed overflow does not occur when assuming that (X + c) < X is always false
make[5]: *** No rule to make target `server_stats.o', needed by `libportscan.a'.  Stop.
make[5]: Leaving directory `/opt/snort_inline-2.6.1.5/src/preprocessors/flow/portscan'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/opt/snort_inline-2.6.1.5/src/preprocessors/flow'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/opt/snort_inline-2.6.1.5/src/preprocessors'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/snort_inline-2.6.1.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/snort_inline-2.6.1.5'
make: *** [all] Error 2
```

i found good solution at [snort_inline faq]("http://snort-inline.sourceforge.net/FAQ.html#compiling") :```

cd /usr/include
mv linux linux.orig
ln -s /usr/src/linux-2.4.24/include/linux linux
```
but this solution not work on ubuntu 9.04, then i try to modify the code :
```
ln -s /usr/src/linux-headers-2.6.28-11/include/linux linux
```  and
```
ln -s /usr/src/linux-headers-2.6.28-12/include/linux linux
```  and
```
ln -s /usr/src/linux-headers-2.6.28-13/include/linux linux
```
but the error not solve.
any idea how to compile snort_inline on ubuntu 9.04??

---

### Post by m42h31 on 2009-06-24
](*,) 	](*,)

---

