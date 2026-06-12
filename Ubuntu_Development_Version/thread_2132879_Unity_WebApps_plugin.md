---
title: "Unity WebApps plugin"
date: 2013-04-06
forum: Ubuntu Development Version
---

### Post by zerubbabel on 2013-04-06
Suddenly, after installing the latest round up updates to Kubuntu 13.04, Chromium is nagging me with the message:
[INDENT]Unity WebApps plugin is required to display some elements on this page[/INDENT]
and when I click "install plug-in" it leads to a page about "unity-chromium-extension" version 2.4.4. I currently have version 2.4.6 installed (it was one of the updates installed this morning). So how can I get rid of this annoying message? It makes using Chromium very distracting.

---

### Post by Gavin77 on 2013-04-06
Try uninstalling the unity extension, it's only a suggested package for Chromium.  I'm pretty sure you can't use it on Kubuntu anyway if I'm not wrong.

---

### Post by zerubbabel on 2013-04-06
> **Gavin77 said:**
> Try uninstalling the unity extension, it's only a suggested package for Chromium.  I'm pretty sure you can't use it on Kubuntu anyway if I'm not wrong.

I tried that, but it makes no perceivable difference. Still get the nagging message.

---

### Post by zerubbabel on 2013-04-07
Am I the only one experiencing this?

---

### Post by zerubbabel on 2013-04-09
This message is driving me crazy. How can I get rid of it?

---

### Post by Psychobudgie on 2013-04-09
Use Chrome rather than Chromium. I get nothing but problems with Chromium for whatever reason, including the one you mention. No such nonsense with the latest Chrome.

---

### Post by zerubbabel on 2013-04-09
> **Psychobudgie said:**
> Use Chrome rather than Chromium. I get nothing but problems with Chromium for whatever reason, including the one you mention. No such nonsense with the latest Chrome.

Can I install Chrome without Google getting its tentacles into my computer, mining everything for fueling its advertising hints?

I would really prefer to stick with Chromium, but have it work as it did a week ago, before it began nagging me with the Unity WebApps plugin message. Surely there must be a way to satisfy that demand so that the message will go away.

---

### Post by jerrylamos on 2013-04-10
Don't know what these webaps do, how much space they take, how much in line code (slowdown) they do, have not felt motivated to investigate.

First thing I do on an install (frequently on U+1!) boot up Firefox and turn off the extensions as far as I'm able, also set "privacy" to "don't record" as much as I know how to do.

I'm getting a flood of targeted marketing and spam as it is.  I've seen than Canonical wants to watch what I'm doing to presumably input to their design.  Not obvious to me Canonical is listening to it's users as well as Linuxmint does.  I "put up with" unity because I test whatever Canonical throws over the fence with a rock tied to it.  On occasion I fire up Meerkat.  Amazing how fast, quick, and easy it is to do the things I do.

I try other linux's from time to time winding up on ubuntu U+1,  Do note that for browsing only, my slowest pc is a Chromebook Acer C1 which for booting and browsing is blazing faster and easier than unity.  So far it won't do offline office write and spreadsheets, and I don't know how to manage local files yet.  These are ubuntu strengths.

BTW, I'm not into "clouds" where Canonical and Google want to get my personal data up where I think targeted marketers can get at it, let alone hackers & spamers.

So how much "spying" are these Unity Webapps doing?  I assume plenty without solid information to the contrary.

---

### Post by jinjorge on 2013-04-10
just recently started running into this issue. at first not that big a deal, but now it's become a pain in the rear.  I have tried installing the plugin to no avail......

---

### Post by zerubbabel on 2013-04-11
I found that I can eliminate the nagging message by disabling the extensions in the Chromium settings, but that doesn't explain why the message appears while the extensions are enabled.

---

### Post by PVversion666 on 2013-04-21
> **zerubbabel said:**
> Am I the only one experiencing this?

I'm experiencing it as well. I hope it's fixed soon. It is very annoying.

---

### Post by Rob Sayer on 2013-04-21
> **jerrylamos said:**
> ... I'm getting a flood of targeted marketing and spam as it is.  I've seen than Canonical wants to watch what I'm doing to presumably input to their design.

That's one reason I use kubuntu.

> Not obvious to me Canonical is listening to it's users as well as Linuxmint does.

I'm not sure I agree with that 100%.  I was using mint 13 kde on my netbook for a while.  I went back to kubuntu because mint tech support is *terrible* compared to ubuntu's.

---

### Post by kuvanito on 2013-04-21
> **zerubbabel said:**
> This message is driving me crazy. How can I get rid of it?

1-get rid of chromium to begin with
2-open dconf editor and find webapps and disable intergation-allowed

---

### Post by cariboo on 2013-04-21
> **jerrylamos said:**
> Don't know what these webaps do, how much space they take, how much in line code (slowdown) they do, have not felt motivated to investigate.

First thing I do on an install (frequently on U+1!) boot up Firefox and turn off the extensions as far as I'm able, also set "privacy" to "don't record" as much as I know how to do.

I'm getting a flood of targeted marketing and spam as it is.  I've seen than Canonical wants to watch what I'm doing to presumably input to their design.  Not obvious to me Canonical is listening to it's users as well as Linuxmint does.  I "put up with" unity because I test whatever Canonical throws over the fence with a rock tied to it.  On occasion I fire up Meerkat.  Amazing how fast, quick, and easy it is to do the things I do.

I try other linux's from time to time winding up on ubuntu U+1,  Do note that for browsing only, my slowest pc is a Chromebook Acer C1 which for booting and browsing is blazing faster and easier than unity.  So far it won't do offline office write and spreadsheets, and I don't know how to manage local files yet.  These are ubuntu strengths.

BTW, I'm not into "clouds" where Canonical and Google want to get my personal data up where I think targeted marketers can get at it, let alone hackers & spamers.

So how much "spying" are these Unity Webapps doing?  I assume plenty without solid information to the contrary.

Most of what you have posted here, is pure out and out FUD. If you really wanted to find out what was being sent to Canonical's servers all it takes is installing Wireshark, and monitoring your network connection while using some of the services provided in the Dash.

I know it's easy to speculate, especially when you aren't even sure what your computer system is doing, but it is starting to get tiring, and unless you have proof of what you are saying, I personally wish you would stop trying to spread any more FUD.

---

