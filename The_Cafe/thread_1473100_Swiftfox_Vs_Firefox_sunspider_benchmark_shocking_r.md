---
title: "Swiftfox Vs Firefox sunspider benchmark shocking results enclosed"
date: 2010-05-04
forum: The Cafe
---

### Post by 133794m3r on 2010-05-04
Firefox is the build that comes with ubuntu(might be why it's faster than swiftfox), and swiftfox latest aka 3.6.3 I've also cleared all of the cache before doing either test to try to make it so that no results were skewed.

Here is swiftfox amd64's results.

[Swiftfox results]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B58,62,63,60,63%5D,%223d-morph%22:%5B31,31,30,31,31%5D,%223d-raytrace%22:%5B77,79,85,78,85%5D,%22access-binary-trees%22:%5B54,49,48,50,49%5D,%22access-fannkuch%22:%5B81,79,80,83,91%5D,%22access-nbody%22:%5B41,41,36,40,35%5D,%22access-nsieve%22:%5B15,15,15,24,14%5D,%22bitops-3bit-bits-in-byte%22:%5B2,2,2,2,2%5D,%22bitops-bits-in-byte%22:%5B12,11,11,11,11%5D,%22bitops-bitwise-and%22:%5B3,2,2,3,2%5D,%22bitops-nsieve-bits%22:%5B36,32,37,31,32%5D,%22controlflow-recursive%22:%5B41,41,49,45,41%5D,%22crypto-aes%22:%5B38,39,35,43,39%5D,%22crypto-md5%22:%5B17,16,17,16,17%5D,%22crypto-sha1%22:%5B9,9,9,9,10%5D,%22date-format-tofte%22:%5B125,131,128,124,124%5D,%22date-format-xparb%22:%5B79,83,79,84,78%5D,%22math-cordic%22:%5B16,12,20,20,16%5D,%22math-partial-sums%22:%5B29,28,28,28,29%5D,%22math-spectral-norm%22:%5B8,8,8,8,8%5D,%22regexp-dna%22:%5B59,61,61,65,71%5D,%22string-base64%22:%5B13,13,14,13,14%5D,%22string-fasta%22:%5B87,90,89,88,94%5D,%22string-tagcloud%22:%5B107,116,113,111,114%5D,%22string-unpack-code%22:%5B118,112,113,113,112%5D,%22string-validate-input%22:%5B42,41,36,35,44%5D%7D")
[,%223d-morph%22:[96,102,97,96,101],%223d-raytrace%22:[101,98,98,99,103],%22access-binary-trees%22:[42,42,49,43,42],%22access-fannkuch%22:[167,171,168,175,167],%22access-nbody%22:[114,117,107,109,119],%22access-nsieve%22:[47,47,47,51,46],%22bitops-3bit-bits-in-byte%22:[46,47,46,50,48],%22bitops-bits-in-byte%22:[73,73,73,72,72],%22bitops-bitwise-and%22:[65,62,68,62,61],%22bitops-nsieve-bits%22:[84,89,90,83,89],%22controlflow-recursive%22:[37,36,38,38,38],%22crypto-aes%22:[64,62,59,66,60],%22crypto-md5%22:[46,46,48,47,49],%22crypto-sha1%22:[49,48,49,49,51],%22date-format-tofte%22:[95,92,93,93,92],%22date-format-xparb%22:[99,102,99,99,98],%22math-cordic%22:[118,118,116,124,127],%22math-partial-sums%22:[102,100,99,119,106],%22math-spectral-norm%22:[51,50,61,57,50],%22regexp-dna%22:[229,225,226,229,214],%22string-base64%22:[46,43,48,44,43],%22string-fasta%22:[119,116,117,112,115],%22string-tagcloud%22:[127,124,140,142,149],%22string-unpack-code%22:[173,156,209,212,243],%22string-validate-input%22:[62,67,70,78,79]}"]Firefox Results]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?{%223d-cube%22:[102,113,102,104,105)

Firefox the base one on 10.04 is ~1.2x faster at its slowest and ~5x faster at its fastest. This leads me to believe that the swiftfox build has some serious javascript engine changes to it or something similar to warrant this extreme speed decrease. Also, can anyone else out there do a similar test on your system so that we can get some more benchmarks/comparisons going for a more legitimate results thread so that the findings will be more likely to be correct.

---

### Post by lovinglinux on 2010-05-04
I'm almost sleeping over the keyboard, but according to my tests and yours too, Firefox isn't faster than Swiftfox.

**Mine:**
[Firefox 2955.2ms](http://tinyurl.com/246rod4)
[Swiftfox 1562.6ms](http://tinyurl.com/2f8zo94)

**Yours:**
Firefox 2407.4ms
Swiftfox 1210.0ms

There is nothing shocking about that, since Swiftfox is compiled with architecture  optimization flags. So it is normal.

---

### Post by -humanaut- on 2010-05-04
I've accutally promoted and adopted Swiftfox Athlon 64 for sometimes and my speed was always faster then Firefox but I have alot of security concerns over Swiftfox now mostly because im a Paranoid but Swiftfox was significantly faster for me.

---

### Post by 133794m3r on 2010-05-05
ah... seems that Sunspider's items were misleading when i was looking at the data since it was always seemingly showing firefox as the faster one. I was just looking at the various ons and didn't look to see if it was done all together. Woops guess i should've noticed that... :lolflag: seems i should check over things before just scanning over all of the data.

---

