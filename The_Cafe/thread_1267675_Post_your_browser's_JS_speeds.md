---
title: "Post your browser's JS speeds"
date: 2009-09-16
forum: The Cafe
---

### Post by doorknob60 on 2009-09-16
Never though I'd post another one of these browser wars type threads...but here goes nothing.

Inspired form this thread: [http://bbs.archlinux.org/viewtopic.php?pid=620262#p620262](http://bbs.archlinux.org/viewtopic.php?pid=620262#p620262)

Here's the test I used: [http://www2.webkit.org/perf/sunspider-0.9/sunspider.html](http://www2.webkit.org/perf/sunspider-0.9/sunspider.html)

Here's my results, ordered from fastest to slowest. All software is at latest version:

Midori: 724.4ms
Chromium: 726.6ms
Firefox: 4378.0ms
Konqueror: 5114.0ms
Opera: 6295.0ms

Surprised? Yeah, me too. Opera fanboys always saying how much faster Opera is than Firefox? Psh...Well I guess I give them credit Opera works a lot better on older computers, but still...

My conclusions:
1. Firefox is faster than people make it out to be (shut it, Opera fanboys!)
2. Webkit kicks any other rendering engine's butt :)
3. I still don't care, Firefox and its extensions FTW.

Also, I'd like to add that they're all great browsers, and all better than IE, I'm not just being a fanboy, I'm just posting my results that I found interesting, and hope you guys find them interesting as well.

---

### Post by Jesus_Valdez on 2009-09-16
Midori!!!!! Yeah!

============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  **747.4ms +/- 3.4%**
--------------------------------------------

  3d:                    93.0ms +/- 6.2%
    cube:                24.2ms +/- 4.3%
    morph:               40.6ms +/- 6.0%
    raytrace:            28.2ms +/- 26.9%

  access:                57.8ms +/- 5.6%
    binary-trees:         8.2ms +/- 12.7%
    fannkuch:            20.0ms +/- 11.6%
    nbody:               14.0ms +/- 6.3%
    nsieve:              15.6ms +/- 9.1%

  bitops:                27.4ms +/- 16.5%
    3bit-bits-in-byte:    3.4ms +/- 20.0%
    bits-in-byte:         8.6ms +/- 16.5%
    bitwise-and:          6.4ms +/- 50.7%
    nsieve-bits:          9.0ms +/- 13.8%

  controlflow:            4.2ms +/- 13.2%
    recursive:            4.2ms +/- 13.2%

  crypto:                37.4ms +/- 5.0%
    aes:                 21.0ms +/- 4.2%
    md5:                  9.4ms +/- 11.8%
    sha1:                 7.0ms +/- 12.6%

  date:                 137.4ms +/- 9.3%
    format-tofte:        59.4ms +/- 11.8%
    format-xparb:        78.0ms +/- 14.6%

  math:                  57.4ms +/- 7.6%
    cordic:              12.8ms +/- 17.4%
    partial-sums:        34.8ms +/- 5.9%
    spectral-norm:        9.8ms +/- 5.7%

  regexp:                36.8ms +/- 4.4%
    dna:                 36.8ms +/- 4.4%

  string:               296.0ms +/- 9.7%
    base64:              29.2ms +/- 3.6%
    fasta:               50.0ms +/- 14.5%
    tagcloud:            56.2ms +/- 11.2%
    unpack-code:         93.4ms +/- 11.8%
    validate-input:      67.2ms +/- 23.9%

---

### Post by YeOK on 2009-09-16
Chromium 4.0.208.0 64bit,

> 
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  **455.6ms** +/- 4.7%
--------------------------------------------

  3d:                    82.8ms +/- 15.4%
    cube:                31.6ms +/- 32.3%
    morph:               28.2ms +/- 7.2%
    raytrace:            23.0ms +/- 15.8%

  access:                35.2ms +/- 4.6%
    binary-trees:         1.6ms +/- 42.6%
    fannkuch:            11.4ms +/- 6.0%
    nbody:               18.4ms +/- 7.7%
    nsieve:               3.8ms +/- 14.6%

  bitops:                32.4ms +/- 2.1%
    3bit-bits-in-byte:    2.4ms +/- 28.4%
    bits-in-byte:         6.8ms +/- 8.2%
    bitwise-and:          9.6ms +/- 7.1%
    nsieve-bits:         13.6ms +/- 5.0%

  controlflow:            2.2ms +/- 25.3%
    recursive:            2.2ms +/- 25.3%

  crypto:                26.0ms +/- 8.3%
    aes:                  9.6ms +/- 17.4%
    md5:                  8.4ms +/- 8.1%
    sha1:                 8.0ms +/- 0.0%

  date:                  63.0ms +/- 5.8%
    format-tofte:        26.8ms +/- 7.6%
    format-xparb:        36.2ms +/- 5.6%

  math:                  47.2ms +/- 2.2%
    cordic:              18.8ms +/- 3.0%
    partial-sums:        18.8ms +/- 3.0%
    spectral-norm:        9.6ms +/- 11.6%

  regexp:                10.8ms +/- 18.9%
    dna:                 10.8ms +/- 18.9%

  string:               156.0ms +/- 6.0%
    base64:              16.4ms +/- 8.6%
    fasta:               26.2ms +/- 2.1%
    tagcloud:            31.6ms +/- 7.7%
    unpack-code:         53.4ms +/- 10.1%
    validate-input:      28.4ms +/- 11.4%


Firefox Minefield 3.7a1pre 64bit

> 
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 **1913.0ms** +/- 1.2%
--------------------------------------------

  3d:                   257.4ms +/- 2.5%
    cube:                95.0ms +/- 3.3%
    morph:               83.8ms +/- 1.2%
    raytrace:            78.6ms +/- 5.7%

  access:               339.2ms +/- 3.0%
    binary-trees:        32.0ms +/- 0.0%
    fannkuch:           164.4ms +/- 1.5%
    nbody:               98.2ms +/- 9.1%
    nsieve:              44.6ms +/- 3.2%

  bitops:               223.2ms +/- 0.8%
    3bit-bits-in-byte:   36.6ms +/- 3.0%
    bits-in-byte:        57.2ms +/- 1.8%
    bitwise-and:         52.4ms +/- 2.1%
    nsieve-bits:         77.0ms +/- 2.8%

  controlflow:           29.8ms +/- 1.9%
    recursive:           29.8ms +/- 1.9%

  crypto:               126.0ms +/- 0.7%
    aes:                 51.6ms +/- 1.3%
    md5:                 36.4ms +/- 1.9%
    sha1:                38.0ms +/- 0.0%

  date:                 132.0ms +/- 2.2%
    format-tofte:        62.4ms +/- 4.6%
    format-xparb:        69.6ms +/- 1.0%

  math:                 226.2ms +/- 2.0%
    cordic:             102.6ms +/- 3.2%
    partial-sums:        75.4ms +/- 1.5%
    spectral-norm:       48.2ms +/- 2.2%

  regexp:               158.6ms +/- 3.9%
    dna:                158.6ms +/- 3.9%

  string:               420.6ms +/- 7.3%
    base64:              38.6ms +/- 1.8%
    fasta:              103.6ms +/- 5.3%
    tagcloud:            93.0ms +/- 12.4%
    unpack-code:        127.8ms +/- 15.7%
    validate-input:      57.6ms +/- 11.6%


More tests, Opera 10.10 64bit
> 
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 **3302.0ms** +/- 1.0%
--------------------------------------------

  3d:                   401.8ms +/- 2.1%
    cube:               122.0ms +/- 1.6%
    morph:              169.6ms +/- 4.7%
    raytrace:           110.2ms +/- 1.5%

  access:               551.4ms +/- 2.6%
    binary-trees:        41.0ms +/- 3.7%
    fannkuch:           282.4ms +/- 4.7%
    nbody:              122.6ms +/- 4.3%
    nsieve:             105.4ms +/- 3.4%

  bitops:               591.4ms +/- 3.4%
    3bit-bits-in-byte:   50.0ms +/- 3.0%
    bits-in-byte:       117.2ms +/- 11.7%
    bitwise-and:        274.8ms +/- 5.0%
    nsieve-bits:        149.4ms +/- 4.6%

  controlflow:           53.8ms +/- 9.4%
    recursive:           53.8ms +/- 9.4%

  crypto:               222.2ms +/- 2.7%
    aes:                107.6ms +/- 2.1%
    md5:                 58.4ms +/- 4.4%
    sha1:                56.2ms +/- 6.1%

  date:                 210.0ms +/- 2.9%
    format-tofte:       133.2ms +/- 3.6%
    format-xparb:        76.8ms +/- 4.2%

  math:                 336.8ms +/- 1.8%
    cordic:             145.4ms +/- 3.2%
    partial-sums:       118.4ms +/- 4.2%
    spectral-norm:       73.0ms +/- 5.1%

  regexp:                76.6ms +/- 3.4%
    dna:                 76.6ms +/- 3.4%

  string:               858.0ms +/- 2.8%
    base64:              93.6ms +/- 2.9%
    fasta:              199.8ms +/- 4.5%
    tagcloud:           129.6ms +/- 5.4%
    unpack-code:        314.8ms +/- 3.8%
    validate-input:     120.2ms +/- 10.5%


Midori 0.1.9 

> 
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  **384.6ms** +/- 0.6%
--------------------------------------------

  3d:                    57.4ms +/- 2.9%
    cube:                14.6ms +/- 4.7%
    morph:               27.6ms +/- 2.5%
    raytrace:            15.2ms +/- 3.7%

  access:                33.2ms +/- 4.1%
    binary-trees:         4.2ms +/- 13.2%
    fannkuch:            11.6ms +/- 5.9%
    nbody:               10.2ms +/- 5.5%
    nsieve:               7.2ms +/- 7.7%

  bitops:                17.0ms +/- 7.3%
    3bit-bits-in-byte:    2.4ms +/- 28.4%
    bits-in-byte:         5.6ms +/- 12.2%
    bitwise-and:          3.8ms +/- 14.6%
    nsieve-bits:          5.2ms +/- 10.7%

  controlflow:            2.8ms +/- 19.9%
    recursive:            2.8ms +/- 19.9%

  crypto:                21.2ms +/- 2.6%
    aes:                 10.2ms +/- 5.5%
    md5:                  6.2ms +/- 9.0%
    sha1:                 4.8ms +/- 11.6%

  date:                  60.2ms +/- 3.7%
    format-tofte:        25.0ms +/- 8.6%
    format-xparb:        35.2ms +/- 1.6%

  math:                  41.8ms +/- 2.5%
    cordic:              10.0ms +/- 0.0%
    partial-sums:        23.4ms +/- 2.9%
    spectral-norm:        8.4ms +/- 8.1%

  regexp:                16.0ms +/- 7.8%
    dna:                 16.0ms +/- 7.8%

  string:               135.0ms +/- 1.1%
    base64:              14.0ms +/- 0.0%
    fasta:               25.6ms +/- 2.7%
    tagcloud:            29.0ms +/- 3.0%
    unpack-code:         40.8ms +/- 1.4%
    validate-input:      25.6ms +/- 2.7%


---

### Post by misfitpierce on 2009-09-16
These are based on test's though... From personal experience of actual webpages used on daily bases for most users like myspace, ubuntuforums, deviantart and so on firefox usually renders it faster from what I have seen and counted. Firefox all the way for me with pipelining turned on.

---

### Post by Colonel Kilkenny on 2009-09-16
JavaScript benchmarks are actually quite small part of the browsing experience. Browsing is not just JS, it's CSS, reflows, DOM, etc. and Opera usually is amazing at those things.
WebKit and Gecko have both new JavaScript engine, Opera has still quite "old" one. Carakan (Opera's new JavaScript engine) should be much faster. So that explains why Opera is atm. perhaps a bit more slower than WebKit and Gecko in JS.

I'm not surprised that WebKit is the fastest. It's fast engine and Sunspider is their own benchmark... Gecko browsers are probably relatively better when testing with Dromaeo etc. :)

---

### Post by PurposeOfReason on 2009-09-16
Something is up with all of your FF tests.
```


============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 1076.2ms +/- 0.4%
--------------------------------------------

  3d:                   160.4ms +/- 0.4%
    cube:                49.4ms +/- 1.4%
    morph:               33.8ms +/- 1.6%
    raytrace:            77.2ms +/- 0.7%

  access:               137.6ms +/- 1.4%
    binary-trees:        38.6ms +/- 2.9%
    fannkuch:            61.4ms +/- 1.1%
    nbody:               26.8ms +/- 2.1%
    nsieve:              10.8ms +/- 9.6%

  bitops:                37.0ms +/- 2.4%
    3bit-bits-in-byte:    1.2ms +/- 46.3%
    bits-in-byte:         8.8ms +/- 6.3%
    bitwise-and:          2.2ms +/- 25.3%
    nsieve-bits:         24.8ms +/- 4.2%

  controlflow:           35.2ms +/- 1.6%
    recursive:           35.2ms +/- 1.6%

  crypto:                62.0ms +/- 2.5%
    aes:                 35.8ms +/- 2.9%
    md5:                 17.2ms +/- 3.2%
    sha1:                 9.0ms +/- 0.0%

  date:                 169.0ms +/- 1.3%
    format-tofte:        94.2ms +/- 2.0%
    format-xparb:        74.8ms +/- 1.4%

  math:                  56.0ms +/- 5.2%
    cordic:              30.8ms +/- 5.3%
    partial-sums:        18.4ms +/- 3.7%
    spectral-norm:        6.8ms +/- 23.8%

  regexp:                59.0ms +/- 1.5%
    dna:                 59.0ms +/- 1.5%

  string:               360.0ms +/- 0.8%
    base64:              19.2ms +/- 2.9%
    fasta:               82.2ms +/- 4.2%
    tagcloud:            96.0ms +/- 0.9%
    unpack-code:        126.4ms +/- 2.0%
    validate-input:      36.2ms +/- 1.5%
```

---

### Post by lovinglinux on 2009-09-16
I have been using [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) benchmark test for a while and it seems to be very reliable. It's produced by Futuremark, which is a leading company in 3D game benchmarking. The tests performed by Peacekeeper are not only JavaScript, but involves DOM and String operations, among other tests.

Here are my benchmarks results, by date and browser ([COLOR="Red"]**higher values are better**[/COLOR]). Please notice that the first tests were made on a vanilla Jaunty installation and subsequent tests were carried after [Firefox tweaks](http://ubuntuforums.org/showthread.php?t=1193567) and [Ubuntu tweaks](http://ubuntuforums.org/showthread.php?t=1193567).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124167&stc=1&d=1249840668[/IMG]

> Note: optimized versions were compiled from source with optimization flags for my processor. 

I have tested Chromium yesterday again and it scored impressive 1900 points.

---

### Post by sunchiqua on 2009-09-16
Mozilla Firefox 3.0 @ Crunchbang

```
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  7135.4ms +/- 0.8%
--------------------------------------------

  3d:                    901.6ms +/- 2.3%
    cube:                331.4ms +/- 5.3%
    morph:               318.2ms +/- 3.0%
    raytrace:            252.0ms +/- 3.3%

  access:               1143.0ms +/- 4.3%
    binary-trees:        113.0ms +/- 9.6%
    fannkuch:            497.6ms +/- 3.9%
    nbody:               354.4ms +/- 7.3%
    nsieve:              178.0ms +/- 3.2%

  bitops:                841.8ms +/- 2.7%
    3bit-bits-in-byte:   161.6ms +/- 7.4%
    bits-in-byte:        195.6ms +/- 4.1%
    bitwise-and:         201.8ms +/- 4.6%
    nsieve-bits:         282.8ms +/- 0.7%

  controlflow:            86.4ms +/- 2.4%
    recursive:            86.4ms +/- 2.4%

  crypto:                450.2ms +/- 3.3%
    aes:                 182.8ms +/- 9.5%
    md5:                 133.4ms +/- 9.2%
    sha1:                134.0ms +/- 8.6%

  date:                  689.0ms +/- 2.2%
    format-tofte:        443.0ms +/- 3.2%
    format-xparb:        246.0ms +/- 3.4%

  math:                  834.4ms +/- 3.6%
    cordic:              338.8ms +/- 3.5%
    partial-sums:        304.6ms +/- 9.4%
    spectral-norm:       191.0ms +/- 5.8%

  regexp:                546.4ms +/- 9.0%
    dna:                 546.4ms +/- 9.0%

  string:               1642.6ms +/- 1.5%
    base64:              202.2ms +/- 6.1%
    fasta:               415.8ms +/- 1.9%
    tagcloud:            301.4ms +/- 4.7%
    unpack-code:         489.8ms +/- 3.1%
    validate-input:      233.4ms +/- 4.7%
```

---

### Post by TheStroj on 2009-09-16
The fact is that Chromium is the fastest no matter what tests you do. Opera is slow, Firefox 3.5 is a bit faster, but still slow, comparing to chromium.

---

### Post by c2006 on 2009-09-16
sunchiqua, how many plugins do you have?!? That's an insanely high figure!


```
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 1549.8ms +/- 1.5%
--------------------------------------------

  3d:                   229.4ms +/- 1.2%
    cube:                69.6ms +/- 3.5%
    morph:               50.0ms +/- 1.8%
    raytrace:           109.8ms +/- 3.4%

  access:               208.6ms +/- 0.3%
    binary-trees:        57.4ms +/- 1.2%
    fannkuch:            95.4ms +/- 0.7%
    nbody:               39.2ms +/- 1.4%
    nsieve:              16.6ms +/- 4.1%

  bitops:                51.6ms +/- 2.2%
    3bit-bits-in-byte:    1.6ms +/- 42.6%
    bits-in-byte:        10.2ms +/- 5.5%
    bitwise-and:          3.0ms +/- 0.0%
    nsieve-bits:         36.8ms +/- 1.5%

  controlflow:           48.8ms +/- 1.1%
    recursive:           48.8ms +/- 1.1%

  crypto:                84.4ms +/- 6.3%
    aes:                 48.8ms +/- 6.6%
    md5:                 23.2ms +/- 12.8%
    sha1:                12.4ms +/- 5.5%

  date:                 234.0ms +/- 4.3%
    format-tofte:       125.2ms +/- 8.7%
    format-xparb:       108.8ms +/- 1.5%

  math:                  93.6ms +/- 9.6%
    cordic:              55.6ms +/- 16.2%
    partial-sums:        28.6ms +/- 2.4%
    spectral-norm:        9.4ms +/- 7.2%

  regexp:                84.0ms +/- 7.8%
    dna:                 84.0ms +/- 7.8%

  string:               515.4ms +/- 1.5%
    base64:              26.8ms +/- 15.2%
    fasta:              119.6ms +/- 4.4%
    tagcloud:           140.6ms +/- 6.3%
    unpack-code:        172.8ms +/- 5.7%
    validate-input:      55.6ms +/- 3.4%

```

Probably higher than I'd like because a) I've got umpteen tabs running (as usual), b) all of my plugins are on, and c) this is a highly non-standard setup I've got going (I'll re-standardise on 64-bit with 9.10).

