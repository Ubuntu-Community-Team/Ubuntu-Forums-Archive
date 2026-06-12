---
title: "Why is my PC trying to connect to the BBC all the time? And what's Google doing?"
date: 2006-11-05
forum: Server Platforms
---

### Post by Pri0n on 2006-11-05
I installed EtherApe the other day, and interestingly enough, it appears that my PC is periodically trying to connect to newslb14.thdo.bbc.co.uk.  This is without any desktop applications (eg: web browser) running.

Given the nature of the site in question (the BBC), my first thought was that perhaps I had a "news ticker" application running in the background, but this isn't the case.

Anybody know why this is happening?:confused:  I'm not actively visiting BBC's web site, or have any news-related applications running.

I also discovered something interesting at Google with EtherApe.

If I go to google ([www.google.com](www.google.com)) and enter a web site in the search criteria (ex: cnn), upon retrieving the list of results, EtherApe responds a connection with google.com (naturally), as well as a connection with cnn.com even though I haven't actually gone to cnn.com's web site.

Wondering if this was some unique property of Google (perhaps for marketing purposes), I tried it on Alta Vista's search engine, and the behavior is different.  For Alta Vista, my computer doesn't automatically connect to the first site that is returned in the list of Google's search results.

Does anybody know what is going on in the background?  Is Google automatically establishing a connection between your computer and the first web site returned in a search criteria, even though you haven't clicked on the link yet?  Could it be passing the keyword(s) entered in your search criteria to the web site? (again, useful for marketing purposes) :-k

---

### Post by MJN on 2006-11-05
> **Pri0n said:**
> If I go to google ([www.google.com]("http://www.google.com")) and enter a web site in the search criteria (ex: cnn), upon retrieving the list of results, EtherApe responds a connection with google.com (naturally), as well as a connection with cnn.com even though I haven't actually gone to cnn.com's web site.

Sorry, can't help you with your BBC query however this last issue is down to 'link prefetching' between Google and your browser (presumably Mozilla-based) designed to speed up the subsequent loading of the 'top result':

[http://www.google.com/help/features.html#prefetch](http://www.google.com/help/features.html#prefetch)
[http://www.mozilla.org/projects/netlib/Link_Prefetching_FAQ.html](http://www.mozilla.org/projects/netlib/Link_Prefetching_FAQ.html)

Mathew

---

### Post by Pri0n on 2006-11-05
Thank you for the links MJN.

---

### Post by PhrankDaChickenGeek on 2006-11-05
Are you sure it's not the Live Bookmark in Firefox for BBC News? This rss feed is default in the toolbar

---

### Post by Pri0n on 2006-11-06
Would it do this even if you don't have the browser loaded up?

Either way, in Firefox I've gone into Edit | Preferences | Feeds, and changed it from "Live Bookmarks" to "No Application Selected" to see if it will stop this (although I wasn't subscribed to any feeds).

---

