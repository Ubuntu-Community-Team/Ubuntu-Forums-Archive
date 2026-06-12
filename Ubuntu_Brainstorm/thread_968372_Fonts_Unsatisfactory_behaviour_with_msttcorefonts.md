---
title: "Fonts: Unsatisfactory behaviour with msttcorefonts"
date: 2008-11-02
forum: Ubuntu Brainstorm
---

### Post by melkart76 on 2008-11-02
I would like to know your opinions on the following fonts issues, and if anything that I write, is wrong, please correct me.

Ubuntu ships without the package msttcorefonts, and on a fresh install the liberation font is not installed, either. Many web pages are designed to require Windows fonts, like Arial etc. When these fonts are not installed, firefox renders the pages with some other font, and that often doesn't look bad at all. But as soon as the user installs the package msttcorefonts, the web page suddenly looks quite different, because now the font Arial is available. Of course, it is a matter of choice, which fonts look good and which don't, but it is very undesirable that only by installing a new package the system changes its behaviour. The user was used to the look without Arial installed and now, all of a sudden, he finds the web pages frequented by him to look different.

This wouldn't be the case, if Ubuntu had the Liberation font installed by default. The Microsoft fonts are free to use, but come with an EULA and therefore can't be shipped with Ubuntu by default. The Liberation font was designed to resemble the Microsoft font and has the GPL license. Wouldn't it be better if Ubuntu shipped with the Liberation font installed by default? Not for being used as the system's standard font, but just for avoiding web pages requiring MS fonts looking different as soon as the user installs msttcorefonts.

Further, Ubuntu uses Antialiasing by default. When the package msttcorefonts is installed, the Microsoft fonts, like Arial, get antialiased, too. On Windows, these fonts are not antialiased for small sizes and the result looks quite different, and, in my opinion, better. I presume that these fonts were just designed not be antialiased at small sizes. Anyway, the looks of web pages using these fonts is different in Ubuntu compared to Windows, and I think, worse.

Apparently it is possible to configure the system in such a way that, just like in Windows, these fonts - and only these - are exempted from Antialiasing at small sizes. There is a website, which explains how to achieve this: [http://www.sharpfonts.com](http://www.sharpfonts.com). Thus, Ubuntu can be configured in such a way that web pages requiring Microsoft fonts look exactly like on Windows, with msttcorefonts installed. And with the Liberation font they still look very similar. Shouldn't Ubuntu be configured in such a way by default?

I attached two screenshots to this post. Both show how firefox renders the Google News-page when msttcorefonts are installed. On the first screenshot the font gets antialiased. On the second screenshot the system is configured not to antialias the MS fonts. On a system with neither msttcorefonts nor the Liberation font installed, the page looks quite different once again.

---

### Post by smartboyathome on 2008-11-02
I don't see it as much of a need. Who really cares if web pages don't look "exact", any good web developer would have wrote it so that even if the fonts are different, they will still work as intended.

---

### Post by melkart76 on 2008-11-02
> **smartboyathome said:**
> I don't see it as much of a need. Who really cares if web pages don't look "exact", any good web developer would have wrote it so that even if the fonts are different, they will still work as intended.

Well, I have a different opinion. When a user experiences, that the fonts on his system look different *all of a sudden* (because he installed msttcorefonts, maybe inadvertently, because it was just pulled in by another package), and he doesn't know why and what to do about it, this destroys his trust in the system's stability. When this happened to me the first time and I had no clue what was going on, I had a fit and cursed Ubuntu for its perceived brokenness, so much that I even reinstalled my old distribution.

Font looks are a big issue by itself, but maybe even more important is the impression of strange, unpredictable behaviour that is caused in the user by the current situation.

---

### Post by Merk42 on 2008-11-03
is there something that will install msttcorefonts? I mean the user could accidentally increase the font size and then things would look different. How about if the user downloaded a more specific font the web site would use?

Other than the search bar, it's really difficult to see the change unless they're side by side. Ubuntu or not, it's impossible to have the same site render across all browsers, even with the same fonts.

---

