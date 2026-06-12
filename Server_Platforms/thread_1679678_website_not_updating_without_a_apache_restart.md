---
title: "website not updating without a apache restart?"
date: 2011-02-01
forum: Server Platforms
---

### Post by Ghosthaven on 2011-02-01
First, I'm a total newbie to web servers and only slightly less of
a newbie to linux. So this is going to be one of those posts that
you guys look at and think "What a doofus, who on earth doesn't
know how to do THAT?!?".

I've installed Ubuntu server and got everything setup pretty well.
My problem is apache.

I put my website in /var/www and changed the security on the files
to allow them to be executed by other, which is what I finally
discovered was my first problem (access denied). But now whenever
I go in and edit my page, the changes aren't reflected on the site
unless I completely restart apache.

I know I'm doing something wrong because I used to pay for a host
and every time I edited a page, it was instantly updated on the
site. Could one of you gurus tell me where I screwed up?

---

### Post by Thirtysixway on 2011-02-01
Perhaps it's cache?

---

### Post by Ghosthaven on 2011-02-01
That's what I thought at first. I tried a hard refresh as well
as trying it on another browser. I even tried it on another
computer... no luck.

Does apache have some kind of update timer?

---

### Post by wojox on 2011-02-01
Sounds like a permissions problem. What are they set at? What did you change them to?

---

### Post by Ghosthaven on 2011-02-01
Well I do believe I'm about the most embarrassed I've been in my
life.

Turns out it was a browser issue after all, all the browsers I used
to test the page had DNS pre-fetching enabled and that prevented
the page from updating when reloaded.

My apologies to the forum.

---

