---
title: "Search an entire state for homes - Is a Web Crawler the right way to go?"
date: 2014-04-16
forum: The Cafe
---

### Post by PopsTheSailor on 2014-04-16
I'm getting close to retiring and am going to move to Florida. I don't really care where, just to the state somewhere. Currently, there is no way I know of to search the entire state for homes. The best you can do is area by area. I don't know much about web crawlers but I was wondering if I could make one that would search each area for the type of home I want and then have all the results come back to me.

Is a web crawler the best thing to use for something like this?

Please don't recommend to me to just narrow down my search to specific areas. I could do that IF I WANTED TO but I DON'T. :)

---

### Post by bapoumba on 2014-04-16
Moved to Cafe, not a support request.

---

### Post by dbass81 on 2014-04-16
> **PopsTheSailor said:**
> I'm getting close to retiring and am going to move to Florida. I don't really care where, just to the state somewhere. Currently, there is no way I know of to search the entire state for homes. The best you can do is area by area. I don't know much about web crawlers but I was wondering if I could make one that would search each area for the type of home I want and then have all the results come back to me.

Is a web crawler the best thing to use for something like this?

Please don't recommend to me to just narrow down my search to specific areas. I could do that IF I WANTED TO but I DON'T. :)

My parents were thinking of moving to Florida, because the homes were so cheap.  Unfortunately distance played a big factor.  I think they used realtor.com a lot.  Easiest way to search is type in a city and state, e.g. tampa, fl, and a max price, like $20,000 and it will show you properties close to it.  There are also other sites such as zillow.com.  Good luck!

---

### Post by tux3do on 2014-04-16
This is a good idea if you have the time to make it. You could write a small crawler in Python, collect as much data as possible (text, images).
Then from this database of pages, you could extract terms such as price $, location etc - or simply browse by image :)

---

### Post by PopsTheSailor on 2014-04-16
I'm wondering if I don't really understand what a web crawler can do. I want to filter what comes back, not bring everything back and then filter. It would be MUCH LESS date to download. Is that possible? I just don't know anything about web crawlers.

---

### Post by Warpnow on 2014-04-22
You have to bring back the data to filter it...there's no magical way you can run an algorithm on data you don't have. Typically you capture the page as an XML and mine the xml for the data you want. If you don't know how to program at all, learning and getting this u to date could take weeks. 

...But no real need to use a web crawler for this...

Alot of these real estate sites have APIs which allow you direct access to their listing if you register with them as a developer. You can use the api to direct pull what you want. 

Just be aware that no matter what path you do gown is most likely to take you much, much longer than just going and searching every major city in florida.

---

