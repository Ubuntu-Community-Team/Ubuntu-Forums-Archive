---
title: "Improving &quot;man&quot; command's configuration"
date: 2008-02-21
forum: Ubuntu Brainstorm
---

### Post by Vesa Paatero on 2008-02-21
Hi everyone,

In my experience it is problematic for inexperienced users that the "man" command only shows the first matching man page. For example, if you write "man printf", you will only see the printf man page of section 1, not that of section 3 or any other section.

Back in the years of my university studies, I came a cross a system configured so that when you typed e.g. "man printf", it would show all printf pages in succession (but suitably separated), and it felt like just the right way to do it. Today I tried to find out which switch (or its equivalent in configuration files) could be used to do that. I found "-a" but the test that followed showed that -a is not quite as handy as I had hoped: With -a you have to press both 'q' and 'Control-C' to quit displaying multiple matching man pages (i.e. 'q' to stop the current page and Control-C to stop the chain of all matching pages).  As I remember it, the best configuration was such that pressing 'q' twice was enough to stop displaying a chain of matching man pages.

Would it be possible to configure the default man pager functionality of Ubuntu Linux so that you get all the matching man pages but that the chain of multiple pages is handy to deal with?

In fact, the "best configuration" that I explained above was probably running on Irix or some UNIX brand other than Linux.

Regards,
Vesa

---

