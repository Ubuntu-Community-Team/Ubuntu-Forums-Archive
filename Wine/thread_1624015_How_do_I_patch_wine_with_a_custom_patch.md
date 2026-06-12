---
title: "How do I patch wine with a custom patch?"
date: 2010-11-17
forum: Wine
---

### Post by jehiva on 2010-11-17
Hello all,

Could someone give a beginner a step by step guide how to apply a patch to wine source? 

I attempted to do this, but received a ton of error messages about hunks being rejected (and output saved to a .rej file).

Thanks!

---

### Post by doctorzeus on 2010-11-18
> **jehiva said:**
> Hello all,

Could someone give a beginner a step by step guide how to apply a patch to wine source? 

I attempted to do this, but received a ton of error messages about hunks being rejected (and output saved to a .rej file).

Thanks!

Funny, I was just about to patch wine to play Empire Total War....

This fairly easy Tutorial can be adapted easily for your specific patch:

[http://shae.me/linux/warcraft-3-wine-and-ubuntu-9-10/](http://shae.me/linux/warcraft-3-wine-and-ubuntu-9-10/)

bit outdated but the theory still applies and the new version (1.3.6) will be downloaded instead...

Hope this helps!

Doctorzeus

P.S

There are about 500 posts on how to patch wine, search the forums before posting :)

---

### Post by jehiva on 2010-11-22
Hello doctorzeus,

Thanks for the response, I was still unable to patch (the tutorial does not address hunk mismatch).

After playing around with it for a bit I was able to patch with the following command:

(In the wine source directory)

patch -p0 -F3 --ignore-whitespace < my.patch

Next time in addition to searching first, I supposed I should RTFM :)

The patch still had hunk messages with only the whitespace option, but when applying the fuzzy it worked without any error messages.  Following this, wine compiled file and my patch worked flawlessly.

---

### Post by doctorzeus on 2010-11-22
Null

---

### Post by doctorzeus on 2010-11-22
> **jehiva said:**
> Hello doctorzeus,

Thanks for the response, I was still unable to patch (the tutorial does not address hunk mismatch).

After playing around with it for a bit I was able to patch with the following command:

(In the wine source directory)

patch -p0 -F3 --ignore-whitespace < my.patch

Next time in addition to searching first, I supposed I should RTFM :)

The patch still had hunk messages with only the whitespace option, but when applying the fuzzy it worked without any error messages.  Following this, wine compiled file and my patch worked flawlessly.

Glad to see you had more luck then me, good for you for figuring it out! :p My patches were seen as Garbage by the compiler...gonna play around with them when I get some free time..

Glad to be of help though!

---

