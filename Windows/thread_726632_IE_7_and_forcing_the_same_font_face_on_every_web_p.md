---
title: "IE 7 and forcing the same font face on every web page."
date: 2008-03-16
forum: Windows
---

### Post by vexorian on 2008-03-16
I won't flood you with details, but I need to actually read html pages in IE using an specific font (Dejavu Sans) because of retarded stuff, using other browsers will not solve my issue.

It is possible to force a font face on all pages for both firefox, opera and many others, yet IE seems to favor windows' fonts too much, the only way I managed to use the correct was deleting the other fonts , but this negatively affects other programs (specially msoffice) so it is a bad solution.

I am wondering if installing IE7 could solve my issue, I certainly don't want to increase IE7's download counter for such a lame reason in vain, so my question is whether it is possible to force a certain font face on every page viewed by IE7.

---

### Post by chewearn on 2008-03-17
It's actually possible, but the option is hidden under Accessibility preferences.  You can set IE7 to ignore the color, font styles and font sizes specified by the webpages.  You can also specify your own (generic) css file.

---

### Post by vexorian on 2008-03-17
> **AstalaVista said:**
> It's actually possible, but the option is hidden under Accessibility preferences.  You can set IE7 to ignore the color, font styles and font sizes specified by the webpages.  You can also specify your own (generic) css file.

That dialog exists in IE6, but it doesn't allow you to change the font style, I have not tried the generic CSS way but I've seen IE6 ignores it when you specify a font different to MS' beloved proprietary fonts.


I specifically need to make it show the page using Dejavu Sans or any other font that's not a MS one. Does IE7 allow you to do that in that dialog?

---

### Post by chewearn on 2008-03-18
Ok, I did a test on IE7; default settings:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=62952&d=1205820004[/IMG]


Setting of:
Ignore font styles specified on webpages + custom css
```
body { font-family:"DejaVu Sans"; }
```[IMG]http://ubuntuforums.org/attachment.php?attachmentid=62953&d=1205820004[/IMG]


So, it does work.

---

