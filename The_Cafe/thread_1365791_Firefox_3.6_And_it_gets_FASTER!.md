---
title: "Firefox 3.6: And it gets FASTER!"
date: 2009-12-27
forum: The Cafe
---

### Post by phrostbyte on 2009-12-27
Tests were done on a 64-bit version of Ubuntu 9.10 with minimal non-interactive processes.

[,%223d-morph%22:[85,85,85,85,85],%223d-raytrace%22:[75,76,75,76,75],%22access-binary-trees%22:[31,31,29,30,30],%22access-fannkuch%22:[162,162,162,163,167],%22access-nbody%22:[116,115,124,116,117],%22access-nsieve%22:[46,47,47,47,47],%22bitops-3bit-bits-in-byte%22:[35,35,35,35,35],%22bitops-bits-in-byte%22:[64,62,64,64,62],%22bitops-bitwise-and%22:[104,103,105,104,103],%22bitops-nsieve-bits%22:[77,77,78,77,73],%22controlflow-recursive%22:[30,29,29,28,28],%22crypto-aes%22:[49,48,49,49,49],%22crypto-md5%22:[38,37,38,37,39],%22crypto-sha1%22:[39,41,40,40,40],%22date-format-tofte%22:[59,59,58,58,59],%22date-format-xparb%22:[67,69,69,68,69],%22math-cordic%22:[100,99,98,98,100],%22math-partial-sums%22:[105,101,103,103,103],%22math-spectral-norm%22:[49,48,49,48,47],%22regexp-dna%22:[175,162,209,167,174],%22string-base64%22:[37,37,37,39,38],%22string-fasta%22:[110,109,113,111,113],%22string-tagcloud%22:[94,92,96,93,95],%22string-unpack-code%22:[119,132,125,145,141],%22string-validate-input%22:[54,54,53,55,55]}"]Firefox 3.5.6 Sunspider Results]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?{%223d-cube%22:[96,94,94,94,94) - 2030.4ms

[Firefox 3.6 Beta 5 Sunspider Results]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B39,42,40,41,40%5D,%223d-morph%22:%5B32,32,32,33,32%5D,%223d-raytrace%22:%5B55,54,57,55,57%5D,%22access-binary-trees%22:%5B37,38,38,38,37%5D,%22access-fannkuch%22:%5B97,96,96,97,96%5D,%22access-nbody%22:%5B29,31,30,30,35%5D,%22access-nsieve%22:%5B11,11,11,11,11%5D,%22bitops-3bit-bits-in-byte%22:%5B1,1,1,1,1%5D,%22bitops-bits-in-byte%22:%5B8,8,8,8,8%5D,%22bitops-bitwise-and%22:%5B1,2,2,2,2%5D,%22bitops-nsieve-bits%22:%5B23,23,23,22,22%5D,%22controlflow-recursive%22:%5B39,39,40,38,40%5D,%22crypto-aes%22:%5B29,29,30,31,29%5D,%22crypto-md5%22:%5B12,13,12,12,12%5D,%22crypto-sha1%22:%5B7,7,7,7,7%5D,%22date-format-tofte%22:%5B65,72,71,72,72%5D,%22date-format-xparb%22:%5B47,47,48,50,49%5D,%22math-cordic%22:%5B13,13,12,12,13%5D,%22math-partial-sums%22:%5B15,15,16,15,15%5D,%22math-spectral-norm%22:%5B6,5,6,5,5%5D,%22regexp-dna%22:%5B46,46,47,47,46%5D,%22string-base64%22:%5B11,10,11,11,10%5D,%22string-fasta%22:%5B63,63,66,66,67%5D,%22string-tagcloud%22:%5B74,76,83,85,84%5D,%22string-unpack-code%22:%5B84,86,84,82,82%5D,%22string-validate-input%22:%5B24,23,31,30,32%5D%7D") -  891.4ms

**Looks like Firefox 3.6 is ~2.25 times faster with JavaScript then Firefox 3.5!**

Explanation: TraceMonkey got a 64-bit just-in-time compiler in Firefox 3.6!

Compared to Chromium (latest build):
[chromium-browser 4.0.283.0~svn20091226r35283-0ubuntu1~ucd1~karmic Sunspider Results]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B21,26,24,23,24%5D,%223d-morph%22:%5B26,24,21,22,21%5D,%223d-raytrace%22:%5B19,17,18,17,17%5D,%22access-binary-trees%22:%5B2,1,1,2,1%5D,%22access-fannkuch%22:%5B13,12,12,12,12%5D,%22access-nbody%22:%5B19,18,18,19,19%5D,%22access-nsieve%22:%5B4,4,4,4,4%5D,%22bitops-3bit-bits-in-byte%22:%5B3,3,3,3,3%5D,%22bitops-bits-in-byte%22:%5B7,7,7,7,7%5D,%22bitops-bitwise-and%22:%5B9,35,9,9,9%5D,%22bitops-nsieve-bits%22:%5B7,8,7,8,8%5D,%22controlflow-recursive%22:%5B3,2,3,2,2%5D,%22crypto-aes%22:%5B9,9,8,8,9%5D,%22crypto-md5%22:%5B4,4,4,4,4%5D,%22crypto-sha1%22:%5B3,3,3,4,3%5D,%22date-format-tofte%22:%5B22,21,21,21,20%5D,%22date-format-xparb%22:%5B29,29,29,29,28%5D,%22math-cordic%22:%5B17,16,16,15,15%5D,%22math-partial-sums%22:%5B18,18,18,18,18%5D,%22math-spectral-norm%22:%5B10,10,9,9,9%5D,%22regexp-dna%22:%5B10,10,9,10,10%5D,%22string-base64%22:%5B11,12,11,12,12%5D,%22string-fasta%22:%5B16,17,17,16,16%5D,%22string-tagcloud%22:%5B27,26,26,26,26%5D,%22string-unpack-code%22:%5B40,38,38,40,38%5D,%22string-validate-input%22:%5B23,23,23,22,23%5D%7D") - 368.8ms

Chromium is still the king of JS performance on Ubuntu. :)

Another interesting comparison:

