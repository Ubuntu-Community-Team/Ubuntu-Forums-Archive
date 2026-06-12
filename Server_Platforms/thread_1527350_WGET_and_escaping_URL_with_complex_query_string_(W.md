---
title: "WGET and escaping URL with complex query string (Web server)"
date: 2010-07-09
forum: Server Platforms
---

### Post by tinonetic on 2010-07-09
Hi

I hope this is the right place to ask. Forgive me if it isn't.

There is a partnering website that provides an RSS feed to display on the website I am working on. The website displays information on the feed every time a user accesses the website. The feed changes almost every day.

For bandwidth considerations and speed, I would like to download the feed once by the server using a crontab job (my website is in a linux shared hosting environment).

The problem exists with the URL structure, which I have no control over. 

Here is the structure of the URL:

```

http://www.website.com/feeds/FastRSS?fql=and(meta.collection:or(zsses),zssc:zw,zssc:1,zssarchived:not(\'1\'),string("",+mode%3D"simpleall",annotation_class%3D"user"))&view=rwallsppublished&hits=25&offset=0&qtf_lemmatize=1&sortby=zsspubdate-rwpubdatedisplay&sortdirection=descending&collapseon=batvuigeneric1

```

This would be my WGET command that downloads,names and saves the feed as an xml file:

```

wget http://www.website.com/feeds/FastRSS?fql=and(meta.collection:or(zsses),zssc:zw,zssc:1,zssarchived:not(\'1\'),string("",+mode%3D"simpleall",annotation_class%3D"user"))&view=rwallsppublished&hits=25&offset=0&qtf_lemmatize=1&sortby=zsspubdate-rwpubdatedisplay&sortdirection=descending&collapseon=batvuigeneric1  -O /home/mywebsite/public_html/rssfeed.xml

```

I am aware that there are characters that need escaping and this is where I am getting my errors. 

I am also aware that I can avoid having to escape by enclosing the URL with single or double quotes. You will notice that the URL has BOTH single and double quotes, so its not as simple.(unless I escape those maybe? or if I can concatenate? How do I do that? )  I have done alot of reading on wget, but I cant seem to diagnose the problem. Any help on how I can structure the URL in a WGET-friendly way? I have seen a few similar enquiries and solutions. The closest to  my problem suggests using URL shortening services([http://www.webhostingtalk.com/archive/index.php/t-551248.html](http://www.webhostingtalk.com/archive/index.php/t-551248.html)), but I still think there is a smarter and more efficient way.

Sorry for the lengthy post

Thanks

---

### Post by CannibalZerg on 2010-07-12
If you have constant URL, just escape double quotes in URL with "\" and put URL in double quotes.

```

wget "http://www.website.com/feeds/FastRSS?fql=and(meta.collection:or(zsses),zssc:zw,zssc:1,zssarchived:not(\'1\'),string(\"\",+mode%3D\"simpleall\",annotation_class%3D\"user\"))&view=rwallsppublished&hits=25&offset=0&qtf_lemmatize=1&sortby=zsspubdate-rwpubdatedisplay&sortdirection=descending&collapseon=batvuigeneric1"  -O /home/mywebsite/public_html/rssfeed.xml

```

---

