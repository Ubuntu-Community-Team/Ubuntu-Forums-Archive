---
title: "Kraken: new Mozilla's browser benchmark"
date: 2010-09-14
forum: The Cafe
---

### Post by lovinglinux on 2010-09-14
Is amazing how many new stuff Mozilla is creating recently.

> Source: [http://blog.mozilla.com/blog/2010/09/14/release-the-kraken-2/](http://blog.mozilla.com/blog/2010/09/14/release-the-kraken-2/)

Release the Kraken
Posted by Erica Jostedt

September 14th, 2010 · Firefox, Mozilla News

Editor&#8217;s note: On Sept. 14, Mozilla released a new JavaScript benchmark named Kraken. For more details, check out Rob Sayre&#8217;s announcement, reposted below.

    We&#8217;re pleased to announce the first version of Kraken, a new browser benchmark. More than Sunspider, V8, and Dromaeo, Kraken focuses on realistic workloads and forward-looking applications. We believe that the benchmarks used in Kraken are better in terms of reflecting realistic workloads for pushing the edge of browser performance forward. These are the things that people are saying are too slow to do with open Web technologies today, and we want to have benchmarks that reflect progress against making these near-future apps universally available.



---

### Post by jerenept on 2010-09-14
This is probably going to be biased toward FF4, but I would be interested to see the benchmarks for the 3 major browsers of tomorrow: (FF4, Chrome 6, IE9)

---

### Post by Dustin2128 on 2010-09-14
*grumbles*
I opened this thread when I just saw the word kraken. I'm disappointed...

---

### Post by clevin on 2010-09-15
> **jerenept said:**
> This is probably going to be biased toward FF4, but I would be interested to see the benchmarks for the 3 major browsers of tomorrow: (FF4, Chrome 6, IE9)

Lets judge the stuff by its merit. If we say Kraken is biased towards firefox because mozilla assembled the test, then obviously sunspider is biased towards safari, and v8 is biased towards chrome.

The reality is. Sunspider and V8 has way too many toy benchmarks that makes no practical sense, you can be a million times faster, but has absolutely no real use. e.g.

> It [sunspider] has a few real applications, but they&#8217;re far too small. For example, crypto-md5 computes an md5sum on some text. Firefox generates really good code for its main loop, but the input text is so short that the trace compilation overhead swamps it and we get a bad score. (And the overhead isn&#8217;t that big, but the test only takes 13ms to run.) If the text was 100x bigger I think we&#8217;d easily have the best score.

In real life, you either has a large one need fast browser to work, which firefox will sure help you, or you have a small one that everybody can finish in a ms. and why is that firefox has to be labeled "slow" in this task, when it actually is faster for users overall?

---