[Firefox 3.5.6 (32-bit) running on Wine]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B32,32,33,34,33%5D,%223d-morph%22:%5B45,52,46,46,46%5D,%223d-raytrace%22:%5B55,53,54,55,54%5D,%22access-binary-trees%22:%5B34,34,34,32,33%5D,%22access-fannkuch%22:%5B55,56,55,56,58%5D,%22access-nbody%22:%5B24,23,23,24,22%5D,%22access-nsieve%22:%5B10,10,10,10,10%5D,%22bitops-3bit-bits-in-byte%22:%5B1,1,1,1,1%5D,%22bitops-bits-in-byte%22:%5B8,7,7,7,7%5D,%22bitops-bitwise-and%22:%5B2,2,2,1,2%5D,%22bitops-nsieve-bits%22:%5B20,20,20,19,20%5D,%22controlflow-recursive%22:%5B35,35,34,35,35%5D,%22crypto-aes%22:%5B25,25,24,24,26%5D,%22crypto-md5%22:%5B12,12,12,12,12%5D,%22crypto-sha1%22:%5B7,7,7,7,7%5D,%22date-format-tofte%22:%5B69,71,68,67,70%5D,%22date-format-xparb%22:%5B83,82,86,86,84%5D,%22math-cordic%22:%5B28,27,29,29,28%5D,%22math-partial-sums%22:%5B12,12,12,12,12%5D,%22math-spectral-norm%22:%5B6,6,6,6,6%5D,%22regexp-dna%22:%5B63,61,67,67,48%5D,%22string-base64%22:%5B13,13,14,13,14%5D,%22string-fasta%22:%5B57,58,58,58,56%5D,%22string-tagcloud%22:%5B67,63,64,68,64%5D,%22string-unpack-code%22:%5B89,92,91,89,91%5D,%22string-validate-input%22:%5B27,30,31,27,27%5D%7D") - 880.4ms
[Firefox 3.6 Beta 5 (32-bit) running on Wine]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B29,28,28,28,32%5D,%223d-morph%22:%5B50,39,41,42,41%5D,%223d-raytrace%22:%5B44,46,46,46,47%5D,%22access-binary-trees%22:%5B33,31,33,32,33%5D,%22access-fannkuch%22:%5B61,82,63,62,61%5D,%22access-nbody%22:%5B22,21,22,21,22%5D,%22access-nsieve%22:%5B9,9,9,8,9%5D,%22bitops-3bit-bits-in-byte%22:%5B1,1,1,1,1%5D,%22bitops-bits-in-byte%22:%5B8,8,8,8,8%5D,%22bitops-bitwise-and%22:%5B2,1,1,2,2%5D,%22bitops-nsieve-bits%22:%5B18,18,18,18,18%5D,%22controlflow-recursive%22:%5B37,36,37,36,37%5D,%22crypto-aes%22:%5B23,24,24,24,23%5D,%22crypto-md5%22:%5B9,9,9,10,10%5D,%22crypto-sha1%22:%5B5,6,5,6,5%5D,%22date-format-tofte%22:%5B58,62,63,62,61%5D,%22date-format-xparb%22:%5B72,73,74,73,73%5D,%22math-cordic%22:%5B25,27,26,25,27%5D,%22math-partial-sums%22:%5B12,12,12,12,12%5D,%22math-spectral-norm%22:%5B5,5,5,6,5%5D,%22regexp-dna%22:%5B46,45,44,45,45%5D,%22string-base64%22:%5B9,8,9,9,9%5D,%22string-fasta%22:%5B40,43,43,46,45%5D,%22string-tagcloud%22:%5B54,59,58,64,62%5D,%22string-unpack-code%22:%5B59,60,61,61,62%5D,%22string-validate-input%22:%5B21,21,22,33,27%5D%7D") - 769.0ms

Looks like the Windows version (Firefox 3.5) beats the Linux version by a large amount! Firefox 3.6 is less of difference, but it still beats the Linux version. I couldn't test it with a 64-bit build, only 32-bit version is available. One explanation is the 32-bit version of Firefox is more optimised (ie, the JIT'er).

Here is a nice chart (X axis is "Execution time in milliseconds"):

[IMG]http://img130.imageshack.us/img130/3063/jsperf.png[/IMG]

Another benchmark: [IE 8 on Windows 7]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B160,170,160,170,160%5D,%223d-morph%22:%5B150,160,150,150,150%5D,%223d-raytrace%22:%5B190,190,190,200,190%5D,%22access-binary-trees%22:%5B120,120,130,120,130%5D,%22access-fannkuch%22:%5B319,329,325,315,320%5D,%22access-nbody%22:%5B200,200,190,200,200%5D,%22access-nsieve%22:%5B100,110,110,100,100%5D,%22bitops-3bit-bits-in-byte%22:%5B90,90,90,90,90%5D,%22bitops-bits-in-byte%22:%5B90,100,100,90,100%5D,%22bitops-bitwise-and%22:%5B235,236,251,250,253%5D,%22bitops-nsieve-bits%22:%5B160,150,160,160,160%5D,%22controlflow-recursive%22:%5B100,100,110,100,100%5D,%22crypto-aes%22:%5B130,130,130,130,120%5D,%22crypto-md5%22:%5B90,80,80,80,80%5D,%22crypto-sha1%22:%5B80,80,80,80,80%5D,%22date-format-tofte%22:%5B170,170,160,170,170%5D,%22date-format-xparb%22:%5B160,160,150,160,160%5D,%22math-cordic%22:%5B180,190,190,200,190%5D,%22math-partial-sums%22:%5B140,130,140,140,140%5D,%22math-spectral-norm%22:%5B130,130,130,130,130%5D,%22regexp-dna%22:%5B166,170,162,173,170%5D,%22string-base64%22:%5B130,120,120,125,120%5D,%22string-fasta%22:%5B200,210,196,200,210%5D,%22string-tagcloud%22:%5B150,150,150,140,150%5D,%22string-unpack-code%22:%5B130,130,130,130,130%5D,%22string-validate-input%22:%5B130,130,130,130,130%5D%7D") - 3923.0ms  (Just to put things in perspective) :)

Now onto Peacekeeper. Peacekeeper is a benchmark that tests a number of different things, including JavaScript performance, DOM performance, and rendering.

