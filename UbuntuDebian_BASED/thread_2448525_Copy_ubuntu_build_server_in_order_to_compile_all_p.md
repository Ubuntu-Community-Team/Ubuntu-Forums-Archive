---
title: "Copy ubuntu build server in order to compile all packages with optimized CFLAGS"
date: 2020-08-09
forum: Ubuntu/Debian BASED
---

### Post by eliax on 2020-08-09
Dear Ubuntu community,
I one wished to, would it be possible to clone an Ubuntu build server in order to compile all ubuntu packages with optimized CFLAGS?

Raspberry Pi 4 64 bit build, specifically tuned to the cortex-a72 CPU:
CFLAGS="-O2 -pipe -march=armv8-a+crc+simd -mtune=cortex-a72 -mfloat-abi=hard -mfpu=vfp -meabi=5 -fomit-frame-pointer -ftree-vectorize -fpredictive-commoning"

and then the binaries would be stripped from unnecessary data with:
strip -s [binary name]

would it at all be possible?

---

