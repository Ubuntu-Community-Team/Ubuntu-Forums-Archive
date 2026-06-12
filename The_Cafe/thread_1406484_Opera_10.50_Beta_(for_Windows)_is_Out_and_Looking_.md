---
title: "Opera 10.50 Beta (for Windows) is Out and Looking Good"
date: 2010-02-14
forum: The Cafe
---

### Post by chessnerd on 2010-02-14
While this beta is currently only for Windows (hopefully the Linux one will be out soon), I must say, the Opera team has done a good job. 

The pre-alpha released last Christmas was pretty buggy and didn't always live up to the claimed speeds. This beta build seems pretty solid and is really fast. Standard web-page loading in Opera has always been fast, but it's the new JavaScript engine that everyone it talking about, so I took a look at that:

The SunSpider JavaScript Benchmark for mine was [939.2 m/s]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B32,34,34,33,33%5D,%223d-morph%22:%5B39,40,40,40,39%5D,%223d-raytrace%22:%5B42,44,42,42,42%5D,%22access-binary-trees%22:%5B13,13,13,13,12%5D,%22access-fannkuch%22:%5B43,43,44,44,46%5D,%22access-nbody%22:%5B28,29,28,28,29%5D,%22access-nsieve%22:%5B14,13,13,13,13%5D,%22bitops-3bit-bits-in-byte%22:%5B4,4,3,4,3%5D,%22bitops-bits-in-byte%22:%5B5,4,5,5,6%5D,%22bitops-bitwise-and%22:%5B4,5,5,5,4%5D,%22bitops-nsieve-bits%22:%5B21,20,20,20,19%5D,%22controlflow-recursive%22:%5B9,10,10,9,10%5D,%22crypto-aes%22:%5B34,32,32,31,31%5D,%22crypto-md5%22:%5B11,11,11,11,11%5D,%22crypto-sha1%22:%5B8,8,8,8,8%5D,%22date-format-tofte%22:%5B62,61,60,66,60%5D,%22date-format-xparb%22:%5B98,99,96,106,96%5D,%22math-cordic%22:%5B19,19,23,19,19%5D,%22math-partial-sums%22:%5B64,63,64,63,65%5D,%22math-spectral-norm%22:%5B13,13,14,13,13%5D,%22regexp-dna%22:%5B34,35,35,33,35%5D,%22string-base64%22:%5B62,61,61,61,61%5D,%22string-fasta%22:%5B51,53,51,50,51%5D,%22string-tagcloud%22:%5B91,89,89,89,88%5D,%22string-unpack-code%22:%5B70,69,69,69,70%5D,%22string-validate-input%22:%5B70,69,69,68,68%5D%7D") while the Chrome 5 Beta was [,%223d-morph%22:[78,57,62,59,58],%223d-raytrace%22:[45,40,42,41,42],%22access-binary-trees%22:[5,4,4,4,4],%22access-fannkuch%22:[34,33,34,33,33],%22access-nbody%22:[42,42,39,42,40],%22access-nsieve%22:[9,9,10,10,9],%22bitops-3bit-bits-in-byte%22:[6,6,7,8,7],%22bitops-bits-in-byte%22:[24,20,20,20,20],%22bitops-bitwise-and%22:[21,21,22,22,22],%22bitops-nsieve-bits%22:[28,27,26,27,26],%22controlflow-recursive%22:[7,7,8,7,7],%22crypto-aes%22:[26,22,23,22,22],%22crypto-md5%22:[20,19,19,19,20],%22crypto-sha1%22:[19,19,19,19,19],%22date-format-tofte%22:[57,50,50,50,50],%22date-format-xparb%22:[64,65,59,58,57],%22math-cordic%22:[37,37,40,34,36],%22math-partial-sums%22:[60,57,57,56,56],%22math-spectral-norm%22:[17,19,18,18,18],%22regexp-dna%22:[43,48,41,41,41],%22string-base64%22:[32,31,32,33,31],%22string-fasta%22:[41,42,50,51,42],%22string-tagcloud%22:[97,84,73,85,85],%22string-unpack-code%22:[77,95,87,93,86],%22string-validate-input%22:[47,43,46,44,45]}"]960.0 m/s]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?{%223d-cube%22:[52,67,59,64,65), meaning that Opera 10.50 is faster than Chrome. As for Firefox, well, [,%223d-morph%22:[148,112,112,111,112],%223d-raytrace%22:[141,141,146,140,139],%22access-binary-trees%22:[100,90,90,91,87],%22access-fannkuch%22:[157,161,159,160,165],%22access-nbody%22:[50,51,52,53,52],%22access-nsieve%22:[26,26,27,28,27],%22bitops-3bit-bits-in-byte%22:[4,3,4,5,3],%22bitops-bits-in-byte%22:[23,22,23,22,23],%22bitops-bitwise-and%22:[6,6,5,6,6],%22bitops-nsieve-bits%22:[58,55,55,54,54],%22controlflow-recursive%22:[94,96,95,95,97],%22crypto-aes%22:[64,62,73,63,70],%22crypto-md5%22:[28,24,29,30,30],%22crypto-sha1%22:[17,18,18,18,17],%22date-format-tofte%22:[166,189,177,190,183],%22date-format-xparb%22:[176,174,163,177,167],%22math-cordic%22:[70,71,69,56,71],%22math-partial-sums%22:[80,40,39,30,41],%22math-spectral-norm%22:[15,15,14,15,15],%22regexp-dna%22:[135,126,124,124,123],%22string-base64%22:[26,27,26,28,26],%22string-fasta%22:[138,136,138,138,133],%22string-tagcloud%22:[173,163,187,193,177],%22string-unpack-code%22:[191,196,197,194,196],%22string-validate-input%22:[63,66,71,70,90]}"]look if you want, but it ain't pretty...]("http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?{%223d-cube%22:[85,87,90,88,90)

The new interface has been cleaned up a bit. It both looks really nice and feels nicer to work with. The in-browser windows look better than in previous versions. Right clicking a tab gives you even more options now and reveals a "Private Tab" option similar to Chrome's "Incognito Mode." Also, the multi-tab preview on Windows 7 works in this beta. The pre-alpha build failed at this task (for me at least).

An interesting addition is the "upgraded" widgets, which are now standalone applications which can run even without the Opera browser being open (not sure if they'll run after an uninstall, but it wouldn't suprise me). The "Manage Widgets..." option now opens the Windows Add/Remove Programs Manager, which shows that, yes, all you're widgets are installed applications. The widgets also get Start Menu links. I'm not sure how this will work on Linux, and I'm not sure how I feel about it on the whole, but it's cool to play Basketball without having Opera open.

Overall, I'm impressed and, baring a massive upgrade in Chrome or Firefox, it seems I'll be sticking with Opera for the foreseeable future.

---

### Post by HappinessNow on 2010-02-14
> **chessnerd said:**
> 

An interesting addition is the "upgraded" widgets, which are now standalone applications which can run even without the Opera browser being open (not sure if they'll run after an uninstall, but it wouldn't suprise me). The "Manage Widgets..." option now opens the Windows Add/Remove Programs Manager, which shows that, yes, all you're widgets are installed applications. The widgets also get Start Menu links. I'm not sure how this will work on Linux, and I'm not sure how I feel about it on the whole, but it's cool to play Basketball without having Opera open.

They finally brought this back! This used to be one of my favorite part of Opera widgets is that you didn't have to have the browser open.

When they first came out with opera widgets this was a default function, and then it disappeared for some reason?

Glad to see it back!

I went to update my Opera but it appears I removed it, I'll install it again and give it a whirl!

EDIT: Link: [http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)

EDIT: unfortunately most of the widgets I have tried out are broken. I liked the original desktop widget function better then this one.

EDIT: I hate to say it but I am uninstalling Opera (all versions).

---

