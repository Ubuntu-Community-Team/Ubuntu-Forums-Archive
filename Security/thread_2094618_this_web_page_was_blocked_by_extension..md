---
title: "this web page was blocked by extension."
date: 2012-12-14
forum: Security
---

### Post by Matrix01 on 2012-12-14
Is anything wrong with this website?

---

### Post by vasa1 on 2012-12-14
Do you have AdBlock Plus installed? I've seen such an error with Chrome.

---

### Post by cariboo on 2012-12-15
I have the Adblock+ addon installed on Chromium, and I see the same thing, as the op.

---

### Post by Matrix01 on 2012-12-16
yep,
i do have Adblock Plus on Chrome.

In addition,
I went to a public library other day,
logged on their desktop, and tried to access to this website.

something like this popped up;
"security system blocked this website by this organization"

Their dsktop is Dell's dual core, Windows Vista, and Internet Explorer.




> **vasa1 said:**
> Do you have AdBlock Plus installed? I've seen such an error with Chrome.

---

### Post by Hungry Man on 2012-12-16
I have ABP with Chrome and it loads. Must be a specific filter.

---

### Post by Matrix01 on 2012-12-16
can u test this website;
[www.mykitchen.com?](www.mykitchen.com?)

---

### Post by vasa1 on 2012-12-16
> **Matrix01 said:**
> can u test this website;
[www.mykitchen.com?](www.mykitchen.com?)
Disable ABP and try. If it opens then it's an issue with ABP's filters.
Disable various filters until you find which is causing the problem.
Then post over here: [https://adblockplus.org/forum/viewforum.php?f=10](https://adblockplus.org/forum/viewforum.php?f=10) mentioning the site and the problematic filter.

Edit: I use ABP 1.3.1 for Chrome but have my own (few) filters and the site opens just fine.

---

### Post by vasa1 on 2012-12-16
BTW, have you allowed local data to be set? when I block that the site doesn't open.

chrome://chrome/settings/content in the section on Cookies.

---

### Post by OpSecShellshock on 2012-12-16
Nothing there anyway from what I can see. In other words, I went to the site with scripts disabled and got nothing. Looked at the source and it just loads a frame with an encoded string, which is not a good sign. If frames are blocked (and yes, of course they are) then supposedly it's just got a "click to proceed" message with a link that matches the source of the frame. Also not a great sign. I didn't even see that though.

So instead of figuring out if anything's wrong with it, at this point I'd suggest asking if there's any reason to go to that domain at all.

---

### Post by Matrix01 on 2012-12-25
i messed up their web address.
it's [www.ourkitchen.com](www.ourkitchen.com).

this' strange,
both address go to same site when i turn off Adblocker Plus.

i tried to get information of their canned beans from 'Our Kitchen'.
their site seem not to exist.

---

### Post by ka55o5 on 2012-12-29
Blank page on Firefox 17.0.1 with ABP, Privoxy and a hosts file blocking ads. In page source, there's a link that opens some index with:

> This Page Is Under Construction - Coming Soon!

---

