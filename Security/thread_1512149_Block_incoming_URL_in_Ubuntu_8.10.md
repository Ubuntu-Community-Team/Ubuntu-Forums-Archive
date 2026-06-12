---
title: "Block incoming URL in Ubuntu 8.10?"
date: 2010-06-17
forum: Security
---

### Post by spiritofelric on 2010-06-17
I'm trying to block an incoming URL.  My ISP is hijacking 404 pages and annoyingly changing the URL line in the browser and flashing all sorts of popup ads.  

I just need it for incoming URLs which my router doesn't seem to handle.  I'd prefer something packaged with Ubuntu 8.04, but anything simple will do.



I know in KDE I could edit the kdeglobals file with:
[COLOR=#111111][FONT=Courier][KDE URL Restrictions] 
rule_1=open,,,,http,www20.search.rogers.com,,false 
rule_count=1 [/FONT][/COLOR]

[COLOR=#111111][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Courier]thanks[/FONT][/COLOR]

---

### Post by mörgæs on 2010-06-17
Slightly off topic: Are you aware that 8.10 is unsupported?

---

### Post by bodhi.zazen on 2010-06-17
> **spiritofelric said:**
> I'm trying to block an incoming URL.  My ISP is hijacking 404 pages and annoyingly changing the URL line in the browser and flashing all sorts of popup ads.  

I just need it for incoming URLs which my router doesn't seem to handle.  I'd prefer something packaged with Ubuntu 8.1, but anything simple will do.



I know in KDE I could edit the kdeglobals file with:
[COLOR=#111111][FONT=Courier][KDE URL Restrictions] 
rule_1=open,,,,http,www20.search.rogers.com,,false 
rule_count=1 [/FONT][/COLOR]

[COLOR=#111111][FONT=Courier]thanks[/FONT][/COLOR]

Depending on how you wish to manage the problem ...

I suggest you try a few extensions to firefox , noscript may help.

You may try this :

[https://addons.mozilla.org/en-US/firefox/addon/7993/](https://addons.mozilla.org/en-US/firefox/addon/7993/)

It is for opendns , but you get the idea.

[http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/](http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/)

Otherwise you probably need to install a proxy, either squid or privoxy (provoyx is easier to configure IMO and adds adblocking and other goodies).

You might also just call your ip provider and ask them for the fix. Often ip providers have an options page.

---

### Post by spiritofelric on 2010-06-17
> **mörgæs said:**
> Slightly off topic: Are you aware that 8.10 is unsupported?

My bad... it's 8.04.  So used to my other laptop with 9.10 :P *confused*

---

### Post by spiritofelric on 2010-06-17
> **bodhi.zazen said:**
> I suggest you try a few extensions to firefox , noscript may help.
I tried a few variations of this, but it didn't lead to the URL not changing.


> 
[https://addons.mozilla.org/en-US/firefox/addon/7993/](https://addons.mozilla.org/en-US/firefox/addon/7993/)
It is for opendns , but you get the idea.
I was hoping for an all browser solution.  I gave this a try, but it only seems to work on outgoing searches.  The problem is that Rogers grabs any 404 error returned and overwrites the packet with their own data.


> 
[http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/](http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/)
Otherwise you probably need to install a proxy, either squid or privoxy (provoyx is easier to configure IMO and adds adblocking and other goodies).
I think i'll try this route.  I would like a method to absolutely block certain incoming URLs anyhow.  *twitches nervously at the thought of setting up a proxy server in Ubuntu*

> 
You might also just call your ip provider and ask them for the fix. Often ip providers have an options page.Unfortunately tried that :( ... I got the old... No, we're not hijacking 404 pages. *rolls eyes*

---

