---
title: "Google's PageRank and changing websites"
date: 2008-01-07
forum: The Cafe
---

### Post by Ebuntor on 2008-01-07
Hi,

I was planning on helping some friends with their site, redesigning the layout and adding new content etc. 
They were worried about me changing anything because:
> Every page has a code that is linked to a ranking on Google. If you make any changes to the page the ranking changes. As I understand it Google's PageRank works by assigning every website a rank based upon links found on the pages. I'm not entirely sure what she means by "code" (the page's source code or the URL?) but could she be right? I thought that if you keep the same links on a page with the same URL it's ok.

If you'd lose your rank simply by making a few changes how could popular websites ever make any updates or improvements?

---

### Post by Ebuntor on 2008-01-07
*bump*

---

### Post by Lostincyberspace on 2008-01-07
It counts the links **to** the site not from the site and uses the meta tags to set what search terms it uses.

---

### Post by Ebuntor on 2008-01-07
> **Lostincyberspace said:**
> It counts the links **to** the site not from the site and uses the meta tags to set what search terms it uses.

Yeah, **to** the site, that's what I meant actually, sorry.

So if I understand correctly no matter what changes are made to the site it will maintain it's rank. Of course as long as other websites keep their links to this website.

And could the meta tags change if any changes are made to the content and if so could this negatively effect the search results?

---

### Post by edd07 on 2008-01-07
> **Ebuntor said:**
> 
And could the meta tags change if any changes are made to the content and if so could this negatively effect the search results?
I think you're safe. The meta tags are defined in the <head> section of the page, so changes to content won't alter them.

Hope this helps

---

### Post by Sam on 2008-01-07
It's a bit more complicated. Read [this](http://www.webworkshop.net/pagerank.html) !

---

### Post by Ebuntor on 2008-01-07
> **edd07 said:**
> I think you're safe. The meta tags are defined in the <head> section of the page, so changes to content won't alter them.

Hope this helps

Sure helps, thank you.

> **Sam said:**
> It's a bit more complicated. Read [this]("http://www.webworkshop.net/pagerank.html") !

Thanks, I found that same page a few minutes ago. Very clear the rank is totally unrelated to the page itself or it's content.

---

### Post by Lostincyberspace on 2008-01-07
Yes that pretty much sums it up.

---

### Post by PartisanEntity on 2008-01-07
Google offers a unique code snippet that a webmaster must add to pages he/she would like indexed. This code snippet should be maintained.

---

### Post by Ebuntor on 2008-01-07
> **PartisanEntity said:**
> Google offers a unique code snippet that a webmaster must add to pages he/she would like indexed. This code snippet should be maintained.

I thought there were only special pieces of code to **block** bots and that you'd always be automatically indexed.

[http://www.google.com/support/webmasters/bin/topic.py?topic=8459](http://www.google.com/support/webmasters/bin/topic.py?topic=8459)

---

### Post by koenn on 2008-01-07
> **PartisanEntity said:**
> Google offers a unique code snippet that a webmaster must add to pages he/she would like indexed. This code snippet should be maintained.

This code is to verify that you're the site owner, when you submit a sitemap. 
Google indexes pages by urls found in the sitemap, or by links from other pages.

---

### Post by Ebuntor on 2008-01-07
> **koenn said:**
> This code is to verify that you're the site owner, when you submit a sitemap. 
Google indexes pages by urls found in the sitemap, or by links from other pages.

I see, I've never heard about that, nor can I find on the Google website. Would it theoretically speaking just be a matter of copy-pasting such a piece of code?

I doubt those friends of mine used this for their site. As I understand it it isn't even really necessary.

---

### Post by boban on 2008-01-07
And another thing - PageRank is 10 years old. After publishing some initial (e.g. [this one)]("http://citeseer.ist.psu.edu/page98pagerank.html") papers Google went commercial. I think that nobody outside the company know what algorithm they are using now...

---

### Post by koenn on 2008-01-07
> **Ebuntor said:**
> I see, I've never heard about that, nor can I find on the Google website. Would it theoretically speaking just be a matter of copy-pasting such a piece of code?

I doubt those friends of mine used this for their site. As I understand it it isn't even really necessary.

[http://www.google.com/support/webmasters/bin/answer.py?answer=40318](http://www.google.com/support/webmasters/bin/answer.py?answer=40318)

when you want to use Google Webmaster Tools (such as submitting a sitemap), google gives you a unique code that you paste in the home page of the site.

---

### Post by Ebuntor on 2008-01-07
> **koenn said:**
> [http://www.google.com/support/webmasters/bin/answer.py?answer=40318](http://www.google.com/support/webmasters/bin/answer.py?answer=40318)

when you want to use Google Webmaster Tools (such as submitting a sitemap), google gives you a unique code that you paste in the home page of the site.

Great, thank you. :) 

I've got a much clearer picture of all the ranking and indexing stuff. Thanks everyone.

---

