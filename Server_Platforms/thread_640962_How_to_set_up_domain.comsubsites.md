---
title: "How to set up domain.com/subsites"
date: 2007-12-14
forum: Server Platforms
---

### Post by i_meister on 2007-12-14
I've found tutorials on how to set up multiple sites as virtual hosts, but what I'd like to set up are multiple sub-directories, like this:

[http://127.0.0.1/](http://127.0.0.1/)               is the website
[http://127.0.0.1/AnotherSite](http://127.0.0.1/AnotherSite)              is another site
[http://127.0.0.1/YetAnotherSite](http://127.0.0.1/YetAnotherSite)           etc.

(Yes, I know I can't use 'home' -- I just don't have my IP address memorized yet. :P  )

What I *don't* want is [www.site1.com](www.site1.com), [www.site2.com](www.site2.com), etc.  What magical thing do I tell apache to get it to look for an index.html when someone puts in [http://myurl/_blah_?](http://myurl/_blah_?)

Thanks in advance,
Ian

---

### Post by bnuytten on 2007-12-15
Have a look at the mod_rewrite module for Apache. I am pretty sure this can rewrite a request like [http://myurl/_blah_?](http://myurl/_blah_?) into [http://myurl/](http://myurl/) or something else. Before you dive into it, I propose you learn about regular expressions (regex) ;-)

---