Here is the Peacekeeper results (Ubuntu 64-bit) - Compiz is enabled:
[IMG]http://img69.imageshack.us/img69/2947/firefox36b5.png[/IMG]
[IMG]http://img515.imageshack.us/img515/313/firefox356.png[/IMG]

Here is Peacekeeper result on Windows 7 (64-bit) - Aero is enabled:
[IMG]http://img39.imageshack.us/img39/8563/firefoxwin.png[/IMG]

Firefox 3.6 has also improved in this benchmark, but it's not as drastic (most of 3.6's improvements are to it's JS engine). This is a benchmark where Linux totally defeats Windows, especially in rendering. Seem's Xorg's hardware acceleration is destroying Windows's lack thereof.

---

### Post by pwnst*r on 2009-12-27
[,%223d-morph%22:[24,22,23,22,22],%223d-raytrace%22:[20,19,19,19,19],%22access-binary-trees%22:[1,2,2,2,1],%22access-fannkuch%22:[12,12,12,14,12],%22access-nbody%22:[17,15,15,15,15],%22access-nsieve%22:[3,3,4,4,4],%22bitops-3bit-bits-in-byte%22:[2,2,3,3,3],%22bitops-bits-in-byte%22:[7,7,7,7,7],%22bitops-bitwise-and%22:[8,12,11,8,7],%22bitops-nsieve-bits%22:[13,13,13,13,13],%22controlflow-recursive%22:[2,2,2,2,3],%22crypto-aes%22:[8,7,8,8,8],%22crypto-md5%22:[9,9,9,9,9],%22crypto-sha1%22:[8,8,9,9,8],%22date-format-tofte%22:[26,25,25,25,24],%22date-format-xparb%22:[24,25,24,25,25],%22math-cordic%22:[14,15,14,15,15],%22math-partial-sums%22:[22,19,18,18,22],%22math-spectral-norm%22:[6,6,6,7,6],%22regexp-dna%22:[15,14,15,15,16],%22string-base64%22:[17,16,16,16,17],%22string-fasta%22:[23,22,23,22,23],%22string-tagcloud%22:[33,33,33,32,33],%22string-unpack-code%22:[49,48,50,49,50],%22string-validate-input%22:[25,24,24,25,25]}"][COLOR="DarkOrange"]Chrome 4.0.249.43[/COLOR]]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?{%223d-cube%22:[20,22,21,22,22)

406.2 ms with 10 tabs open (dunno if any of that makes a difference) 

*edit* make that thirteen tabs.  i have 3 tabs that are incognito so i can have my other gmail address open.

---

### Post by gnuvistawouldbecool on 2009-12-27
Well, since this will be rather dependant on hardware, this probably means little, not knowing what you were running, but using:
 20091226 Minefield/3.7a1pre, on a AMD Athlon 64 3000, 2.0GHz, 512MB DDR computer,

[1661.0ms]("http://http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B80,80,83,79,79%5D,%223d-morph%22:%5B52,53,54,50,52%5D,%223d-raytrace%22:%5B92,95,92,91,91%5D,%22access-binary-trees%22:%5B38,37,35,37,40%5D,%22access-fannkuch%22:%5B121,120,121,119,120%5D,%22access-nbody%22:%5B48,49,49,42,42%5D,%22access-nsieve%22:%5B22,22,23,23,21%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,1,1%5D,%22bitops-bits-in-byte%22:%5B12,12,12,12,12%5D,%22bitops-bitwise-and%22:%5B4,3,3,4,4%5D,%22bitops-nsieve-bits%22:%5B37,38,53,38,35%5D,%22controlflow-recursive%22:%5B9,9,822,9,10%5D,%22crypto-aes%22:%5B50,50,52,51,53%5D,%22crypto-md5%22:%5B21,21,22,22,21%5D,%22crypto-sha1%22:%5B12,11,12,11,11%5D,%22date-format-tofte%22:%5B121,120,119,120,121%5D,%22date-format-xparb%22:%5B84,86,82,84,82%5D,%22math-cordic%22:%5B26,29,25,25,24%5D,%22math-partial-sums%22:%5B42,28,31,27,28%5D,%22math-spectral-norm%22:%5B12,10,12,11,12%5D,%22regexp-dna%22:%5B116,110,108,107,106%5D,%22string-base64%22:%5B19,19,20,19,19%5D,%22string-fasta%22:%5B128,126,129,128,128%5D,%22string-tagcloud%22:%5B182,176,186,173,162%5D,%22string-unpack-code%22:%5B127,141,131,136,130%5D,%22string-validate-input%22:%5B55,84,59,53,51%5D%7D")

---

### Post by pwnst*r on 2009-12-27
[,%223d-morph%22:[42,41,41,41,41],%223d-raytrace%22:[61,60,61,60,61],%22access-binary-trees%22:[33,32,33,32,33],%22access-fannkuch%22:[53,52,54,53,54],%22access-nbody%22:[23,20,21,20,20],%22access-nsieve%22:[11,12,10,10,10],%22bitops-3bit-bits-in-byte%22:[1,1,1,1,1],%22bitops-bits-in-byte%22:[7,7,7,7,7],%22bitops-bitwise-and%22:[2,2,2,2,3],%22bitops-nsieve-bits%22:[21,21,21,22,21],%22controlflow-recursive%22:[33,33,33,33,33],%22crypto-aes%22:[27,30,28,28,27],%22crypto-md5%22:[13,13,13,14,14],%22crypto-sha1%22:[7,7,8,7,7],%22date-format-tofte%22:[84,81,82,81,81],%22date-format-xparb%22:[78,76,77,77,77],%22math-cordic%22:[24,24,24,24,25],%22math-partial-sums%22:[13,12,13,12,13],%22math-spectral-norm%22:[6,5,5,5,5],%22regexp-dna%22:[55,52,49,50,50],%22string-base64%22:[14,14,14,13,14],%22string-fasta%22:[64,65,64,65,64],%22string-tagcloud%22:[76,74,71,73,72],%22string-unpack-code%22:[110,111,112,112,112],%22string-validate-input%22:[29,30,29,29,29]}"][COLOR="DarkOrange"]Firefox 3.5.6[/COLOR]]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?{%223d-cube%22:[36,36,37,37,37)

