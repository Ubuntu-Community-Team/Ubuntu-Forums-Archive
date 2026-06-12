---
title: "fdct_mmx.o missing during Cinelerra compile in Hardy"
date: 2008-12-20
forum: Ubuntu Studio
---

### Post by Brigham on 2008-12-20
I've spent a good deal of time trying to solve this and am resigned to bring it to the community.  Does anyone have a solid solution to this.  Executing "make" from Cinelerra source (acquired via git) I receive this error:

```


ar: .libs/fdct_mmx.o: No such file or directory
make[2]: *** [libmpeg2enc.la] Error 1
make[2]: Leaving directory `/home/michael/my_cinelerra/mpeg2enc'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/michael/my_cinelerra'
make: *** [all] Error 2


```

I've installed the latest "nasm" from sourceforge as another forum post suggested.  The error persists.  I will post below the context of the error shown about.  Make was working in the "mpeg2enc" folder.

```

Making all in mpeg2enc
make[2]: Entering directory `/home/michael/my_cinelerra/mpeg2enc'
/bin/bash ../libtool --tag=CC --tag=CC   --mode=link gcc -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2   -o libmpeg2enc.la  conform.lo mpeg2enc.lo putseq.lo putpic.lo puthdr.lo putmpg.lo putvlc.lo putbits.lo predict.lo readpic.lo writepic.lo transfrm.lo fdctref.lo idct.lo quantize.lo ratectl.lo stats.lo motion.lo cpu_accel.lo fdct_mmx.lo fdctdata.lo idct_mmx.lo idctdata.lo quant_mmx.lo quantize_x86.lo predict_mmx.lo predcomp_mmxe.lo predcomp_mmx.lo  -lm -ldl -lpthread
ar cru .libs/libmpeg2enc.a .libs/conform.o .libs/mpeg2enc.o .libs/putseq.o .libs/putpic.o .libs/puthdr.o .libs/putmpg.o .libs/putvlc.o .libs/putbits.o .libs/predict.o .libs/readpic.o .libs/writepic.o .libs/transfrm.o .libs/fdctref.o .libs/idct.o .libs/quantize.o .libs/ratectl.o .libs/stats.o .libs/motion.o .libs/cpu_accel.o .libs/fdct_mmx.o .libs/fdctdata.o .libs/idct_mmx.o .libs/idctdata.o .libs/quant_mmx.o .libs/quantize_x86.o .libs/predict_mmx.o .libs/predcomp_mmxe.o .libs/predcomp_mmx.o
[I]ar: .libs/fdct_mmx.o: No such file or directory
make[2]: *** [libmpeg2enc.la] Error 1
make[2]: Leaving directory `/home/michael/my_cinelerra/mpeg2enc'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/michael/my_cinelerra'
make: *** [all] Error 2[/I]

```

---

### Post by Brigham on 2008-12-21
The error isn't fixed, but I found a repository version suited for my system (cinelerra-smp: good for multiprocessor system using OpenGL 2.0).

---

