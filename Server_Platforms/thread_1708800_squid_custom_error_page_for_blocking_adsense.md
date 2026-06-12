---
title: "squid custom error page for blocking adsense"
date: 2011-03-17
forum: Server Platforms
---

### Post by bentong on 2011-03-17
Hi guys

please help if its possible with squid. currently, i am blocking adsense ads to save bandwidth but my problem is, i won't know if there are ads on a site as it only shows a blank white space.

what i wanted to do is block the adsense ads and replace it with a custom error message on its format so I will how many ads are there on the page and its positioning

many thanks

---

### Post by bentong on 2011-03-18
help please., i'm fairly new to administration.

something similar with safesquid, can someone kind enough to point me to the right direction.

thanks

---

### Post by SeijiSensei on 2011-03-18
I know how to change the custom error pages; they're stored in /usr/share/squid/errors/[language]/, I don't have a clue how you'd tie an error page to a particular ACL rule, though.  I'm not sure there is a way, and from the lack of responses to your query, I'm guessing no one else knows how to do this either.

There's a general error page for blocked content, ERR_ACCESS_DENIED, that you could use, but that will apply for all denials, not just ones related to AdSense.

By the way, if you're talking about "Google AdSense," aren't those all in plain text?  If so, they consume so little bandwidth compared to everything else on a site that blocking them is hardly worth the effort.

---