912.6 ms one tab open

---

### Post by phrostbyte on 2009-12-27
> **gnuvistawouldbecool said:**
> Well, since this will be rather dependant on hardware, this probably means little, not knowing what you were running, but using:
 20091226 Minefield/3.7a1pre, on a AMD Athlon 64 3000, 2.0GHz, 512MB DDR computer,

[1661.0ms]("http://http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B80,80,83,79,79%5D,%223d-morph%22:%5B52,53,54,50,52%5D,%223d-raytrace%22:%5B92,95,92,91,91%5D,%22access-binary-trees%22:%5B38,37,35,37,40%5D,%22access-fannkuch%22:%5B121,120,121,119,120%5D,%22access-nbody%22:%5B48,49,49,42,42%5D,%22access-nsieve%22:%5B22,22,23,23,21%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,1,1%5D,%22bitops-bits-in-byte%22:%5B12,12,12,12,12%5D,%22bitops-bitwise-and%22:%5B4,3,3,4,4%5D,%22bitops-nsieve-bits%22:%5B37,38,53,38,35%5D,%22controlflow-recursive%22:%5B9,9,822,9,10%5D,%22crypto-aes%22:%5B50,50,52,51,53%5D,%22crypto-md5%22:%5B21,21,22,22,21%5D,%22crypto-sha1%22:%5B12,11,12,11,11%5D,%22date-format-tofte%22:%5B121,120,119,120,121%5D,%22date-format-xparb%22:%5B84,86,82,84,82%5D,%22math-cordic%22:%5B26,29,25,25,24%5D,%22math-partial-sums%22:%5B42,28,31,27,28%5D,%22math-spectral-norm%22:%5B12,10,12,11,12%5D,%22regexp-dna%22:%5B116,110,108,107,106%5D,%22string-base64%22:%5B19,19,20,19,19%5D,%22string-fasta%22:%5B128,126,129,128,128%5D,%22string-tagcloud%22:%5B182,176,186,173,162%5D,%22string-unpack-code%22:%5B127,141,131,136,130%5D,%22string-validate-input%22:%5B55,84,59,53,51%5D%7D")

Run a test on same hardware with Firefox 3.5.6

---

### Post by phrostbyte on 2009-12-27
dbl post

---

### Post by pwnst*r on 2009-12-27
lol

---

### Post by Pogeymanz on 2009-12-27
Firefox 3.6Beta5:
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 1323.2ms +/- 2.9%
--------------------------------------------

  3d:                   192.6ms +/- 2.5%
    cube:                62.6ms +/- 5.0%
    morph:               39.4ms +/- 1.7%
    raytrace:            90.6ms +/- 2.5%

  access:               152.4ms +/- 3.6%
    binary-trees:        46.2ms +/- 1.2%
    fannkuch:            60.4ms +/- 3.1%
    nbody:               28.0ms +/- 17.5%
    nsieve:              17.8ms +/- 5.8%

  bitops:                42.2ms +/- 2.5%
    3bit-bits-in-byte:    1.8ms +/- 30.9%
    bits-in-byte:        12.6ms +/- 5.4%
    bitwise-and:          3.0ms +/- 0.0%
    nsieve-bits:         24.8ms +/- 4.2%

  controlflow:           40.0ms +/- 2.2%
    recursive:           40.0ms +/- 2.2%

  crypto:                67.2ms +/- 5.8%
    aes:                 39.0ms +/- 9.8%
    md5:                 18.4ms +/- 3.7%
    sha1:                 9.8ms +/- 13.9%

  date:                 202.4ms +/- 2.1%
    format-tofte:       126.6ms +/- 2.7%
    format-xparb:        75.8ms +/- 4.8%

  math:                  51.0ms +/- 19.3%
    cordic:              16.8ms +/- 6.2%
    partial-sums:        25.8ms +/- 40.9%
    spectral-norm:        8.4ms +/- 8.1%

  regexp:               104.0ms +/- 4.5%
    dna:                104.0ms +/- 4.5%

  string:               471.4ms +/- 5.4%
    base64:              11.4ms +/- 6.0%
    fasta:               79.0ms +/- 2.2%
    tagcloud:           133.6ms +/- 7.3%
    unpack-code:        207.2ms +/- 9.1%
    validate-input:      40.2ms +/- 10.4%


Firefox3.7Alpha1:
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 1352.8ms +/- 14.6%
--------------------------------------------

  3d:                   198.4ms +/- 3.5%
    cube:                64.4ms +/- 1.7%
    morph:               42.2ms +/- 2.5%
    raytrace:            91.8ms +/- 6.9%

  access:               137.0ms +/- 2.1%
    binary-trees:        28.8ms +/- 4.7%
    fannkuch:            65.4ms +/- 1.0%
    nbody:               26.6ms +/- 6.3%
    nsieve:              16.2ms +/- 3.4%

  bitops:                43.2ms +/- 2.4%
    3bit-bits-in-byte:    1.6ms +/- 42.6%
    bits-in-byte:        12.4ms +/- 5.5%
    bitwise-and:          2.2ms +/- 25.3%
    nsieve-bits:         27.0ms +/- 3.3%

  controlflow:          122.2ms +/- 166.6%
    recursive:          122.2ms +/- 166.6%

  crypto:                68.4ms +/- 1.0%
    aes:                 40.0ms +/- 5.8%
    md5:                 18.4ms +/- 3.7%
    sha1:                10.0ms +/- 21.5%

  date:                 182.4ms +/- 0.8%
    format-tofte:       105.2ms +/- 1.3%
    format-xparb:        77.2ms +/- 1.8%

  math:                  53.2ms +/- 2.0%
    cordic:              22.6ms +/- 3.0%
    partial-sums:        22.0ms +/- 4.0%
    spectral-norm:        8.6ms +/- 7.9%

  regexp:               104.6ms +/- 7.7%
    dna:                104.6ms +/- 7.7%

  string:               443.4ms +/- 4.2%
    base64:              11.4ms +/- 6.0%
    fasta:               79.4ms +/- 2.1%
    tagcloud:           127.4ms +/- 2.5%
    unpack-code:        185.0ms +/- 12.5%
    validate-input:      40.2ms +/- 12.3%


