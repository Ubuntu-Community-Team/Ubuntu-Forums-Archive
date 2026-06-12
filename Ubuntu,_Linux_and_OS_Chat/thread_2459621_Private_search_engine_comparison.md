---
title: "Private search engine comparison"
date: 2021-03-22
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2021-03-22
I rarely use Google these days. I use [Startpag]("https://www.startpage.com/")[e]("https://www.startpage.com/"). 
I was curious about the differences among the privacy respecting search engines so I did some research & found this >>> [https://www.startpage.com/privacy-please/privacy-advocate-articles/private-search-engine-comparison](https://www.startpage.com/privacy-please/privacy-advocate-articles/private-search-engine-comparison)

> **IP Address Protection:** When you visit Startpage, their servers change your IP address to 0.0.0.0 rather than logging any amount of your IP address. 

Now that's ^^ awesome. 

If you are looking for search engines that respect your privacy read that article.

---

### Post by DuckHook on 2021-03-22
@linuxyogi

You are taking to this privacy stuff like a fish takes to water! \\:D/

SearX is also excellent. Here's a link to a SearX gateway: [https://search.disroot.org/](https://search.disroot.org/)

You will have to make your own determination as to how trustworthy you feel disroot to be.

---

### Post by linuxyogi on 2021-03-23
> **DuckHook said:**
> @linuxyogi

You are taking to this privacy stuff like a fish takes to water! \\:D/

SearX is also excellent. Here's a link to a SearX gateway: [https://search.disroot.org/](https://search.disroot.org/)

You will have to make your own determination as to how trustworthy you feel disroot to be.

Didn't know about SearX. From the same article I linked they say :

> I won’t dive into SearX because it is best served as a self-hosted  search option that can be programmed to scrape results from any search  engine you please. Usually, **SearX is used by more advanced users or  people with a more serious [threat model]("https://www.startpage.com/privacy-please/privacy-advocate-articles/first-step-toward-privacy-design-threat-model")**.

I don't why they say its for "advanced users". I will just use it & try to find that myself.

Edit : The site is down
[ATTACH=CONFIG]288171[/ATTACH]
(Click to enlarge)

---

### Post by DuckHook on 2021-03-23
SearX is designed to allow self&#8209;hosting. This is probably what the author meant by "more serious threat model": when in doubt, it doesn't get any safer than hosting your own search engine. However, it is not necessary to host your own. Since SearX is a widely distributed and federated meta search engine, a number of entities already run such engines that are open for community use. I linked you to one of them.

The site you tried is not the official SearX site. Try the following link instead: [https://searx.github.io/searx/](https://searx.github.io/searx/)

This site contains a further link setting out a list of providers who run SearX instances: [https://searx.space/](https://searx.space/)

Note that you are entering the world of small providers. That carries its own form of risk. Some run such instances because they are idealists who believe in privacy and anonymity. Others do so for brownie points because they already run SearX for their own organization and see no problem extending this service to the public as part of their existing infrastructure. But I wouldn't be surprised to find the usual assortment of scumbags sprinkled among them who are phishing for unsuspecting marks.

I'm reasonably sure of Disroot's idealism, but that's very much my own opinion. Proceed cautiously all the same. Be doubly careful with referrals gleaned from some list posted online.

---

### Post by linuxyogi on 2021-03-23
> **DuckHook said:**
>  But I wouldn't be surprised to find the usual assortment of scumbags sprinkled among them who are phishing for unsuspecting marks. 

In that case I will just keep using Startpage. Which search engine do you use yourself ? Do you use SearX ?

---

### Post by T6&amp;sfpER35% on 2021-03-23
i've used Startpage previously but found it too slow to load,although i like that they give google search results .

I use duckduckgo now . Cant complain

---

### Post by DuckHook on 2021-03-23
> **linuxyogi said:**
> …Which search engine do you use yourself ? Do you use SearX ?
My main go-to is DuckDuckGo. I do use SearX as my secondary search engine when the results from DuckDuckGo feel insufficient, but only through that link I posted earlier. I trust Disroot not to skim my search results, but that's because I've gotten comfortable with their site maintainers through other interactions within that platform, primarily XMPP chat. They are a bunch of idealists who run their site for privacy/anonymity reasons and are supported by a nonprofit foundation. The maintainers have day jobs with understanding employers, but who knows how long such an arrangement can persist? If they shut down at some point, I will go looking for another gateway.

SearX is an excellent engine. Unlike the others, it's a metasearch engine, which is just a technospeak way of saying that it aggregates the results of other search engines while stripping inquiries of all identifying data. It also strips results of all ads, so this already means the elimination of one of the biggest threat vectors. How often have you used even DuckDuckGo or Startpage and inadvertently hit the first result which turns out to be an ad linked site with unknown fingerprinting practices? SearX is FOSS, tested and actually not too complex. I know of a few organizations that have set up their own instances and force all internal searches through it because, *provided it is set up properly*, it is safer.

Here are SearX's own views on running private instances: [https://searx.github.io/searx/user/own-instance.html](https://searx.github.io/searx/user/own-instance.html)

---

### Post by DuckHook on 2021-03-23
> **3nd said:**
> i've used Startpage previously but found it too slow to load
Interesting. I just tried it on my Brave instance and it loads quite quickly. No difference that I can sense between it and Google to be honest.
> I use duckduckgo now . Cant complain
Agree. 95% of the time, the results are more than satisfactory. When they aren't, there are plenty of one&#8209;off alternatives. I don't understand why so many are willing to sacrifice privacy for the sake of that remaining smidgen of search accuracy. I've also noticed that DDG will sometimes give *better* results than Google. I suspect this is because of Google's vested interest in promoting favoured sites versus DDG's fairer algorithms.

---

### Post by T6&amp;sfpER35% on 2021-03-24
> [COLOR=#000000]I just tried it on my Brave instance and it loads quite quickly[/COLOR]
yes , i gave it another shot and it seems to load faster than before .
think i'll stick with startpage for awhile and see how it goes.

---

### Post by DuckHook on 2021-03-24
> **3nd said:**
> …think i'll stick with startpage for awhile and see how it goes.
This just in: [https://www.theregister.com/2021/03/24/popular_privacy_extension_clearurls_removed/](https://www.theregister.com/2021/03/24/popular_privacy_extension_clearurls_removed/)

Further reasons (as if we needed more) to look at all things Google through lenses of scepticism.

---

### Post by DuckHook on 2021-03-31
For the past week, something has been nagging me about Startpage. Going through some of my old links turned up this: [https://restoreprivacy.com/startpage-system1-privacy-one-group/](https://restoreprivacy.com/startpage-system1-privacy-one-group/)

Perhaps a re&#8209;think and a greater measure of investigation is in order. I won't jump to the conclusion that they are evil, but accepting investments from an egregious data&#8209;profiler and installing their head honcho onto your board certainly smells awful.

---

### Post by makitso on 2021-04-01
I also use DDG but it uses Bing search which does not give good search results.

---

### Post by Frogs Hair on 2021-04-01
I started seeing unknown search providers showing up in startpage results thinking they were links regarding my query. When selected I found that it was another search engine with whole new set of links. Trying ecosia this week.   [https://info.ecosia.org/privacy](https://info.ecosia.org/privacy)

---

### Post by DuckHook on 2021-04-01
> **makitso said:**
> I also use DDG but it uses Bing search which does not give good search results.
You may wish to try SearX. I use it when DDG doesn't quite do the job. I've already referenced it in post [#7 above]("https://ubuntuforums.org/showthread.php?t=2459621&p=14027994#post14027994").

[list=1]
[*]You will first need to identify a gateway that you trust. This is probably the hardest part, as gateway providers tend to be little guys whose provenance is hard to research. An initial listing of such gateways is in the link in post #7.
[*]Once you've navigated to the gateway you want, it's easy to add it as a new search option to either FF or Brave. 
[*]In FF, while in the search page of the chosen SearX site, you just click on the three dots in the URL bar and select the option: "Add Search Engine". It should now show up as one of your search engine options in Preferences &#8594; Search. There you can make it your default if you wish.
[*]In Brave, once you've used the search page at least once, it will show up within Settings &#8594; Search Engine &#8594; Manage search engines. On my install, I had to mark it as "default" before it would shift from the accumulated selections at the bottom to one of the searchable ones at top. Even if you would prefer another engine as your default, you will need to declare the SearX gateway as the default to get it "registered" You can then change the default search engine to whatever you prefer afterward.
[/list]
I use the SearX gateway offered by Disroot, but only because I have satisfied myself via XMPP chat and getting to know them that these guys are legit and won't log my searches. I would ***not*** recommend them to anyone else on the basis of my own judgment. I firmly believe that we all need to do our own research on such matters.

It's always possible to run your own SearX gateway: it's a FOSS package available from the repos: ```
duckhook@Zeus:~$  apt show searx
Package: searx
Version: 0.16.0+dfsg1-2
Priority: optional
Section: universe/web
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Johannes 'josch' Schauer <josch@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 104 kB
Depends: python3-searx (= 0.16.0+dfsg1-2), python3:any
Suggests: nginx, uwsgi, uwsgi-plugin-python3
Homepage: https://asciimoo.github.io/searx/
Download-Size: 26.5 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: Privacy-respecting metasearch engine
 Searx is an internet metasearch engine which aggregates results from more than
 70 search services. Searx runs as a web service and provides a web interface
 that allows the user to do a general search (aggregating results from google,
 bing, yahoo) or search for files (piratebay, kickass, torrentz), images (bing,
 deviantart, google images, flickr), IT (github, stackoverflow, Arch Linux
 wiki), maps (OpenStreetMap, photon), music (youtube, spotify, soundcloud),
 news (bing news, google news, reddit), science (arxiv, wolframalpha) social
 media (digg, twitter) and videos (youtube, dailymotion, vimeo).
```
I've found that, as a metasearch engine, the results are excellent, since it agglomerates the results from many search engines (including Google, DDG and many others) thus providing the best of all of them. I might just switch from DDG to Disroot/SearX as my default.

One thing to be careful about: because it forwards your search query to other engines with the referrer tag, you may end up losing a certain amount of anonymity in the forwarding process.
> **Frogs Hair said:**
> I started seeing unknown search providers showing up in startpage results thinking they were links regarding my query. When selected I found that it was another search engine with whole new set of links. Trying ecosia this week.   [https://info.ecosia.org/privacy](https://info.ecosia.org/privacy)
I'm curious about Ecosia too. Will compare notes with you in a week!

---

### Post by dirtydog01 on 2021-12-09
DuckDuckGo is my #1

---

### Post by dirtydog01 on 2021-12-10
Disroot.org is new to me. Looks very interting.

---

