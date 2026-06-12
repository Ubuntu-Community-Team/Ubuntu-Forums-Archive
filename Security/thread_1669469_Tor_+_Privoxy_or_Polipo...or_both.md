---
title: "Tor + Privoxy or Polipo...or both?"
date: 2011-01-17
forum: Security
---

### Post by endotherm on 2011-01-17
So I'm looking into tor again, and finding some changes in the recommended approaches. the [tor project]("https://www.torproject.org/docs/tor-doc-unix.html.en#polipo") now recommends the Polipo proxy, but the [Ubuntu community documentation ]("https://help.ubuntu.com/community/Tor")(which does not appear updated to reflect Maverick) still recommends Privoxy. 

I can see from the [Polipo faq]("http://www.pps.jussieu.fr/%7Ejch/software/polipo/faq.html") that the two can both be used together (clientApp -> Privoxy -> Polipo -> Tor), but I'm not finding a comparision on what either brings to the equation that the other lacks or why using both would be a boon. I don't particularly need local caching, and indeed that seems to have been a problem for polipo in past (see faq page "Is Polipo Secure"). will caching affect my choice dramatically? 

so what do you guys think?

---

### Post by bodhi.zazen on 2011-01-17
The tor project now advises polipo , they claim it has several advantages including speed and a local cache, but then they disable the cache for increased privacy.

I think it depends on what additional features you plan to use and how much you plan to tweak the settings.

I have been using privoxy for a long time and prefer the adblock with privoxy.

I personally do not notice a significant speed difference between polipo and privoxy.

See [http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR) for my impressions / suggestions.

---

### Post by endotherm on 2011-01-17
Thank you, that is very helpful.

---