So far the alpha is doing a little worse on my machine. Oh well. I don't have FF3.5 installed at all, so I can't compare that.

---

### Post by phrostbyte on 2009-12-27
> **Pogeymanz said:**
> Firefox 3.6Beta5:
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 1323.2ms +/- 2.9%
--------------------------------------------

  3d:                   192.6ms +/- 2.5%
    cube:                62.6ms +/- 5.0%
    morph:               39.4ms +/- 1.7%
    raytrace:            90.6ms +/- 2.5%

  access:               152.4ms +/- 3.6%
    binary-trees:        46.2ms +/- 1.2%
    fannkuch:            60.4ms +/- 3.1%
    nbody:               28.0ms +/- 17.5%
    nsieve:              17.8ms +/- 5.8%

  bitops:                42.2ms +/- 2.5%
    3bit-bits-in-byte:    1.8ms +/- 30.9%
    bits-in-byte:        12.6ms +/- 5.4%
    bitwise-and:          3.0ms +/- 0.0%
    nsieve-bits:         24.8ms +/- 4.2%

  controlflow:           40.0ms +/- 2.2%
    recursive:           40.0ms +/- 2.2%

  crypto:                67.2ms +/- 5.8%
    aes:                 39.0ms +/- 9.8%
    md5:                 18.4ms +/- 3.7%
    sha1:                 9.8ms +/- 13.9%

  date:                 202.4ms +/- 2.1%
    format-tofte:       126.6ms +/- 2.7%
    format-xparb:        75.8ms +/- 4.8%

  math:                  51.0ms +/- 19.3%
    cordic:              16.8ms +/- 6.2%
    partial-sums:        25.8ms +/- 40.9%
    spectral-norm:        8.4ms +/- 8.1%

  regexp:               104.0ms +/- 4.5%
    dna:                104.0ms +/- 4.5%

  string:               471.4ms +/- 5.4%
    base64:              11.4ms +/- 6.0%
    fasta:               79.0ms +/- 2.2%
    tagcloud:           133.6ms +/- 7.3%
    unpack-code:        207.2ms +/- 9.1%
    validate-input:      40.2ms +/- 10.4%


Firefox3.7Alpha1:
============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                 1352.8ms +/- 14.6%
--------------------------------------------

  3d:                   198.4ms +/- 3.5%
    cube:                64.4ms +/- 1.7%
    morph:               42.2ms +/- 2.5%
    raytrace:            91.8ms +/- 6.9%

  access:               137.0ms +/- 2.1%
    binary-trees:        28.8ms +/- 4.7%
    fannkuch:            65.4ms +/- 1.0%
    nbody:               26.6ms +/- 6.3%
    nsieve:              16.2ms +/- 3.4%

  bitops:                43.2ms +/- 2.4%
    3bit-bits-in-byte:    1.6ms +/- 42.6%
    bits-in-byte:        12.4ms +/- 5.5%
    bitwise-and:          2.2ms +/- 25.3%
    nsieve-bits:         27.0ms +/- 3.3%

  controlflow:          122.2ms +/- 166.6%
    recursive:          122.2ms +/- 166.6%

  crypto:                68.4ms +/- 1.0%
    aes:                 40.0ms +/- 5.8%
    md5:                 18.4ms +/- 3.7%
    sha1:                10.0ms +/- 21.5%

  date:                 182.4ms +/- 0.8%
    format-tofte:       105.2ms +/- 1.3%
    format-xparb:        77.2ms +/- 1.8%

  math:                  53.2ms +/- 2.0%
    cordic:              22.6ms +/- 3.0%
    partial-sums:        22.0ms +/- 4.0%
    spectral-norm:        8.6ms +/- 7.9%

  regexp:               104.6ms +/- 7.7%
    dna:                104.6ms +/- 7.7%

  string:               443.4ms +/- 4.2%
    base64:              11.4ms +/- 6.0%
    fasta:               79.4ms +/- 2.1%
    tagcloud:           127.4ms +/- 2.5%
    unpack-code:        185.0ms +/- 12.5%
    validate-input:      40.2ms +/- 12.3%


So far the alpha is doing a little worse on my machine. Oh well. I don't have FF3.5 installed at all, so I can't compare that.

I'm surprised the alpha is doing so well, I would assume they built it with debug symbols.

---

### Post by crimesaucer on 2009-12-27
Yeah, I've been using the TraceMonkey for 64-bit patch for the last couple of months now, I think it gives me issues on certain flash sites, like pages like this: [http://www.surfline.com/surf-news/gift-wrapped_39664/1/](http://www.surfline.com/surf-news/gift-wrapped_39664/1/)



Before the patch, my version of Firefox 3.5 had a score of about 4800 for the sunspider benchmarks, and the first versions of 3.6b1 and 3.6b2 (without the patch) were around 4400.



Then when the "TraceMonkey for 64-bit" patch came out it dropped my results down to 1660 - 1600 for versions 3.6b2, 3.63, and 3.6b4.



When building Firefox 3.7a1pre (with native TraceMonkey 64-bit included and no patch needed) my score dropped down to around 1400.



Sadly, I've tested every version number that I've built for Linux64, and I've compared them all to the windows versions on my Vista64 partition, and the windows versions are always faster. The 32-bit windows version (on my Vista64) of 3.7a1pre has a score near 1200.



Another nice thing about the newer versions of Firefox is that they have the PGO working better.

---

### Post by phrostbyte on 2009-12-27
> **crimesaucer said:**
> Yeah, I've been using the TraceMonkey for 64-bit patch for the last couple of months now, I think it gives me issues on certain flash sites, like pages like this: [http://www.surfline.com/surf-news/gift-wrapped_39664/1/](http://www.surfline.com/surf-news/gift-wrapped_39664/1/)



Before the patch, my version of Firefox 3.5 had a score of about 4800 for the sunspider benchmarks, and the first versions of 3.6b1 and 3.6b2 (without the patch) were around 4400.



Then when the "TraceMonkey for 64-bit" patch came out it dropped my results down to 1660 - 1600 for versions 3.6b2, 3.63, and 3.6b4.



When building Firefox 3.7a1pre (with native TraceMonkey 64-bit included and no patch needed) my score dropped down to around 1400.



