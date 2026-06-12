---
title: "googlebot trying to access aptdphutc.html"
date: 2011-04-09
forum: Security
---

### Post by wily_one on 2011-04-09
I've seen this in my apache2 error.log a couple of times now:
[error] [client 66.249.67.208] File does not exist: /var/www/aptdphutc.html


Since this is a Google crawler I'm not too concerned about it, but I do find it odd that a search for aptdphutc.html turns up nothing.

Anyone know what this is?

---

### Post by CharlesA on 2011-04-09
Make sure your site has no broken links.

---

### Post by wacky_sung on 2011-04-09
This can be a crawl done by malwares / email worms to your sites.

---

### Post by SeijiSensei on 2011-04-09
Is this a server on a static IP that you've maintained for quite a while?  If it's a dynamic IP, or an address you recently acquired, Google may still be spidering for content it found on that address before you obtained it.

---

### Post by wily_one on 2011-04-09
@wacky_sung, the address belongs to crawl-66-249-67-208.googlebot.com, which is why I said it was a Googlebot crawler.

@SeijiSensei, I suppose that's possible.  I am on dynamic, but my address has been stable for months.

I just find it odd that I come up with zero hits for "aptdphutc.html".  I even tried searching on Bing and Yahoo.  If no one has ever had such a page, why is the Google crawler trying to find it?

---

### Post by Doug S on 2011-04-10
Myself, I find googlebot to be a bit of an odd web crawler.
It does invent web page names with random characters, specifically to check what your server will respond with for a 404 (not found) type request.
Sometimes I have seen googlebot ask for the same random web pages 3 or 4 times over 3 or 4 days. I have also seen it ask for different random names from the same directory 4 or 5 times over 4 or 5 days.
 
I have also seen googlebot anticipate a possible web page. What do I mean? For example say I was posting some pictures with some sort of sequence numbers to the web pages, but I had deleted one picture because it was bad. I have seen googlebot actually create the missing sequence number and try it (although, I have not seen it for about 18 months now. I have more detail on this one at [http://www.smythies.com/~doug/googlebot.html](http://www.smythies.com/~doug/googlebot.html) )
 
Googlebot also has no sense of inheritance. What do I mean? If I use a robot metatag on an HTML page with NOFOLLOW. Googlebot will still crawl the child pages, and index them if they don't contain their own meta tag directives saying not to. The yahoo, slurp web crawler does have a sense of inheritance, as do most others.

---

### Post by SeijiSensei on 2011-04-10
> **Doug S said:**
> It does invent web page names with random characters, specifically to check what your server will respond with for a 404 (not found) type request.

That's probably what's happening here.  That's very informative, Doug.

---

### Post by wily_one on 2011-04-10
Yes, thanks Doug.

---

