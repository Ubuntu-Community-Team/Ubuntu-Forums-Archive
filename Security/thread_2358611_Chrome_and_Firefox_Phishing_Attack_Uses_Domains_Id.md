---
title: "Chrome and Firefox Phishing Attack Uses Domains Identical to Known Safe Sites"
date: 2017-04-15
forum: Security
---

### Post by philhughes on 2017-04-15
Posting this to help it get wider visibility on a quiet weekend:

[https://www.wordfence.com/blog/2017/04/chrome-firefox-unicode-phishing/?utm_source=list&utm_medium=email&utm_campaign=041417](https://www.wordfence.com/blog/2017/04/chrome-firefox-unicode-phishing/?utm_source=list&utm_medium=email&utm_campaign=041417)

---

### Post by KenUBF on 2017-04-15
Wow. That's crazy. I can't tell the difference at all. Only by right clicking and opening the Inspect window in Chromium and looking at Sources did it even tell me the name of the actual website. As of right now that's the only way I've found to tell the sites apart. In Firefox if you look at the certificate it tells you the name of the real website. Thanks for the heads up!

---

### Post by vasa1 on 2017-04-19
I'm posting two images of what I see when I click on their demo link:
The first is with Chrome Dev (Version 59.0.3071.9 (Official Build) dev (64-bit))
The second is with Firefox 52.0.2.

I'll post a third with Chrome stable in a while.

And here's a third, this with Chrome stable (Version 57.0.2987.133 (64-bit))

---

### Post by Habitual on 2017-04-19
Toggling a value in about / config disables it in Firefox. No restart necessary.

---

### Post by vasa1 on 2017-04-19
That about:config setting is covered in the link in the OP:> In your firefox location bar, type &#8216;about:config&#8217; without quotes.

Do a search for &#8216;punycode&#8217; without quotes.

You should see a parameter titled: network.IDN_show_punycode

Change the value from false to true.

---

### Post by vasa1 on 2017-04-19
Chrome stable Version 58.0.3029.81 (64-bit) released on April 19 [s]fixes[/s]addresses this. Of the various bugs listed in [https://chromereleases.googleblog.com/2017/04/stable-channel-update-for-desktop.html](https://chromereleases.googleblog.com/2017/04/stable-channel-update-for-desktop.html), only [https://bugs.chromium.org/p/chromium/issues/detail?id=683314](https://bugs.chromium.org/p/chromium/issues/detail?id=683314) is public. From there:> Block domain labels made of Cyrillic letters that look alike Latin

Block a label made entirely of Latin-look-alike Cyrillic letters when the TLD is not an IDN (i.e. this check is ON only for TLDs like 'com', 'net', 'uk', but not applied for IDN TLDs like &#1088;&#1092;.


Firefox 53.0 (64-bit) still needs the about:config workaround.

---

### Post by KenUBF on 2017-04-20
I use Chromium. Does anyone know when a stable version will be released? I can confirm that the about:config solution works in Firefox. Just tested it.

---

### Post by vasa1 on 2017-04-20
Well, there's no fixed schedule. It depends on the time available to the maintainer of the package and on how easy it is to build for each supported version (and architecture).

---

