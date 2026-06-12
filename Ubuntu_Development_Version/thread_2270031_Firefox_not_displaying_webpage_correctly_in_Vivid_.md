---
title: "Firefox not displaying webpage correctly in Vivid 15.04"
date: 2015-03-19
forum: Ubuntu Development Version
---

### Post by andyklein on 2015-03-19
This webpage (which I imagine is used by a lot of folks who, like me, have an employer that unfortunately uses Microsoft's Office 365 cloud service) --
  [https://login.microsoftonline.com/](https://login.microsoftonline.com/)
doesn't render correctly in Firefox 36.0.1 on a fresh (fully-updated as of 19-March-2015) stock install of Ubuntu 15.04 beta. In addition, the webpage is not functional since it is impossible to type into the textboxes.

It renders and works correctly in Firefox 36.0.1 in Ubuntu 14.04 LTS and in Chromium on Ubuntu 15.04 beta.

I have attached screenshots of incorrect (FF w/15.04) and correct (FF w/14.04) renderings below. I am wondering if anyone can reproduce this incorrect rendering with Firefox on 15.04 vivid?

Thanks.

---

### Post by MikeMecanic on 2015-03-19
Me 2 have problems.  Install add blocker and problem was FIXED.   Never know, try it.  I have no problem so far with Opera 28: [http://www.opera.com/computer/linux](http://www.opera.com/computer/linux)

Try that add-on for Firefix: [https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/)

---

### Post by andyklein on 2015-03-19
Hmm, thanks for trying. I have tried both with and without the AdBlock Plus extension, and I get the same result.

If anyone else gets a chance to try this link, I would be keen to know the results. If more people find similar results, I will put post a bug.

---

### Post by sammiev on 2015-03-19
Using gnome 15.04 here and this is what I get.

---

### Post by cariboo on 2015-03-19
It's not firefox that's the problem, I use chromium most of the time, and I get something similar on some web pages

I once asked Jorge about it, as I thought it was a problem with the Discourse page. He suggested it may be a missing font package.

---

### Post by MikeMecanic on 2015-03-19
Her's what I get on my installation.

---

### Post by cariboo on 2015-03-20
Moved a couple of duplicate posts to the jail.

---

### Post by andyklein on 2015-03-20
Was totally a missing font problem. Thanks, cariboo907.

---

