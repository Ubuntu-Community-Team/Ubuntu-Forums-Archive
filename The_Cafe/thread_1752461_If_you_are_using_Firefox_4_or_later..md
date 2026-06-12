---
title: "If you are using Firefox 4 or later."
date: 2011-05-07
forum: The Cafe
---

### Post by mmix on 2011-05-07
Turn on disable online Tracking.
[http://pureinfotech.com/2011/03/28/how-to-disable-online-tracking-in-firefox-4-web-browser/](http://pureinfotech.com/2011/03/28/how-to-disable-online-tracking-in-firefox-4-web-browser/)

---

### Post by Throne777 on 2011-05-07
> **mmix said:**
> Turn on disable online Tracking.
[http://pureinfotech.com/2011/03/28/how-to-disable-online-tracking-in-firefox-4-web-browser/](http://pureinfotech.com/2011/03/28/how-to-disable-online-tracking-in-firefox-4-web-browser/)

It doesn't disable tracking. All it does it lets sites know you don't want to be tracked, it's up to them to listen to that request or not.

It's similar to walking around town with a shirt saying 'Please don't stalk me' on it.

---

### Post by Frogs Hair on 2011-05-07
> **Throne777 said:**
> It doesn't disable tracking. All it does it lets sites know you don't want to be tracked, it's up to them to listen to that request or not.

It's similar to walking around town with a shirt saying 'Please don't stalk me' on it.

True , I have that option enabled and Ghostery is still blocking up to for trackers most of the time .

---

### Post by NormanFLinux on 2011-05-07
Google helpfully asks if you want them to collect stats on your browsing.

No kidding!

Its none of their damned business to do that in their browser.

---

### Post by Throne777 on 2011-05-07
> **NormanFLinux said:**
> Google helpfully asks if you want them to collect stats on your browsing.

No kidding!

Its none of their damned business to do that in their browser.

A lot of programs do. Banshee (the media player) asks if it can collect usage data, for example.

Such things aren't sufficient conditions for super evil, Orwellian nightmares.

---

### Post by NormanFLinux on 2011-05-07
We can opt out to protect our privacy. I don't want some corporation tracking what sites I visit. It usually never is to just improve their product.

---

### Post by Lucradia on 2011-05-07
Wish Microsoft WGA would have an opt-out.

Also, had this checked since iI nstalled, since I knew it was one of the big features advertised when mozilla firefox 4 was advertised.

---

### Post by Throne777 on 2011-05-07
> **NormanFLinux said:**
> We can opt out to protect our privacy. I don't want some corporation tracking what sites I visit. It usually never is to just improve their product.

Depends. Anonymous tracking (which is almost certainly what Google would be doing with Chrome) can hardly be said to be 'tracking *you*'. If the data was personally identifiable (which, I believe, it isn't), then I'd agree with you. Otherwise, you're not protecting your privacy by opting out, because your privacy was never being violated in the first place.

---

### Post by tgalati4 on 2011-05-07
To solve the MS WGA issue, just don't install it.  I have one PC in the house with Windows and it has the ever-present one update to install:  WGA.  I just decline and move on.  I think WGA stands for "We Gonna Annoy".

---

### Post by Lucradia on 2011-05-07
> **tgalati4 said:**
> To solve the MS WGA issue, just don't install it.  I have one PC in the house with Windows and it has the ever-present one update to install:  WGA.  I just decline and move on.  I think WGA stands for "We Gonna Annoy".

WGA is also on when you activate your key, it's just a different kind.

---

### Post by Pogeymanz on 2011-05-07
I have it turned on, but I'm still 90% sure that website are just going to see that I don't want them stalking me, and they'll stalk harder because of it.

Still using my paranoid addons, Adblock+(EasyPrivacy list), NoScript, BetterPrivacy, Biscuit.

---

### Post by handy on 2011-05-07
Apart from the Firefox add-ons that I do trust to help protect my privacy. I also use Greasemonkey running the googlePrivacy script, which does more than GoogleSharing & the script has been viewed by thousands, so I trust it.

By setting network.http.sendRefererHeader in Firefox preferences (about:config) to zero, then whenever you visit a link from one site, the destination site doesn't know the original site you were referred from.

This in effect makes the Firefox add-on RefControl redundant.

Also, by setting network.prefetch-next to false it brings about the following:

Link prefetching is when a web page hints to the browser that certain pages are likely to be visited, so the browser downloads them immediately so they can be displayed immediately when the user requests it. This preference controls whether link prefetching is enabled.

I prefer this disabled personally, for a variety of reasons.

Here another quote, this time a post by tjwoosta on spiralinear.org:

> That has nothing to do with your browser giving away your location, they just trace your ip. Its usually not accurate because theyre just getting the location of your isp. If you use a proxy, tor for instance, they get the location of the exit nodes isp. Basically a whois lookup and they plot the address on a map.

Heres how that geolocation works in firefox by the way, if anyones interested.
		
[Quote]
How does it work?
When you visit a location-aware website, Firefox will ask you if you want to share your location.

If you consent, Firefox gathers information about nearby wireless access points and your computer’s IP address. Then Firefox sends this information to the default geolocation service provider, Google Location Services, to get an estimate of your location. That location estimate is then shared with the requesting website.

If you say that you do not consent, Firefox will not do anything.
	
So the browser is able to access your wireless device and perform an access point scan? Thats kinda scary..

Other then that I think websites can usually only determine your general location using your service providers address. Also your locale which is in your useragent. [/quote]

I also have changed my useragent string in Firefox by adding the following to the about:config 

generaluseragentoverride

& a string that I've chosen from here:

[http://www.useragentstring.com/pages/useragentstring.php](http://www.useragentstring.com/pages/useragentstring.php)

Which makes my machine look to be a windows machine running IE & such.

There is all this stuff & some more for anyone interested in this thread:

[http://spiralinear.org/forum/viewtopic.php?f=17&t=243](http://spiralinear.org/forum/viewtopic.php?f=17&t=243)

---

### Post by Allavona on 2011-05-08
I use the TRACKMENOT add-on in Firefox. It simply slams Google with dozens of search request every minute or so. Sorta like how a slight-of-hand street magician distracts you so you don't pay any attention to what he's doing with his hands. The slowdown is negligible and I no longer see googleanalytics show up.

Beef TACO is a great add-on as well. Targeted Advertising Cookie Opt-out. Redirect Remover,  Ad Block+extentions, are all good to use.

But no matter what browser you use, and Firefox remains the Champion, you will in some way be tracked. Hell, you can't even go the the store and buy anything without them wanting all your info! I've got more filters in Thunderbird than all the coffee houses throughout the world!

Of course, one could always proxy....

---

### Post by Throne777 on 2011-05-08
> **Allavona said:**
> I use the TRACKMENOT add-on in Firefox. It simply slams Google with dozens of search request every minute or so. Sorta like how a slight-of-hand street magician distracts you so you don't pay any attention to what he's doing with his hands. The slowdown is negligible and I no longer see googleanalytics show up.


It's the worst strategy ever. It's like being pulled over by the cop and when asked 'Do you know how fast you were going?' replying with:
'I like unicorns. I don't like the band The Police, I hope you don't mind. I want to look at doves in my spare time. Did you know that the acronym NHS stands for National Health Service? I was going over the speed limit, officer. I hope to get a nice, shiny new bike for Christmas. My old pencil case was blue with a picture of a dinosaur on it'.

---