Sadly, I've tested every version number that I've built for Linux64, and I've compared them all to the windows versions on my Vista64 partition, and the windows versions are always faster. The 32-bit windows version (on my Vista64) of 3.7a1pre has a score near 1200.



Another nice thing about the newer versions of Firefox is that they have the PGO working better.

The official Firefox for Windows is 32-bit (even on Vista64). I can't find any working 64-bits of Firefox for Windows. The ones here will not execute on Wine: [http://wiki.mozilla-x86-64.com/Firefox:Download](http://wiki.mozilla-x86-64.com/Firefox:Download). Plus I wouldn't recommend downloading random executables of the Internet on Windows, as they may contain viruses.

Please report any bugs you have with 64-bit TraceMonkey to Mozilla. :)

---

### Post by crimesaucer on 2009-12-27
> **phrostbyte said:**
> The official Firefox for Windows is 32-bit (even on Vista64). I can't find any working 64-bits of Firefox for Windows. The ones here will not execute on Wine: [http://wiki.mozilla-x86-64.com/Firefox:Download](http://wiki.mozilla-x86-64.com/Firefox:Download). Plus I wouldn't recommend downloading random executables of the Internet on Windows, as they may contain viruses.

Please report any bugs you have with 64-bit TraceMonkey to Mozilla. :)

Yeah I knew that, it's really too bad that they only have 32-bit windows builds and 32-bit adobe flash for windows (not that I even use my windows partition that often).


As for wine and viruses there's no worry for me. I don't even use wine, and if I did I would never try downloading random windows programs. 


I prefer to keep a dual partition around instead of installing wine, that way I can log into my Vista64 if I need to use Windows for something (which is never).


I've posted comments on the Bugzilla page for Linux PGO, and was one of the first people to ask for 64-bit TraceMonkey on linux way back when 3.5's TraceMonkey first became available.

---

### Post by phrostbyte on 2009-12-28
> **crimesaucer said:**
> Yeah I knew that, it's really too bad that they only have 32-bit windows builds and 32-bit adobe flash for windows (not that I even use my windows partition that often).


As for wine and viruses there's no worry for me. I don't even use wine, and if I did I would never try downloading random windows programs. 


I prefer to keep a dual partition around instead of installing wine, that way I can log into my Vista64 if I need to use Windows for something (which is never).


I've posted comments on the Bugzilla page for Linux PGO, and was one of the first people to ask for 64-bit TraceMonkey on linux way back when 3.5's TraceMonkey first became available.

I'm sure there is little optimisations they can do here and there on TraceMonkey, but nothing matches the 64-bit JITer ATM. This change will cause noticeable performance gains in web apps for Ubuntu users. I just want to make sure there is no regressions.

Viruses are not a worry for me because I nuke my Wine directory regularly. :)

---

### Post by phrostbyte on 2009-12-28
I'll look into running a benchmark which tests rendering (ie. Peacekeeper) since rendering tends to be important too. :) I am worried about rendering being GPU / driver variant though, so it's not as easy to get a clear picture of browser/OS performance.

---

### Post by Xbehave on 2009-12-28
[for 64bit users]("ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.6.x/")

