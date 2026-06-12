---
title: "Favorite webkit browser for Linux?"
date: 2009-04-24
forum: The Cafe
---

### Post by mmace1 on 2009-04-24
In case you're wondering why - Gecko-based browsers (Firefox & the like) don't work on many, *many* E. Asian sites, nor does WINE-hacked IE6 always do the trick, seemingly KHTML doesn't do so great either, nor Presto. 

Webkit seems to have the best luck thus far, so...What's your favorite Webkit browser that runs on Linux?

---

### Post by Daisuke_Aramaki on 2009-04-24
i still use Midori from time to time. But it is still a little bit buggy, and crashes quite often. Kazehakase also does the same. Fast, but crashes often

---

### Post by Skripka on 2009-04-24
Arora.

---

### Post by JK3mp on 2009-04-25
I usually use firefox but as far as webkit i use midori. Might check out arora...suprisingly never heard of it. :P

---

### Post by Rokurosv on 2009-04-25
Arora, it's fast and I think it's a promising browser

---

### Post by halovivek on 2009-04-25
what is mean by webkit and what is the difference between firefox and that one?
Dont blame me. New to this word.

---

### Post by Rokurosv on 2009-04-25
> **halovivek said:**
> what is mean by webkit and what is the difference between firefox and that one?
Dont blame me. New to this word.

Webkit is the name of a rendering engine, the one that reads the html code in websites and displays it on your computer. Firefox uses the Gecko engine. There are variations between engines, some stuff renders differently on different engines. Other engines are Presto, the one that opera uses, and Trident for Internet Explorer.

---

### Post by mmace1 on 2009-04-25
> **halovivek said:**
> what is mean by webkit and what is the difference between firefox and that one?
Dont blame me. New to this word.

Every web browser has a 'layout engine' that does the actual work of opening the webpage and making everything look the way it's suppose to. 

For example, web browsers Camino & Firefox, even though they are different browsers, they both use the same layout engine (in this case - Gecko), and thus open webpages about the same way.  

[http://en.wikipedia.org/wiki/Comparison_of_layout_engines]("http://en.wikipedia.org/wiki/Comparison_of_layout_engines")

So in terms of whether a website opens/works properly, all the mostly matters is the layout engine. 

So - I'm asking about web browsers that use the Webkit layout engine, as that engine tends to do the best on E. Asian sites (aside from the best one for them - the Trident layout engine, but that's only used for Internet Explorer, which isn't really available in Linux).

---

### Post by ubuntu27 on 2009-04-25
I always use Firefox (Gecko), but when I want to use Webkit, I use Epiphany.

You have to choose the correct package if you want Epiphany to use webkit instead of Gecko.

---

### Post by Giant Speck on 2009-04-25
Chromium, but I don't use it for everyday browsing, and I won't until it is in at least beta stage.

---

### Post by Orlsend on 2009-04-25
For webkit testing I use Midori.

---

### Post by phrostbyte on 2009-04-25
Arora :)

---

### Post by amitabhishek on 2009-04-25
> **mmace1 said:**
> In case you're wondering why - Gecko-based browsers (Firefox & the like) don't work on many, *many* E. Asian sites, nor does WINE-hacked IE6 always do the trick, seemingly KHTML doesn't do so great either, nor Presto. 

Webkit seems to have the best luck thus far, so...What's your favorite Webkit browser that runs on Linux?


Can you please give a few URLs of E. Asian sites so that I can know the degree of difference (in rendering) between browsers.

---

### Post by ubuntu27 on 2009-04-25
I went to Synaptic to install Epiphany with webkit, and behold! It is not there :confused:

So looks like There is no Epiphany-browser with webkit for Ubuntu 9.04 OR it is not available for 64-bit systems.

Can someone confirm this?

---

### Post by Giant Speck on 2009-04-25
> **ubuntu27 said:**
> I went to Synaptic to install Epiphany with webkit, and behold! It is not there :confused:

So looks like There is no Epiphany-browser with webkit for Ubuntu 9.04 OR it is not available for 64-bit systems.

Can someone confirm this?

Add the following to /etc/apt/sources.list:

```
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
```

Then run:

```
sudo apt-get update
sudo apt-get install epiphany-webkit
```

---

### Post by ubuntu27 on 2009-04-25
Thank you Giant Speck. :KS

---

### Post by kpkeerthi on 2009-04-25
Arora

---

### Post by mmace1 on 2009-04-25
> **amitabhishek said:**
> Can you please give a few URLs of E. Asian sites so that I can know the degree of difference (in rendering) between browsers.
[B]
South Korean sites:[/B] off the top of my head - 

