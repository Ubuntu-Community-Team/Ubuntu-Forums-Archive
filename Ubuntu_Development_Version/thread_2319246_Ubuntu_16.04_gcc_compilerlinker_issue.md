---
title: "Ubuntu 16.04 gcc compiler/linker issue"
date: 2016-04-02
forum: Ubuntu Development Version
---

### Post by W9DKI on 2016-04-02
using the c-code ( see  the C11 codes at github.com  w9dki  -- some ruminations):  I find that i now have to use the gcc-5 linker option  -static

in 15.04 or 15.10 and in 16.04 

gcc-5 -std=gnu11 -Wall -static -Ofast -msse2 -frename-registers -malign-double -fno-strict-aliasing -DHAVE_SSE2=1 -DDSFMT_MEXP=19937 -o randn_complex_7 dSFMT.c randn_complex_7.c -lm -lrt -lgsl -lgslcblas

gsl_zigg_dsfmt                              = 0.40294689 (s) 
Box-Muller                                     = 1.08208780 (s) 
SIMD Box-Muller with fast_sin-cos  = 0.54119308 (s) 
Box-Muller manual SIMD                = 0.56403200 (s) 
SIMD Marsaglia polar                     = 0.53167263 (s) 
Time for Leva Gaussian ratio           = 0.37637315 (s) 


when the -static option is not used we get in 16.04 (but only for the Intel I7 in turbo mode @4.5GHz, and not for a T9900 Core-Duo at 3.02GHz)

gcc-5 -std=gnu11 -Wall  -Ofast -msse2 -frename-registers -malign-double -fno-strict-aliasing -DHAVE_SSE2=1 -DDSFMT_MEXP=19937 -o randn_complex_7 dSFMT.c randn_complex_7.c -lm -lrt -lgsl -lgslcblas

gsl_zigg_dsfmt                              = 0.45731819 (s) 
Box-Muller                                     = 1.87405287 (s) 
SIMD Box-Muller with fast_sin-cos  = 1.40218740 (s) 
Box-Muller manual SIMD                = 1.39679041 (s) 
SIMD Marsaglia polar                     = 1.31057323 (s) 
Time for Leva Gaussian ratio          = 0.39094781 (s) 

Note the factor of 2 to 2.6 slow down for the Box-Muller and Marsaglia algorithms without using the gcc -static option,  that was not seen for 15.04 or 15.10, or for Ubuntu 16.04 and a Core duo T9900/.  I get the same results for gcc-4.8 and gcc-4.9 in Ubuntu 16.04

So it is the Ubuntu 16.04  gcc linker, not the gcc-5 compiler itself.

This occurs only for an Intel i7 running at 4.5 GHz in single thread,  turbo mode.   This behavior is not seen for a mobile Core-Duo T9900 laptop and Ubuntu 16.04.   And the c  code even runs almost twice as fast in the laptop, without the -static option.  However, the -static option changes everything for the i7... but only for Ubuntu 16.04 and not 15.04 or 15.10.  Go figure?  

 A fresh, clean  Ubuntu 16.04 install 12 hours ago did not change anything for the water cooled Intel i7.

W9DKI
2 Apr 2016
[EMAIL="dlwalters@hspacetech.com"]dlwalters@hspacetech.com[/EMAIL]

---