What is the real world difference in these? I noticed 2.0->3.0 a lot and 3.0->3.5, and i consider sunspidder one of the better benchmarks but think that 
[v8]("http://v8.googlecode.com/svn/data/benchmarks/v5/run.html") (highly used js from real sites as a basis)
[dromea]("http://dromaeo.com/") (more stuff including css stuff)
are probably worth a look at too (i got the links from [here](http://www.whatbrowser.org/en-gb/more/) which is probably a useful link to send to friends/family

> 'll look into running a benchmark which tests rendering (ie. Peacekeeper) since rendering tends to be important too. I am worried about rendering being GPU / driver variant though, so it's not as easy to get a clear picture of browser/OS performance.
I have to say i think that peacekeeper sucks, it does some very advanced stuff which you will never see on real websites, for renderings speed there must be a better choice. Also i think render speed is pretty good now so it's only JS speed that really matters, because a plain site will render almost instantly on any browser, but the JS is orders of magnitude slower, i.e a 10ms vs 15ms is a pointless comparison when the page will take seconds to the javascript.

As for talk about 3.7, wont that generally be slower than 3.6 until 3.6 starts feature freezing and changes are sent up the line to 3.7?

---

### Post by phrostbyte on 2009-12-28
> **Xbehave said:**
> [for 64bit users]("ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.6.x/")

What is the real world difference in these? I noticed 2.0->3.0 a lot and 3.0->3.5, and i consider sunspidder one of the better benchmarks but think that 
[v8]("http://v8.googlecode.com/svn/data/benchmarks/v5/run.html") (highly used js from real sites as a basis)
[dromea]("http://dromaeo.com/") (more stuff including css stuff)
are probably worth a look at too (i got the links from [here](http://www.whatbrowser.org/en-gb/more/) which is probably a useful link to send to friends/family


I have to say i think that peacekeeper sucks, it does some very advanced stuff which you will never see on real websites, for renderings speed there must be a better choice. Also i think render speed is pretty good now so it's only JS speed that really matters, because a plain site will render almost instantly on any browser, but the JS is orders of magnitude slower, i.e a 10ms vs 15ms is a pointless comparison when the page will take seconds to the javascript.

As for talk about 3.7, wont that generally be slower than 3.6 until 3.6 starts feature freezing and changes are sent up the line to 3.7?

I just did Peacekeeper test (with Firefox 3.5.6 only) because it tests rendering, which is important part of a webbrowser (imo). I tested on Ubuntu 9.10 and Windows 7.

And you know what? Ubuntu actually beat Windows 7. I am surprised myself, because with all the crap people talk about X.org surely Ubuntu would lose. But even without a JITer, Ubuntu still beat Windows 7. :) Maybe X.org is not as bad as people make it out to be.

I will post results tommorow. :)

---

### Post by phrostbyte on 2009-12-28
> **Xbehave said:**
> [for 64bit users]("ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.6.x/")

What is the real world difference in these? I noticed 2.0->3.0 a lot and 3.0->3.5, and i consider sunspidder one of the better benchmarks but think that 
[v8]("http://v8.googlecode.com/svn/data/benchmarks/v5/run.html") (highly used js from real sites as a basis)
[dromea]("http://dromaeo.com/") (more stuff including css stuff)
are probably worth a look at too (i got the links from [here](http://www.whatbrowser.org/en-gb/more/) which is probably a useful link to send to friends/family


I have to say i think that peacekeeper sucks, it does some very advanced stuff which you will never see on real websites, for renderings speed there must be a better choice. Also i think render speed is pretty good now so it's only JS speed that really matters, because a plain site will render almost instantly on any browser, but the JS is orders of magnitude slower, i.e a 10ms vs 15ms is a pointless comparison when the page will take seconds to the javascript.

As for talk about 3.7, wont that generally be slower than 3.6 until 3.6 starts feature freezing and changes are sent up the line to 3.7?

It's quite noticeable on JS heavy apps, like Google Maps or Mail. It's amazing they are pushing this dynamically typed uncompilable language to pretty extreme limits. JavaScript TraceMonkey OR V8 is already a hell of lot of faster then CPython/Perl/PHP/Ruby. From a CS perspective, I don't think there is anything stopping a dynamic language like JavaScript or Python from literally being as fast as C code (at least after the parsing step, a one time deal). It's just our compilers aren't advanced enough yet, but who knows 10 years from now. I mean look at V8, it just keeps getting faster and faster. No end in sight. :)

---

### Post by Xbehave on 2009-12-28
> **phrostbyte said:**
> I just did Peacekeeper test (with Firefox 3.5.6 only) because it tests rendering
I'm not convinced it does so in a meaningful way, but then again i can't point you to one that does. I think the reason that the good benchmarks don't do rendering is because it depends much more on not the browser (graphics drivers, windows system, operating system, etc) than it does on the browser. For a thorough benchmark I'd go with dromeo which does all of v8+sunspider+some more however on my rather ancient laptop it said it would take 30m (if you have newer hardware it's probably worth using though)

> which is important part of a webbrowser (imo).
Imo timing rendering speed is like measuring the time it takes you to open a car door, before a race.

> And you know what? Ubuntu actually beat Windows 7. I am surprised myself, because with all the crap people talk about X.org surely Ubuntu would lose.
Crap people talk about xorg is mostly crap, a large part of the reason linux versions of firefox are slower is PGO (windows builds have it linux ones don't). If you want to do a complete comparison you should probably include swiftweasle on linux as that is firefox+PGO for linux.

note: Wayland (an alternative to xorg) will be runnable on a standard 2.6.33 kernel, so we are likely to see a lot more xorg crap in the near future (as there is some validity to some of the complaints)

I'm running 3.6 atm think the change is less than that of 3.0->3.5, I mean all progress is good but there I probably won't be use 3.6 as my main browser like I did 3.0 and 3.5. That said while typing this, it has seamed more responsive, and i've had no input lag, which i get with 3.5 (otoh 3.6 is on a ramdisk so may have an unfair advantage.

> From a CS perspective, I don't think there is anything stopping a dynamic language like JavaScript or Python from literally being as fast as C code (at least after the parsing step, a one time deal). 
You need to "compile" JavaScript everytime you load a page, so while JS may look good under certain loads (places where you compile once then run a loop lots of times), it can't compete with large codebases where you only run each path a few times, imagine if you had to compile the kernel as you booted it (lots of fast probing goes on, but you only run a probe once). Basically if JS/Python is so good V8/cpython would be written in JS/Python not c++/c.

---

### Post by Colonel Kilkenny on 2009-12-28
> **Xbehave said:**
> I'm not convinced it does so in a meaningful way, but then again i can't point you to one that does. I think the reason that the good benchmarks don't do rendering is because it depends much more on not the browser (graphics drivers, windows system, operating system, etc) than it does on the browser. For a thorough benchmark I'd go with dromeo which does all of v8+sunspider+some more however on my rather ancient laptop it said it would take 30m (if you have newer hardware it's probably worth using though)

Imo timing rendering speed is like measuring the time it takes you to open a car door, before a race.

Imho, rendering is just as important as JS speed. Rendering is not just about drawing something to your screen. It's about drawing stuff to your screen, it's about restyling stuff on your screen, it's about repainting stuff, it's about reflows/relayouts, it's about DOM speed. Reflows etc. are huge part of the overall user experience. You can create your dynamic and sexy UIs, but they still suck big time if rendering is lousy. Because very often JS is used to make pages more interactive and dynamic (elements moving/resizing without reloads, + all sorts of UI/usability bling) and all those actions like resizing elements are all about the rendering speed.

Edit.
Also, I'm not saying that SunSpider & V8 are not good benchmarks or that WebKit (or JavascriptCore/V8 ) is slow, but those two tests... they're both made by the mysterious "WebKit people", so it's not a huge surprise that WebKit (and especially Chromium) browsers are so good in SunSpider or V8. 
Without any proof/experience one could also guess that in Dromaeo Firefox is probably relatively quicker when compared to other tests. And Surprise surprise, Dromaeo is made by Mozilla (excluding the V8/SunSpider parts)).

So "lies, big lies, statistics" is quite good phrase to remember.

---

### Post by HappinessNow on 2009-12-28
> **phrostbyte said:**
> Tests were done on a 64-bit version of Ubuntu 9.10 with minimal non-interactive processes.

Firefox 3.5.6 Sunspider Results - 2030.4ms

Firefox 3.6 Beta 5 Sunspider Results -  891.4ms

**Looks like Firefox 3.6 is ~2.25 times faster with JavaScript then Firefox 3.5!**

Explanation: TraceMonkey got a 64-bit just-in-time compiler in Firefox 3.6!

Compared to Chromium (latest build):
chromium-browser 4.0.283.0~svn20091226r35283-0ubuntu1~ucd1~karmic Sunspider Results - 368.8ms

Chromium is still the king of JS performance on Ubuntu. :)

Another interesting comparison:

Firefox 3.5.6 (32-bit) running on Wine - 880.4ms
Firefox 3.6 Beta 5 (32-bit) running on Wine - 769.0ms

Looks like the Windows version (Firefox 3.5) beats the Linux version by a large amount! Firefox 3.6 is less of difference, but it still beats the Linux version. I couldn't test it with a 64-bit build, only 32-bit version is available. One explanation is the 32-bit version of Firefox is more optimised (ie, the JIT'er).

Here is a nice chart (X axis is "Execution time in milliseconds"):

[IMG]http://img130.imageshack.us/img130/3063/jsperf.png[/IMG]

Can you test minefield on your same system and let us know your results?

---

### Post by nrs on 2009-12-28
I think it's sad that Firefox runs faster in wine than it does natively. At least with 3.6 it looks like it's going to become a lot less sad -- but it's still slower.

---

### Post by crimesaucer on 2009-12-28
> **phrostbyte said:**
> I'm sure there is little optimisations they can do here and there on TraceMonkey :)

Well, the PGO part of comment was about a totally different set of hurdles that have finally been jumped over for the new Firefox versions.


Over on the Arch Forum (and the AUR), we have been struggling with PGO builds forever (way before TraceMonkey was invented), then when TraceMonkey was made we were trying to patch our builds for both TraceMonkey 64, and for Profile Guided Optimization. Now Firefox 3.7 finally has native TM-64, and will probably have the PGO patch built in also.

The Arch AUR packages:
[http://aur.archlinux.org/packages.php?ID=22919](http://aur.archlinux.org/packages.php?ID=22919)
[http://aur.archlinux.org/packages.php?ID=32030](http://aur.archlinux.org/packages.php?ID=32030)
[http://aur.archlinux.org/packages.php?ID=22296](http://aur.archlinux.org/packages.php?ID=22296)

And here are 2 PGO bugzilla pages (pgo working now): 

[https://bugzilla.mozilla.org/show_bug.cgi?id=520704](https://bugzilla.mozilla.org/show_bug.cgi?id=520704)
[https://bugzilla.mozilla.org/show_bug.cgi?id=418866](https://bugzilla.mozilla.org/show_bug.cgi?id=418866)


And our forum thread with details and benchmarking: [http://bbs.archlinux.org/viewtopic.php?id=73422&p=1](http://bbs.archlinux.org/viewtopic.php?id=73422&p=1)



> **Xbehave said:**
> As for talk about 3.7, wont that generally be slower than 3.6 until 3.6 starts feature freezing and changes are sent up the line to 3.7?


3.7 has been way faster for me (in both Linux and Windows). And both 3.7 and 3.6 version seem equally stable. The only issue I have with 3.7 that i don't have with 3.6 is that certain Add-ons aren't usable with the Nightly Tester Tools.

---

### Post by crimesaucer on 2009-12-28
Also, my peacekeeper benchmarks for Firefox 3.7a1pre (built with "--enable-canvas3d" in the mozconfig) got the score of: 1812

Sunspider is: 1426.6ms +/- 1.8%

Acid3: 93%

EDITED to add my computer specs (crappy laptop category):

Arch64 (mk8 AMD64 kernel patched with BFS, and CFLAGS = "-march=athlon64-sse3 -O2 -pipe", makeflags = "-j2")
Xfce4/xfwm4 compositing (at the time of that test), now I use Xmonad on xfce4 with no compositing. (I'll run the test again)
Hp Pavilion dv9920us AMD Turion 64 x2 TL-60 4GB RAM ddr2
NVIDIA GeForce 7150m /nForce 630m - 256MB integrated Up to 1071 MB shared, configured to performance:

```
$  nvidia-settings -q GPUCurrentClockFreqs -t
425,666
```

```
nvidia-settings -q GPUCurrentPerfLevel -t
2
```

---

### Post by Xbehave on 2009-12-28
> **crimesaucer said:**
> Also, my peacekeeper benchmarks for Firefox 3.7a1pre (built with "--enable-canvas3d" in the mozconfig) got the score of: 1812

Sunspider is: 1426.6ms +/- 1.8%
peacekeeper is very hw/os/driver dependent, could you give some context? what are your 3.6/3.5/chrome/etc scores?

---

### Post by crimesaucer on 2009-12-28
> **Xbehave said:**
> peacekeeper is very hw/os/driver dependent, could you give some context? what are your 3.6/3.5/chrome/etc scores?

I added my crappy specs in the post above. 


As for official Chrome64 results:

Peacekeeper for Chrome 4.0.249.43 = 2452 Points

Sunspider: 761.4ms +/- 1.3%

Acid3 test: 100%

---

### Post by phrostbyte on 2009-12-28
Here is the Peacekeeper results (Ubuntu 64-bit) - Compiz is enabled:
[IMG]http://img69.imageshack.us/img69/2947/firefox36b5.png[/IMG]
[IMG]http://img515.imageshack.us/img515/313/firefox356.png[/IMG]

Here is Peacekeeper result on Windows 7 (64-bit) - Aero is enabled:
[IMG]http://img39.imageshack.us/img39/8563/firefoxwin.png[/IMG]

Notice the rendering score.

---

### Post by .•*´ on 2010-01-28
SAfari 4
Opera 10
ePipany 2.26
Chrome 4


Are the only browsers that achieve 100% on acid3 test.

How significant that may be is open to opinion.

---

### Post by phrostbyte on 2010-01-28
> **.•*´ said:**
> SAfari 4
Opera 10
ePipany 2.26
Chrome 4


Are the only browsers that achieve 100% on acid3 test.

How significant that may be is open to opinion.

It's that all significant IMO, since most web sites are written to the lowest common denominator (eg: IE6). The thing Firefox is missing for Acid3 is SVG fonts really.

---

### Post by alfredkayser on 2010-02-04
> **Xbehave said:**
> ...but think that 
[v8]("http://v8.googlecode.com/svn/data/benchmarks/v5/run.html") (highly used js from real sites as a basis)
[dromea]("http://dromaeo.com/") (more stuff including css stuff)
Please note that v8 is NOT stuff from real sites, with benchmarks such as: Crypto, RayTrace, EarleyBoyer, RegExp, Splay. A typical site doesn't much raytracing, de/crypting, self balancing search trees, etc... V8 was specifically developed by Google to 'benchmark' its own browser...

See [http://ejohn.org/blog/javascript-performance-rundown/](http://ejohn.org/blog/javascript-performance-rundown/) for more information about different browser tests...

---