---

### Post by sunchiqua on 2009-09-16
> **c2006 said:**
> sunchiqua, how many plugins do you have?!? That's an insanely high figure!
 
Probably higher than I'd like because a) I've got umpteen tabs running (as usual), b) all of my plugins are on, and c) this is a highly non-standard setup I've got going (I'll re-standardise on 64-bit with 9.10).
 
Only 1 additional plugin - Firebug. Not even sure why it's so slow .. haven't had any problems with JS/AJAX :)

---

### Post by YeOK on 2009-09-16
> **Colonel Kilkenny said:**
> JavaScript benchmarks are actually quite small part of the browsing experience. Browsing is not just JS, it's CSS, reflows, DOM, etc. and Opera usually is amazing at those things.
WebKit and Gecko have both new JavaScript engine, Opera has still quite "old" one. Carakan (Opera's new JavaScript engine) should be much faster. So that explains why Opera is atm. perhaps a bit more slower than WebKit and Gecko in JS.

I'm not surprised that WebKit is the fastest. It's fast engine and Sunspider is their own benchmark... Gecko browsers are probably relatively better when testing with Dromaeo etc. :)

Google Chrome / Chromium uses its own Javascript engine called V8, it only uses Webkit to render the html.

[http://code.google.com/p/v8/](http://code.google.com/p/v8/)

I also added a few more tests to my original post.

---

### Post by artir on 2009-09-16
GOTO [http://ubuntuforums.org/showthread.php?t=1105346](http://ubuntuforums.org/showthread.php?t=1105346)

I achieved 651.5ms on epiphany, with webkit 1.1.3 on intrepid x86_64 (webkit patched to allow 64 bits JIT)

I think that would be even faster if I redid it again, thing i'll do in karmic (when I did it it was the fastest JS speed posted ever on the internet due to the not-so known patch)

---

### Post by falconindy on 2009-09-16
**Chromium64 4.0.209.0**
WebKit:
```
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  395.0ms +/- 4.6%
--------------------------------------------

  3d:                    64.0ms +/- 7.9%
    cube:                23.6ms +/- 15.2%
    morph:               20.8ms +/- 20.9%
    raytrace:            19.6ms +/- 5.7%

  access:                30.8ms +/- 8.8%
    binary-trees:         2.0ms +/- 0.0%
    fannkuch:            12.2ms +/- 22.1%
    nbody:               13.4ms +/- 8.3%
    nsieve:               3.2ms +/- 17.4%

  bitops:                29.8ms +/- 3.5%
    3bit-bits-in-byte:    2.4ms +/- 28.4%
    bits-in-byte:         6.4ms +/- 10.6%
    bitwise-and:          9.0ms +/- 0.0%
    nsieve-bits:         12.0ms +/- 0.0%

  controlflow:            2.6ms +/- 26.2%
    recursive:            2.6ms +/- 26.2%

  crypto:                23.4ms +/- 6.1%
    aes:                  7.6ms +/- 14.6%
    md5:                  8.2ms +/- 6.8%
    sha1:                 7.6ms +/- 9.0%

  date:                  64.8ms +/- 4.2%
    format-tofte:        26.2ms +/- 4.0%
    format-xparb:        38.6ms +/- 5.4%

  math:                  40.4ms +/- 6.0%
    cordic:              18.4ms +/- 10.2%
    partial-sums:        15.8ms +/- 10.3%
    spectral-norm:        6.2ms +/- 9.0%

  regexp:                11.4ms +/- 52.6%
    dna:                 11.4ms +/- 52.6%

  string:               127.8ms +/- 2.1%
    base64:              12.8ms +/- 4.3%
    fasta:               22.0ms +/- 4.0%
    tagcloud:            26.6ms +/- 4.2%
    unpack-code:         40.0ms +/- 2.2%
    validate-input:      26.4ms +/- 7.1%
```
Peacekeeper score is 3785.

Sigh, if only Chromium was a little more stable.

---

### Post by TheStroj on 2009-09-16
> **falconindy said:**
> **Chromium64 4.0.209.0**
WebKit:
```
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  395.0ms +/- 4.6%
--------------------------------------------

  3d:                    64.0ms +/- 7.9%
    cube:                23.6ms +/- 15.2%
    morph:               20.8ms +/- 20.9%
    raytrace:            19.6ms +/- 5.7%

  access:                30.8ms +/- 8.8%
    binary-trees:         2.0ms +/- 0.0%
    fannkuch:            12.2ms +/- 22.1%
    nbody:               13.4ms +/- 8.3%
    nsieve:               3.2ms +/- 17.4%

  bitops:                29.8ms +/- 3.5%
    3bit-bits-in-byte:    2.4ms +/- 28.4%
    bits-in-byte:         6.4ms +/- 10.6%
    bitwise-and:          9.0ms +/- 0.0%
    nsieve-bits:         12.0ms +/- 0.0%

  controlflow:            2.6ms +/- 26.2%
    recursive:            2.6ms +/- 26.2%

  crypto:                23.4ms +/- 6.1%
    aes:                  7.6ms +/- 14.6%
    md5:                  8.2ms +/- 6.8%
    sha1:                 7.6ms +/- 9.0%

  date:                  64.8ms +/- 4.2%
    format-tofte:        26.2ms +/- 4.0%
    format-xparb:        38.6ms +/- 5.4%

  math:                  40.4ms +/- 6.0%
    cordic:              18.4ms +/- 10.2%
    partial-sums:        15.8ms +/- 10.3%
    spectral-norm:        6.2ms +/- 9.0%

  regexp:                11.4ms +/- 52.6%
    dna:                 11.4ms +/- 52.6%

  string:               127.8ms +/- 2.1%
    base64:              12.8ms +/- 4.3%
    fasta:               22.0ms +/- 4.0%
    tagcloud:            26.6ms +/- 4.2%
    unpack-code:         40.0ms +/- 2.2%
    validate-input:      26.4ms +/- 7.1%
```
Peacekeeper score is 3785.

Sigh, if only Chromium was a little more stable.
Yeah, Chromium is really fast but, as you said, unstable.

---

### Post by vishzilla on 2009-09-16
> **TheStroj said:**
> Yeah, Chromium is really fast but, as you said, unstable.

well that because its still alpha. got to give credit to Google!

**Chromium 4.0.212.0**

```
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  935.8ms +/- 3.6%
--------------------------------------------

  3d:                   146.0ms +/- 10.6%
    cube:                52.4ms +/- 30.4%
    morph:               45.8ms +/- 5.9%
    raytrace:            47.8ms +/- 7.2%

  access:                65.6ms +/- 3.2%
    binary-trees:         5.0ms +/- 30.5%
    fannkuch:            22.8ms +/- 7.1%
    nbody:               31.8ms +/- 8.0%
    nsieve:               6.0ms +/- 14.7%

  bitops:                62.4ms +/- 3.9%
    3bit-bits-in-byte:    4.6ms +/- 24.2%
    bits-in-byte:        13.0ms +/- 6.8%
    bitwise-and:         17.4ms +/- 8.1%
    nsieve-bits:         27.4ms +/- 5.2%

  controlflow:            4.8ms +/- 21.7%
    recursive:            4.8ms +/- 21.7%

  crypto:                56.2ms +/- 8.2%
    aes:                 19.4ms +/- 3.5%
    md5:                 18.6ms +/- 3.7%
    sha1:                18.2ms +/- 23.4%

  date:                 155.2ms +/- 10.0%
    format-tofte:        67.8ms +/- 5.1%
    format-xparb:        87.4ms +/- 15.7%

  math:                  98.6ms +/- 5.1%
    cordic:              33.2ms +/- 17.6%
    partial-sums:        46.6ms +/- 8.1%
    spectral-norm:       18.8ms +/- 16.5%

  regexp:                27.4ms +/- 6.9%
    dna:                 27.4ms +/- 6.9%

  string:               319.6ms +/- 7.7%
    base64:              29.0ms +/- 12.5%
    fasta:               47.8ms +/- 8.7%
    tagcloud:            70.0ms +/- 1.8%
    unpack-code:         95.2ms +/- 23.3%
    validate-input:      77.6ms +/- 25.0%
```

---

### Post by TheStroj on 2009-09-16
> **vishzilla said:**
> well that because its still alpha. got to give credit to Google!
Yes, thank you Google that Chromium is an Open Source project =D

---

### Post by Jesus_Valdez on 2009-09-16
Now with Swiftweasel 3.5.2

============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  **4179.4ms +/- 2.6%**
--------------------------------------------

  3d:                    466.4ms +/- 12.5%
    cube:                169.6ms +/- 26.7%
    morph:               148.2ms +/- 19.7%
    raytrace:            148.6ms +/- 26.3%

  access:                582.4ms +/- 14.5%
    binary-trees:         77.4ms +/- 30.4%
    fannkuch:            207.8ms +/- 14.6%
    nbody:               222.2ms +/- 20.8%
    nsieve:               75.0ms +/- 35.7%

  bitops:                494.6ms +/- 9.8%
    3bit-bits-in-byte:    80.4ms +/- 28.6%
    bits-in-byte:        103.2ms +/- 25.3%
    bitwise-and:         186.4ms +/- 12.5%
    nsieve-bits:         124.6ms +/- 19.9%

  controlflow:            57.6ms +/- 42.8%
    recursive:            57.6ms +/- 42.8%

  crypto:                255.4ms +/- 12.4%
    aes:                  97.8ms +/- 13.4%
    md5:                  93.2ms +/- 14.9%
    sha1:                 64.4ms +/- 31.8%

  date:                  337.0ms +/- 13.6%
    format-tofte:        161.2ms +/- 11.0%
    format-xparb:        175.8ms +/- 17.4%

  math:                  419.2ms +/- 8.2%
    cordic:              134.8ms +/- 24.1%
    partial-sums:        187.6ms +/- 11.3%
    spectral-norm:        96.8ms +/- 32.7%

  regexp:                425.2ms +/- 3.6%
    dna:                 425.2ms +/- 3.6%

  string:               1141.6ms +/- 8.5%
    base64:              100.0ms +/- 28.2%
    fasta:               204.6ms +/- 17.5%
    tagcloud:            246.2ms +/- 13.5%
    unpack-code:         390.6ms +/- 6.1%
    validate-input:      200.2ms +/- 21.2%

---

