---
title: "Dansguardian Filtering issues"
date: 2013-05-16
forum: Server Platforms
---

### Post by umfunix on 2013-05-16
You might have noticed, but I need to establish a proxy server (Squid3) with filtering (Dansguardian) and a report genereator (SARG) on my network.  I have successfully installed and configured squid3 and dansguardian:  i get the access denied page when trying to access a p@rn site.  However, I found one of my clients browsing through p@rn images without going to these sites, by just opening [https://www.google.com](https://www.google.com), clicking on images and type in p@rn in the search field.  Images are then displayed in the google search.  Yes, he could not go to any of those sites, but he could se plenty of images.

I then went and changed the following files according to the recommendations in the files and on web sites:
etc/dansguardian/lists/urlregexplist
un-commented these 2 lines
"(^[http://](http://)[0-9a-z]+\.google\.[a-z]+[-/%.0-9a-z]*/images\?)(.*)(&?)(safe=[^&]*)"->"\1\2\3"
"(^[http://](http://)[0-9a-z]+\.google\.[a-z]+[-/%.0-9a-z]*/images\?)"->"\1safe=vss&"

etc/dansguardian/lists/bannedregexpurllist
Here I also uncommented the search engine options

etc/dansguardian/lists/pharaselists/pornography/banned
Here I commented out
#<google>,<&safe=off>
#<hl=en&safe=off&output=search>
<SafeSearch is off>

And still the client could see the p@rn images by just doing an image google search.

Please help where else should I change.

---

