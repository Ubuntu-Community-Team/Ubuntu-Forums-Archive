---
title: "Dansguardian not using urlregexplist filters"
date: 2013-03-07
forum: Ubuntu Christian Edition
---

### Post by Azrael84 on 2013-03-07
Hi,

I wanted to enforce google safe search and after some research found that I needed to put

    "safe=off"->""
    "(^[http://](http://)[a-z]*\.google\.[a-z]*/[a-z]*\?)"->"\1safe=vss&"

into the urlregexplist file. I did this then restarted `service dansguardian restart`, and even restarting the computer, but this does not seem to
have taken affect at all. I could still search for anything in google/googleimages. I can even type google.com/safe=off and this URL does not get 
modified. Is there some other setting telling dansguardian to ignore this file?

Everything else in dansguardian set up seems to be working just fine for me.

---

### Post by Azrael84 on 2013-03-07
I think I worked out that is not working because I am using google.co.uk it works for google.com or google.ca etc, but I don't know anything about regexp to rewrite an expression that would also match on .co.uk. Can anyone assist?

---

### Post by stlsaint on 2013-03-09
Have you tried adding "images.google.com" to your banned list?

---

### Post by davidkennedy85 on 2013-04-02
Azrael84, that's because all Google Searches go over https now. If you go to [http://www.google.com](http://www.google.com), then search for something, the address bar will change to [https://www.google.com/search?whatever+you+searched+for](https://www.google.com/search?whatever+you+searched+for). Regular expression matching does not work over https. See my post here for a better explanation: [http://ubuntuforums.org/showthread.php?t=2131780](http://ubuntuforums.org/showthread.php?t=2131780)

stlsaint, blocking images.google.com is no longer effective as Google no longer uses sub-domains (e.g. images.google.com, video.google.com) for any of its media searches.

You can block Google altogether. To do this, just add google.com to your bannedsiteslist.

---

### Post by Azrael84 on 2013-04-03
I use `google.co.uk` and there doesn't seem to be a problem there.  I also use

    (google)+.*(images|imghp)
    (google)+.*(tbm=isch)
    (images)+.*(google)

in the `bannedregexpurllist` to block google images, which seems to work reasonably well. With

    "safe=off"->""
    "(^[http://[a-z]*\.google\](http://[a-z]*\.google\).[\.a-z]*/[a-z]*\?)"->"\1safe=vss&"

enforcing the safe search in `urlregexplist`. 

I resorted to a blanket SSL block to stop encrypted searches etc.

---

### Post by Azrael84 on 2013-04-03
Also there is the option of just allowing nosslsearch.google.com.

---

### Post by davidkennedy85 on 2013-04-03
Thanks for pointing that out. It led me down an interesting avenue of research. Actually, turns out that Google Search forces https if you are signed into Google, either via Gmail or some other Google product. If you are not signed in, then it will allow you to use regular http. That goes for most Google top-level language domains (e.g. Google.es and Google.fr). See this article for more info: [http://googleblog.blogspot.com/2011/10/making-search-more-secure.html](http://googleblog.blogspot.com/2011/10/making-search-more-secure.html)

Oddly enough, if you are signed into google.com, that does not mean you are signed into google.co.uk - but if you are signed into google.co.uk, then you are also signed into google.com. What that means is you can be signed into google.com and still use regular http to search on google.co.uk. This is why I could never get normal http search to work in Chrome until now.

As for using a blanket SSL block, that is probably not a good idea if you ever do any banking, bill paying or shopping online. If you do, then you are vulnerable to a man-in-the-middle attack. Anyone who wanted to could get your credit card number, social security number, or whatever other information you transmit by intercepting your http traffic.

If you want to use the bannedregexpurllist to block Google Images or force safe search, there is apparently a way to allow Google services such as Gmail to use https while forcing Google Search to use http. Like you said, you could just allow nosslsearch.google.com. If you are an administrator on your network, you could also configure the DNS entry for [www.google.com]("http://www.google.com") to be a CNAME for nosslsearch.google.com. This article explains it pretty well: [http://support.google.com/websearch/answer/186669]("http://support.google.com/websearch/answer/186669?hl=en")

Again, thanks for pointing this out. I was headed down the road of blocking Google altogether. I may still do this, but hopefully one of these methods will work instead.

---

### Post by H.323 on 2013-09-03
Add the following to your bannedregexpurl file
(google.com){1,}.*(img|data:image)
(google)+.*(images|imghp)
(google)+.*(tbm=isch)
(images)+.*(google)
(google.com){1,}.*(imgurl)

Add the following to your urlregexplist file
"^https://www(.google.com.*$)"->"https://nosslsearch\1"

Happy browsing without google images.

---

