---
title: "About some security news on glibc."
date: 2016-02-25
forum: Ubuntu, Linux and OS Chat
---

### Post by bapoumba on 2016-02-25
I'm not sure i get the whole picture though..
This popped in my news feed : [http://www.ibtimes.co.uk/google-red-hat-discover-critical-dns-security-flaw-that-enables-malware-infect-entire-internet-1545687](http://www.ibtimes.co.uk/google-red-hat-discover-critical-dns-security-flaw-that-enables-malware-infect-entire-internet-1545687)
I do not know the "International Business Times", maybe I should be ashamed regarding their awards on their "about page"..
I searched a bit before posting the link here though, well...

Anyway, they point at [http://dankaminsky.com/2016/02/20/skeleton/](http://dankaminsky.com/2016/02/20/skeleton/), most of the stuff is above my head, there is a newer post : [http://dankaminsky.com/2016/02/21/ghost/](http://dankaminsky.com/2016/02/21/ghost/)
If you look for "DNS bug" you find stuff back from 2008 or something, and very few things from the recent days : [https://googleonlinesecurity.blogspot.fr/2016/02/cve-2015-7547-glibc-getaddrinfo-stack.html](https://googleonlinesecurity.blogspot.fr/2016/02/cve-2015-7547-glibc-getaddrinfo-stack.html)

I'm surprised there are no more news in the usual things I read, so I'm not sure about what to think.

---

### Post by QDR06VV9 on 2016-02-25
Thanks  bapoumba for the links..
Well I guess this should be the only good for now..
> On the plus side, although there are millions of DNS caches across  the internet, no researchers have yet to be able to get the glibc DNS  bug to work through caches, and therefore, Kaminsky says that only "some  networks are going to be vulnerable to some cache traversal attacks  sometimes".
However, he says that while this might not be an  immediate problem, if this flaw is not patched soon, it could become a  much bigger problem a year or two down the line.


Some talk awhile back about the net being too secure?
> There&#8217;s a level of maturity that can be brought to the table, and I  think should.  There are a lot of unanswered questions about the scope  of this flaw, and many others, that perhaps neither vendors nor  volunteer researchers are in the best position to answer.  We can do  better building the secure platforms of the future.  Let&#8217;s start here. 
This should get some folks worked up a bit!

---

