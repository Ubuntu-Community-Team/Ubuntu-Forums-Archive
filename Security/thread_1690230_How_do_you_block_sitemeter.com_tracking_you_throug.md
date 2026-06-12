---
title: "How do you block sitemeter.com tracking you through web sites?"
date: 2011-02-18
forum: Security
---

### Post by tron101386 on 2011-02-18
How do you block sitemeter.com from tracking you when you visit a web site that has this tracker installed on it? I'm hoping there is a way so it can't see me at all or at least my computer stats. It still sees me when I have all cookies turned off and deleted them. Interesting I had someone go to the website running windows 7 and zone alarm firewall and it didn't show much detail. It did show part of the IP address which is expected but running Ubuntu x64 with Firstarter firewall and all the firewall's security settings to the highest and it shows every info stat about my computer. So maybe it's a firewall issue? I just would like it if possible the dumb site to not be able to track me at all if possible. 

I guess that site has been in some hot water. [http://www.geeknewscentral.com/2007/04/02/betrayal-of-trust-is-sitemetercom-planting-3rd-party-cookie/](http://www.geeknewscentral.com/2007/04/02/betrayal-of-trust-is-sitemetercom-planting-3rd-party-cookie/)

---

### Post by handy on 2011-02-18
If you are using Firefox you could install the Greasemonkey add-on & perhaps someone has written a script to do what you require. You will need to search through all of the scripts that people have written to work with Greasemonkey.

That's the best I can do for you. :)

---

### Post by SeijiSensei on 2011-02-18
In Firefox, install the Adblock Plus add-on, then add the site to the black list.  You might also want to explore the Noscript add-on that controls Javascripts as well.

---

### Post by bodhi.zazen on 2011-02-18
> **tron101386 said:**
> How do you block sitemeter.com from tracking you when you visit a web site that has this tracker installed on it? I'm hoping there is a way so it can't see me at all or at least my computer stats. It still sees me when I have all cookies turned off and deleted them. Interesting I had someone go to the website running windows 7 and zone alarm firewall and it didn't show much detail. It did show part of the IP address which is expected but running Ubuntu x64 with Firstarter firewall and all the firewall's security settings to the highest and it shows every info stat about my computer. So maybe it's a firewall issue? I just would like it if possible the dumb site to not be able to track me at all if possible. 

I guess that site has been in some hot water. [http://www.geeknewscentral.com/2007/04/02/betrayal-of-trust-is-sitemetercom-planting-3rd-party-cookie/](http://www.geeknewscentral.com/2007/04/02/betrayal-of-trust-is-sitemetercom-planting-3rd-party-cookie/)

See this extension:

[https://addons.mozilla.org/en-US/firefox/addon/ghostery/](https://addons.mozilla.org/en-US/firefox/addon/ghostery/)

Additional tips : [http://bodhizazen.net/Tutorials/Privacy](http://bodhizazen.net/Tutorials/Privacy)

---

### Post by handy on 2011-02-18
My understanding is that ghostery has been bought by a company that we can't necessarily trust. After that happened I dumped ghostery & installed Greasemonkey & run the googlePrivacy script. 

The script works great, does a lot more than ghostery did, plus the script is there for all to review, so I trust it.

---

### Post by bodhi.zazen on 2011-02-21
> **handy said:**
> My understanding is that ghostery has been bought by a company that we can't necessarily trust. After that happened I dumped ghostery & installed Greasemonkey & run the googlePrivacy script. 

The script works great, does a lot more than ghostery did, plus the script is there for all to review, so I trust it.

But that google privacy script only runs on google (search pages) and is thus limited.

A better option is to use an alternate search engine :

[http://www.startpage.com/](http://www.startpage.com/)

Other options exist as well.

ghostery runs on all sites.

At any rate, there are a plethora of privacy extensions for firefox.

---

### Post by handy on 2011-02-21
I use Scroogle for searching anyway.
In combination with googlePrivacy script I run Adblock +, Beef Taco, BetterPrivacy & NoScript.

I think they were about as good as I could do, apart from some edits in about:config which helped make me harder to track.

***[edit:]** Oh yeh', the next post reminded me, I also have Firefox ask for my permission every time a site wants to set a cookie & have it remember my answer for all cookies on that site. On very rare occasions I delete my "block" setting for a site in Ff Preferences. Mostly my cookies are for sites where I have accounts of one kind or another about 50 all together, the other 1000+ in my "block" list are not needed by "me".  *

---

### Post by wacky_sung on 2011-02-21
Actually if you are using chromium with the setting below and you are kinda safe from those tracking cookies.

[IMG]http://i56.tinypic.com/f0waae.png[/IMG]

Beside that, running along with squid and privoxy will enhance your privacy as well.Not forgetting to use bleachbit as well.

---

### Post by handy on 2011-02-21
As mentioned in post_#7 above, this is what I do in Firefox about:config :

[i]By setting **network.http.sendRefererHeader** in Firefox preferences (about:config) to **zero**, then whenever you visit a link from one site, the destination site doesn't know the original site you were referred from.

This in effect makes the Firefox add-on "RefControl" redundant.

Also, by setting **network.prefetch-next** to **false** it brings about the following:

Link prefetching is when a web page hints to the browser that certain pages are likely to be visited, so the browser downloads them immediately so they can be displayed immediately when the user requests it. This preference controls whether link prefetching is enabled.

I prefer this disabled personally, for a variety of reasons. [/i]

I took the above from the following linked to page, there is some other info of associated interest in the short thread that it was lifted from:

[http://www.spiralinear.org/showthread.php?tid=243](http://www.spiralinear.org/showthread.php?tid=243)

---

### Post by handy on 2011-02-21
> **bodhi.zazen said:**
> But that google privacy script only runs on google (search pages) and is thus limited. 

My mistake. I haven't been into this stuff for some months & my old memory does botch it from time to time. :) I think the "g" & the "o" in ghostery had my brain connect it with google! Oh well.

From memory(?) the other add-ons I'm using allow me to cover what ghostery does (& more). I'm sure I looked pretty hard at what they & ghostery were capable of before dumping ghostery. & as previously mentioned, I think that Evidon the newish owners of ghostery are still using the data that they pick up from the online user's browser to gather general data that can be manipulated for the benefit of marketroids.

Of course I could just be, being slightly paranoid... ;)


On that note, I'll post a link to the Panopticlick site for the readers here that aren't familiar with it at this stage as it is educational about just what gets picked up from a user's browser:

[http://panopticlick.eff.org/](http://panopticlick.eff.org/)

---

