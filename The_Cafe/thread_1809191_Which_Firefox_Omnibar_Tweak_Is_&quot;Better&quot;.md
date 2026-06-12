---
title: "Which Firefox Omnibar Tweak Is &quot;Better?&quot;"
date: 2011-07-21
forum: The Cafe
---

### Post by moore.bryan on 2011-07-21
Well, like many, I wanted Firefox's URL bar to act more like Chrome/Chromium's in that it will autocomplete bookmarks/historically visited sites *and* search from it. Now, those are two separate things, and the autocomplete feature can be enabled simply by altering the about:config a bit.

For the "omnibar" option, there are two main add-ons for this: [Foobar]("https://addons.mozilla.org/en-US/firefox/addon/foobar/") and [Omnibar]("https://addons.mozilla.org/en-US/firefox/addon/omnibar/"). Both are good, but I wondered if using an add-on wasn't overkill. Perhaps there could be an about:config fix for this too... and I was right.

So, here's my question for people who might know much more than I: which is the better option; that is, is it "better" to go with an extension or the about:config "hack?" I've been away from Firefox for a while and when I used to use it exclusively, too many extensions could really bog things down, so this may actually be moot now.

---

### Post by lovinglinux on 2011-07-21
There is also [AwesomeBar HD]("https://addons.mozilla.org/en-US/firefox/addon/prospector-awesomeBar-HD/") from Mozilla labs. It lacks customization, but looks promising. 

Personally, I prefer a power search tool like [Web Search Pro]("https://addons.mozilla.org/en-US/firefox/addon/web-search-pro/"), which does not integrate with the address bar, but offers categorization of add-ons with sub folders, Drag & DropZones (which is awesome), context search and automatically triggers the search when you select the engine.

---

### Post by moore.bryan on 2011-07-21
Thanks, lovinglinux, but like I wrote, I'm okay with Foobar/Omnibar and am just wondering if it makes more sense to use an extension or just keep to the about:config hack. Using an extension just seems like bringing a hatchet when a scalpel is needed.

---

### Post by lovinglinux on 2011-07-21
> **moore.bryan said:**
> Thanks, lovinglinux, but like I wrote, I'm okay with Foobar/Omnibar and am just wondering if it makes more sense to use an extension or just keep to the about:config hack. Using an extension just seems like bringing a hatchet when a scalpel is needed.

Well, I don't know how to do that via about:config. Is that really possible? Besides, those add-ons offer more customization options, that you can't achieve with simple preferences changes.

On a side note, I have more than 50 add-ons installed and FF works just fine. Too many add-ons can have a big impact on Firefox performance, but depends on the add-ons you use, what they do and how they are coded.

---

### Post by moore.bryan on 2011-07-21
> **lovinglinux said:**
> Well, I don't know how to do that via about:config. Is that really possible?
Yeah... I've been doing it since the very first Firefox. If you customize the navigation bar by removing the search box, you can enter about:config, search for "keyword.URL," and change the blank box to the search string for whichever search engine you want; I use [DuckDuckGo]("https://duckduckgo.com/"), mainly for their !bang syntax searches.

[quote=lovinglinux] Besides, those add-ons offer more customization options, that you can't achieve with simple preferences changes.[/quote]
True... I'm just not sure I need any of those changes.

[quote=lovinglinux]On a side note, I have more than 50 add-ons installed and FF works just fine. Too many add-ons can have a big impact on Firefox performance, but depends on the add-ons you use, what they do and how they are coded.[/QUOTE]
It would seem Firefox has comes leaps-and-bounds from the last I used it. I only used a handful of extensions, but they totally bogged it down.

---

### Post by lovinglinux on 2011-07-21
> **moore.bryan said:**
> Yeah... I've been doing it since the very first Firefox. If you customize the navigation bar by removing the search box, you can enter about:config, search for "keyword.URL," and change the blank box to the search string for whichever search engine you want; I use [DuckDuckGo]("https://duckduckgo.com/"), mainly for their !bang syntax searches.

Oh, I see. That is the "Search By Name" feature. Well, I use that, but it only gives you a single engine search. The add-ons you mentioned allow full integration with the search bar.

> **moore.bryan said:**
> It would seem Firefox has comes leaps-and-bounds from the last I used it. I only used a handful of extensions, but they totally bogged it down.

Well, the javascript engine evolved a lot. If you benchmark various versions of Firefox, you will see a huge difference between versions 3, 3.6, 4, 5, 6 and 7. That has a big impact on extensions performance. For instance, I develop an extension that has a different code for Firefox versions below 4, because otherwise the extension performs really slow.

---

### Post by moore.bryan on 2011-07-21
> **lovinglinux said:**
> ... it only gives you a single engine search.
Yup... all I need, though, with DDG.

[quote=lovinglinux]Well, the javascript engine evolved a lot. If you benchmark various versions of Firefox, you will see a huge difference between versions 3, 3.6, 4, 5, 6 and 7. That has a big impact on extensions performance. For instance, I develop an extension that has a different code for Firefox versions below 4, because otherwise the extension performs really slow.[/QUOTE]
I've been noticing that. I was on Opera and then Chromium for the longest time because Firefox just became too "bloated;" now, I think I may be back.

---

