---
title: "Scientific Software Again"
date: 2005-12-16
forum: Requests
---

### Post by larry on 2005-12-16
Hi,
I work quite a lot with R-cran, which should be familiar to plenty of people having tried their hands at statistics.
I personally need some packages which were released shortly before Ubuntu 5.10 (namely, the copula package released on the 18th of September 2005 in my case).
Some previous requests of mine showed that I am not alone in the Ubuntu community to need really up-to-date scientific software. This package (and all the newly released R packages) are already built for Debian, so it should not be a pain to have them ready for Ubuntu.
Unfortunately, I am not able to do it myself, hence my request. I could perhaps install that package from source, but then it would not get any updated/fixed versions when they are released, unless I manually take care of it. 
Bottom line: it is much better to have it in the Ubuntu Breezy backports.
Best Regards

Larry

---

### Post by UphillSkier on 2005-12-16
[QUOTE=larry]Hi,
I work quite a lot with R-cran, which should be familiar to plenty of people having tried their hands at statistics.
I personally need some packages which were released shortly before Ubuntu 5.10 (namely, the copula package released on the 18th of September 2005 in my case).
Some previous requests of mine showed that I am not alone in the Ubuntu community to need really up-to-date scientific software. This package (and all the newly released R packages) are already built for Debian, so it should not be a pain to have them ready for Ubuntu.
Unfortunately, I am not able to do it myself, hence my request. I could perhaps install that package from source, but then it would not get any updated/fixed versions when they are released, unless I manually take care of it. 
Bottom line: it is much better to have it in the Ubuntu Breezy backports.
Best Regards


Larry[/QUOTE]
If there is a debian package available, can't you just download it and apply apt-get? Sorry if this is a naive response, but I use R as well and would like to know.

{edit}  Sorry - this post probably doesn't belong in this forum.  I didn't realize this was the backports forum when I posted.

---

### Post by macgyver2 on 2005-12-16
[QUOTE=larry]I personally need some packages which were released shortly before Ubuntu 5.10 (namely, the copula package released on the 18th of September 2005 in my case).[/QUOTE]
The issue here is that the copula package doesn't appear to be in Ubuntu yet (you can check for yourself using the [package database](http://packages.ubuntu.com/)).  The Backports project, well, does just that--backports.  If a package isn't in the Ubuntu development branch, it can't be backported.

I believe *[this](https://wiki.ubuntu.com/UniverseCandidates)* is the approach you need to take initially.

---

### Post by macgyver2 on 2005-12-19
Follow-up: You might also post your request for science-related packages to the [EMAIL="ubuntu-science@tauware.de"]ubuntu-science mailing list[/EMAIL].

---

