---
title: "Flash (SWF) decompilers in Linux"
date: 2009-06-22
forum: The Cafe
---

### Post by ThinkBuntu on 2009-06-22
I came across this topic when searching today: 
[http://ubuntuforums.org/showthread.php?t=681701](http://ubuntuforums.org/showthread.php?t=681701)

It seems that the conclusion there was that the poster was attempting to steal code. However, I have a SWF for a design project with no matching FLA provided, and would definitely like to decompile it, so that assumption is not always correct. The SWF itself is very simple.

Does anybody know of tools for decompiling simple SWF files in Linux? "flasm" is the closest tool I've found thus far: [http://www.nowrap.de/flasm.html](http://www.nowrap.de/flasm.html). Flare ( [http://www.nowrap.de/flare.html](http://www.nowrap.de/flare.html) ) also looks promising.

---

### Post by dragos240 on 2009-06-22
> **ThinkBuntu said:**
> I came across this topic when searching today: 
[http://ubuntuforums.org/showthread.php?t=681701](http://ubuntuforums.org/showthread.php?t=681701)

It seems that the conclusion there was that the poster was attempting to steal code. However, I have a SWF for a design project with no matching FLA provided, and would definitely like to decompile it, so that assumption is not always correct. The SWF itself is very simple.

Does anybody know of tools for decompiling simple SWF files in Linux? "flasm" is the closest tool I've found thus far: [http://www.nowrap.de/flasm.html](http://www.nowrap.de/flasm.html). Flare ( [http://www.nowrap.de/flare.html](http://www.nowrap.de/flare.html) ) also looks promising.


Not that i've heard of.... I used to use sothink's flash decompiler. It worked like a charm, it costed money, but it worked excelent. I have an edited version of line rider, on sal's, but i'm ip banned.

---

### Post by tazza on 2009-07-09
after some looking around I found that swftools is a great package in the repository. When installed there are a few tools you can use including:
swfbbox, swfc, swfcombine, swfdump, swfextract, swfextract and swfstrings.
I thing that swfextract might be the most helpful.

Is this what you are looking for?

---

### Post by Yellobes on 2012-05-15
Sorry to dig up an old thread, but my employer has asked me to investigate a potentially hacked site, and I need to decompile some *swfs. Have y'all made any further progress on this/ do y'all still remember?

---