[http://onlinetour.co.kr/](http://onlinetour.co.kr/)
Though it's in Korea - try to select your travel dates, amongst other errors

[http://www.daum.net/](http://www.daum.net/)
One of the top 5 Korean sites - can't login though

[http://flyasiana.com/english/](http://flyasiana.com/english/)
2nd largest airline in Korea - try to select departure/arrival cities

[http://eng.wooribank.com/](http://eng.wooribank.com/)
Large Korean bank - in addition to various errors, it needs security programs to install which are only compatible with IE6-7.  This is the norm for all S. Korean banking sites seemingly. 


Based on watching my best friend here try to use Firefox, and based on their feedback, I'd say at least 33% (more like 50%?) of websites have some major aspects unusable in Gecko.  I'll ask others though (I'm in S. Korea).  Though I never use IE otherwise, I no longer even attempt to use Firefox when trying any E. Asian sites.  Ubuntu is near useless to friends of mine who try it, as they have no effective web browser. 

My *very limited* experience with Chinese sites, mostly airlines, finds around 1/2 won't fully work with Gecko.   

I'm *assuming* Japanese sites would be the same, due to the similar cultures, and similar dominance of IE, though, I may have over-stepped saying "E. Asia", as I don't know for sure that is the case.  Additionally, I think I recall the few Taiwanese sites I used worked fine.  

I'll get you a better list in a bit once I talk to some people, but here's a start.

---

### Post by halovivek on 2009-04-25
> **mmace1 said:**
> [B]


My *very limited* experience with Chinese sites, mostly airlines, finds around 1/2 won't fully work with Gecko.   

I'm *assuming* Japanese sites would be the same, due to the similar cultures, and similar dominance of IE, though, I may have over-stepped saying "E. Asia", as I don't know for sure that is the case.  Additionally, I think I recall the few Taiwanese sites I used worked fine.  

I'll get you a better list in a bit once I talk to some people, but here's a start.

So if we want some website supports only IE like that. So can we use epiphany to view and browse the site. Am i right.

---

### Post by mmace1 on 2009-04-25
If the site only supports IE, that means it only supports the Trident rendeing engine.  And IE is the only browser to use that engine, so...

Maybe Eiphany will work (it can use either the Gnome or Webkit rendering engines), you'd have to test and see.

---

### Post by shuttleworthwannabe on 2009-04-25
> **ubuntu27 said:**
> I always use Firefox (Gecko), but when I want to use Webkit, I use Epiphany.

You have to choose the correct package if you want Epiphany to use webkit instead of Gecko.

care to share how you do this?

I tried installing the WebKit package for epiphany (using the PPA available), but the rendering is very poor and crashes a lot.

---

### Post by Tibuda on 2009-04-25
> **mmace1 said:**
> Maybe Eiphany will work (it can use either the Gnome or Webkit rendering engines), you'd have to test and see.

Gnome rendering engine? You can choose between Gecko and WebKit for Epiphany. But Epiphany WebKit is not stable yet.


> **shuttleworthwannabe said:**
> I tried installing the WebKit package for epiphany (using the PPA available), but the rendering is very poor and crashes a lot.
I can't see nothing wrong with the rendering, but it is not stable yet.

---

### Post by cb951303 on 2009-04-25
webkit in a firefox like GUI: [http://code.google.com/p/arora/](http://code.google.com/p/arora/)

---

### Post by chucky chuckaluck on 2009-04-25
arora and midori are pretty similar, but i get the sense that arora is a little further along and is faster, at least on my machine. i tried konqueror using webkit the other day and that pretty bad.


edit: cute polar bear > green whatever that thing is.

---

### Post by Giant Speck on 2009-04-25
I understand that Arora is supposed to have a Firefox-like interface, but is there a team out there actively working on an actual webkit port of Firefox?

---

### Post by dragos240 on 2009-04-25
> **mmace1 said:**
> In case you're wondering why - Gecko-based browsers (Firefox & the like) don't work on many, *many* E. Asian sites, nor does WINE-hacked IE6 always do the trick, seemingly KHTML doesn't do so great either, nor Presto. 

Webkit seems to have the best luck thus far, so...What's your favorite Webkit browser that runs on Linux?

Give me an example of a site please.

---

### Post by Skripka on 2009-04-25
> **chucky chuckaluck said:**
> arora and midori are pretty similar, but i get the sense that arora is a little further along and is faster, at least on my machine. i tried konqueror using webkit the other day and that pretty bad.


edit: cute polar bear > green whatever that thing is.

Yea, Midori does not even support internal ad proxies (such as privoxy) yet.

---

### Post by Spiritous on 2009-04-25
Firefox is awesome, Mainly because of the addons :)

---

### Post by mmace1 on 2009-04-25
> **dragos240 said:**
> Give me an example of a site please.

Someone asked this before, and I gave a quick reply on page 2 with some examples (though all from S. Korea specifically).

---

### Post by dragos240 on 2009-04-25
thank you.

---

### Post by billgoldberg on 2009-04-25
> **Giant Speck said:**
> Add the following to /etc/apt/sources.list:

```
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
```

Then run:

```
sudo apt-get update
sudo apt-get install epiphany-webkit
```

Just tried and it was a big disappointment.

It's slower than firefox and lags during scrolling.

---

### Post by chucky chuckaluck on 2009-04-25
> **billgoldberg said:**
> Just tried and it was a big disappointment.

It's slower than firefox and lags during scrolling.

but... but... i-it's got webkit!!!

---

### Post by Giant Speck on 2009-04-25
> **chucky chuckaluck said:**
> but... but... i-it's got webkit!!!

Sh-should we hang him or burn him at the stake?

---

### Post by chucky chuckaluck on 2009-04-25
mm! +1 for steak.

---

### Post by Mark76 on 2009-05-31
I seem to be getting less annoying pop ups from imageshack since I switched to Midori.

In fact.  I can't remember the last time I had one.

---

### Post by ghindo on 2009-05-31
I think in a few more releases, Midori will finally be mature enough for day-to-day browsing; at the moment, it's still a bit unstable and sparse of features, but it's still my favorite. :KS

---

### Post by infestor on 2009-10-24
Webkit really is a fantastic layout engine...so chromium would be my favorite on linux

---

