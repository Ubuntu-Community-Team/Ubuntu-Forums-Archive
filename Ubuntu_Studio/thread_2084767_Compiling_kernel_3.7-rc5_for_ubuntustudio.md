---
title: "Compiling kernel 3.7-rc5 for ubuntustudio"
date: 2012-11-16
forum: Ubuntu Studio
---

### Post by condomitti on 2012-11-16
Hi guys,

Have you tried compiling the 3.7-rc5 with UbSt?
I'm trying to compile the source but I get two errors.

One, when I try "fakeroot debian/rules binary-indep":

```
cp -a drivers/media/dvb/dvb-core/*.h /home/condomitti/development/linux/source/debian/linux-headers-3.7-rc5/usr/src/linux-headers-3.7-rc5/drivers/media/dvb-core
cp: cannot stat `drivers/media/dvb/dvb-core/*.h': No such file or directory
make: ** [install-headers] Erro 1

```

And the other when I issue "fakeroot debian/rules binary-perarch":

```
make[2]: Entering directory `/home/condomitti/development/linux/source/debian/build/tools-perarch/tools/lib/traceevent'
make[2]: Leaving directory `/home/condomitti/development/linux/source/debian/build/tools-perarch/tools/lib/traceevent'
    LINK perf
libperf.a(pmu.o): In function `pmu_format_parse':
/home/condomitti/development/linux/source/debian/build/tools-perarch/tools/perf/util/pmu.c:50: undefined reference to `perf_pmu_in'
libperf.a(pmu-bison.o): In function `perf_pmu_parse':
/home/condomitti/development/linux/source/debian/build/tools-perarch/tools/perf/util/pmu-bison.c:1317: undefined reference to `perf_pmu_lex'
collect2: error: ld returned 1 exit status
make[1]: *** [perf] Error 1
make[1]: Leaving directory `/home/condomitti/development/linux/source/debian/build/tools-perarch/tools/perf'
make: ** [/home/condomitti/development/linux/source/debian/stamps/stamp-build-perarch] Erro 2

```

Has anyone got these errors?
I have compiled the kernel for ubuntu (not studio) some times in the past without any trouble. Not sure how to solve that now.

Thanks

Condomitti.

---

### Post by pdoes on 2012-12-11
With the 3.7 kernel the media directory layout has changed. The directory dvd doesn't exist by itself anymore.

You would have to try and see if you can work with the raring repository as this has the 3.7 kernel.

---

### Post by jhscheer on 2012-12-12
> **condomitti said:**
> 
I'm trying to compile the source but I get two errors.

One, when I try "fakeroot debian/rules binary-indep":

```
cp -a drivers/media/dvb/dvb-core/*.h /home/condomitti/development/linux/source/debian/linux-headers-3.7-rc5/usr/src/linux-headers-3.7-rc5/drivers/media/dvb-core
cp: cannot stat `drivers/media/dvb/dvb-core/*.h': No such file or directory
make: ** [install-headers] Erro 1

```


I've got the exact same problem, but with 3.7.


> **pdoes said:**
> With the 3.7 kernel the media directory layout has changed. The directory dvd doesn't exist by itself anymore.

You would have to try and see if you can work with the raring repository as this has the 3.7 kernel.

Could you please elaborate this, or point me to additional information?

---

### Post by zibeltbg on 2012-12-14
Hallo guys,

   I have Ubuntu Studio 12.10 with 3.5.0-18-lowlatency  kernel

   my request is to give me a correct tutorial for compiling the same 3.5.0-18-lowlatency  kernel especially for Ubuntu Studio 12.10, because I'm not sure if the instructions for compiling kernel for Ubuntu are correct for Ubuntu Studio
  
  thank you very much

---

### Post by alexr1090 on 2013-01-20
> **jhscheer said:**
> I've got the exact same problem, but with 3.7.




Could you please elaborate this, or point me to additional information?

What I did to get rid of this particular error was to copy the files from dvb-core ( I believe it's in the media directory) to the new dvb-core where it wants it to be. That included making a directory. Next I got a couple more errors and did similar things. Except for the last error when it wanted a file I couldn't find. I simply created a dummy file and hoped nothing went wrong.

---

