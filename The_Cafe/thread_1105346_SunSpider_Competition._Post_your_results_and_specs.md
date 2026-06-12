---
title: "SunSpider Competition. Post your results and specs!"
date: 2009-03-24
forum: The Cafe
---

### Post by artir on 2009-03-24
I did the test my main PC, which has a Q6600(4*2.4 Ghz), 2 GB ram(667 Mhz) and a 8600GT graphic card.

I used  WebkitGTK 1.1.3 compiled with a patch to enable JIT on 64 bit systems and run the test on Epiphany 2.27 unstable on Ubuntu Intrepid x64.
Beat this:! :D

Result:651.5ms

---

### Post by gletob on 2009-03-24
Check this out :-P
Intel Pentium Dual core 1.47Ghz, Intel G965, 2.5 Gb Ram

4999.8 ms

[http://preview.tinyurl.com/dx9l56](http://preview.tinyurl.com/dx9l56)

---

### Post by klange on 2009-03-24
FF3.0 on Windows 7 (Don't ask); 2*1.7GHz Core Duo; 1GB RAM; Intel GMA 950
```
--------------------------------------------
Total:                  4692.4ms +/- 2.9%
--------------------------------------------

  3d:                    538.0ms +/- 1.7%
    cube:                196.4ms +/- 2.7%
    morph:               174.4ms +/- 2.1%
    raytrace:            167.2ms +/- 3.7%

  access:                736.2ms +/- 5.2%
    binary-trees:         76.0ms +/- 49.4%
    fannkuch:            352.8ms +/- 1.4%
    nbody:               195.0ms +/- 0.6%
    nsieve:              112.4ms +/- 4.0%

  bitops:                533.0ms +/- 1.2%
    3bit-bits-in-byte:    99.2ms +/- 1.4%
    bits-in-byte:        138.2ms +/- 1.2%
    bitwise-and:         124.4ms +/- 4.9%
    nsieve-bits:         171.2ms +/- 1.6%

  controlflow:            60.8ms +/- 0.9%
    recursive:            60.8ms +/- 0.9%

  crypto:                296.6ms +/- 2.4%
    aes:                 112.2ms +/- 1.2%
    md5:                  88.6ms +/- 2.5%
    sha1:                 95.8ms +/- 7.2%

  date:                  408.4ms +/- 7.8%
    format-tofte:        250.6ms +/- 14.7%
    format-xparb:        157.8ms +/- 6.4%

  math:                  537.6ms +/- 5.3%
    cordic:              251.0ms +/- 1.6%
    partial-sums:        182.0ms +/- 9.6%
    spectral-norm:       104.6ms +/- 15.6%

  regexp:                395.8ms +/- 8.7%
    dna:                 395.8ms +/- 8.7%

  string:               1186.0ms +/- 6.2%
    base64:              161.4ms +/- 61.9%
    fasta:               243.4ms +/- 4.2%
    tagcloud:            213.2ms +/- 3.7%
    unpack-code:         413.6ms +/- 6.7%
    validate-input:      154.4ms +/- 6.5%
```

---

### Post by unoodles on 2009-03-24
meh. Core 2 Duo 1.8 Ghz. Intel 965. Firefox 3.0.0.7. Ubuntu 8.10

```
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  4565.8ms +/- 3.7%
--------------------------------------------

  3d:                    565.4ms +/- 2.5%
    cube:                210.6ms +/- 6.8%
    morph:               181.4ms +/- 12.6%
    raytrace:            173.4ms +/- 12.0%

  access:                641.8ms +/- 9.9%
    binary-trees:         91.6ms +/- 12.2%
    fannkuch:            242.6ms +/- 12.3%
    nbody:               207.8ms +/- 11.9%
    nsieve:               99.8ms +/- 18.5%

  bitops:                462.4ms +/- 5.1%
    3bit-bits-in-byte:    83.2ms +/- 28.6%
    bits-in-byte:        110.2ms +/- 13.2%
    bitwise-and:         117.4ms +/- 6.7%
    nsieve-bits:         151.6ms +/- 13.1%

  controlflow:            70.6ms +/- 27.6%
    recursive:            70.6ms +/- 27.6%

  crypto:                305.6ms +/- 17.3%
    aes:                 115.4ms +/- 27.2%
    md5:                  93.6ms +/- 26.3%
    sha1:                 96.6ms +/- 24.9%

  date:                  488.2ms +/- 6.1%
    format-tofte:        293.2ms +/- 3.5%
    format-xparb:        195.0ms +/- 12.7%

  math:                  518.8ms +/- 9.4%
    cordic:              207.8ms +/- 7.3%
    partial-sums:        199.2ms +/- 8.1%
    spectral-norm:       111.8ms +/- 18.2%

  regexp:                358.6ms +/- 11.2%
    dna:                 358.6ms +/- 11.2%

  string:               1154.4ms +/- 5.4%
    base64:              132.6ms +/- 8.1%
    fasta:               244.4ms +/- 5.8%
    tagcloud:            234.0ms +/- 7.8%
    unpack-code:         376.6ms +/- 15.5%
    validate-input:      166.8ms +/- 7.9%
```

Edit: Just did it on the same machine in Chromium.

```

============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 1536.2ms +/- 5.3%
--------------------------------------------

  3d:                   213.6ms +/- 20.7%
    cube:                64.4ms +/- 32.4%
    morph:               70.0ms +/- 34.4%
    raytrace:            79.2ms +/- 8.6%

  access:               136.2ms +/- 20.7%
    binary-trees:         7.6ms +/- 55.0%
    fannkuch:            57.4ms +/- 30.7%
    nbody:               45.0ms +/- 45.1%
    nsieve:              26.2ms +/- 6.2%

  bitops:               128.4ms +/- 5.4%
    3bit-bits-in-byte:   11.6ms +/- 5.9%
    bits-in-byte:        26.6ms +/- 16.7%
    bitwise-and:         31.8ms +/- 7.5%
    nsieve-bits:         58.4ms +/- 11.5%

  controlflow:            8.0ms +/- 44.0%
    recursive:            8.0ms +/- 44.0%

  crypto:               122.8ms +/- 36.3%
    aes:                 32.8ms +/- 69.3%
    md5:                 49.4ms +/- 34.4%
    sha1:                40.6ms +/- 42.4%

  date:                 182.8ms +/- 34.7%
    format-tofte:        90.8ms +/- 38.8%
    format-xparb:        92.0ms +/- 35.4%

  math:                 171.2ms +/- 25.4%
    cordic:              53.0ms +/- 34.6%
    partial-sums:        86.4ms +/- 34.2%
    spectral-norm:       31.8ms +/- 13.1%

  regexp:                53.2ms +/- 38.2%
    dna:                 53.2ms +/- 38.2%

  string:               520.0ms +/- 10.7%
    base64:              77.4ms +/- 23.5%
    fasta:               76.4ms +/- 42.3%
    tagcloud:           120.2ms +/- 24.0%
    unpack-code:        138.8ms +/- 10.8%
    validate-input:     107.2ms +/- 28.5%
```

---

### Post by aktiwers on 2009-03-24
Just installed Firefox 3.1 on my Q9550 (Quadro 2.4ghz), 4gb ram, 9800GTX..  Ubuntu 8.10 64bit.

Total:                 1982.0ms +/- 3.1%

---

