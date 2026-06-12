---
title: "Chrome bookmark items truncated/cut off"
date: 2013-03-29
forum: Ubuntu Development Version
---

### Post by x-shaney-x on 2013-03-29
Having messed up my 12.10 install I decided to install a 13.04 daily.
So far, the first issue I have noticed is that some of the bookmark toolbar items are cut off.

One just has the icon followed by "..." and my facebook one reads like "Facebo...".

I cannot see any reason for this as there is loads of space on the toolbar and it didn't do this in the 12.10 install.

Anyone else get the same issue?

---

### Post by mcellius on 2013-03-29
Is your screen at the same resolution under 13.04 as it was under 12.10?  And are the versions of Chrome the same?

---

### Post by x-shaney-x on 2013-03-30
> **mcellius said:**
> Is your screen at the same resolution under 13.04 as it was under 12.10?  And are the versions of Chrome the same?


Yes, same resolution and everything looks the same.  I did think it may be related to tweaks to the latest Ambiance theme but I have found the bookmark items are still cut off if I switch Chrome to its in-built "Classic" theme, even though the text on the bookmarks toolbar is smaller.
I have tried setting up my kids user account on this install and noticed the bookmark items on there are also cut off, even though it has just five bookmarks on it.

Chrome itself is the same version I was using in 12.10 also.

Alas, the problem will probably go unsolved for now as I'm finding 13.04 way too unstable and annoying for general use, which is suprising  as it's normally very solid at this stage and I am usually using the dev release as my daily driver by now...

---

### Post by Psychobudgie on 2013-03-30
I have the precise same issue here. Only occurs on 13.04 and does not occur with the same Chrome version in 12.10 so it seems to be something specific to Raring. Have had no luck in locating that which is the culprit but if I do I will let you know.

---

### Post by x-shaney-x on 2013-04-02
I've now noticed it also happens when running chrome in kubuntu 13.04

---

### Post by Frogs Hair on 2013-04-02
I found that if the edited bookmark is under five characters I see ab.... . If five or more  characters are used it appears normally -abcde .

---

### Post by x-shaney-x on 2013-04-02
Hmm, not in my case.  Facebook is cut but IMDb isn't.

---

### Post by John_Swing on 2013-04-03
I have the same problem, only for bookmarks folders though.

---

### Post by Frogs Hair on 2013-04-03
Part of last Chrome update had to do with the spell checker and I wonder if it is related some how. Since changing one bookmark I was able to add new ones with out problems. ??

---

### Post by Psychobudgie on 2013-04-12
It appears to be related to either spelling or capitalisation of some words. Facebook truncates while facebook with a lower case f does not. Similar result for b3ta. Have to assume it's related to a grammar check within the spell check code.

---

### Post by x-shaney-x on 2013-04-12
Strangely enough, there is no such problem running in gnome. I've tried different themes and fonts and keep getting the problem but it goes away with the default gnome theme and font.

---

### Post by Psychobudgie on 2013-04-12
Was the same here. Worked perfectly in gnome. But as I said, change the case of some words and they will truncate or not as the case me be (this pun was brought to you by...)

---

### Post by jerrylamos on 2013-04-12
Haven't run Ubuntu's Chrome/Chromium for a while.  Last time I did bookmarks were a bear - my Firefox bookmark list is over a couple hundred long which I edit frequently.

Google Chromebook browser handles bookmarks very well so far.  They appear as a tab, quick easy to select, full window, easy to scan, sort, and very long lines permitted.

---

### Post by Frogs Hair on 2013-04-12
I have since received a Chrome update and the book mark I changed on the last version has been returned to its original name without any problem. What ever the cause it's not a problem at the moment.

---

### Post by x-shaney-x on 2013-04-29
> **Frogs Hair said:**
> I have since received a Chrome update and the book mark I changed on the last version has been returned to its original name without any problem. What ever the cause it's not a problem at the moment.

Just done a fresh install of 13.04 final and installed Chrome and still getting the bookmarks problem :(

---

### Post by markbl on 2013-04-29
I have a fresh clean install of Ubuntu 13.04 release running gnome-shell and I see this now in Chrome (beta version).

---

### Post by asayler on 2013-05-04
I too am experiencing the bookmark truncation issues using Ubuntu 13.04 with Unity (upgraded from 12.10) and Chrome 26.0.1410.63. My "Trips" bookmark bar folder gets truncated to "Tri..." but folders like "Blogs" and "Accounts" are unaffected. "Travel" is unaffected, but "Trains" turns to "Tra...".

It's very strange.

I'm also having strange issue with the new Chrome spell check transposing words: [https://plus.google.com/u/0/104909300505732387997/posts/4M4ZGvork3c](https://plus.google.com/u/0/104909300505732387997/posts/4M4ZGvork3c). That also seems to be Chrome + Ubuntu specific, but was occurring on 12.10, not just 13.04.

[FONT=Ubuntu][COLOR=#303942]
[/COLOR][/FONT]

---

### Post by asayler on 2013-05-04
I also see the issue using google-chrome-beta instead of google-chrome-stable.

Upgraded to Version 27.0.1453.73 beta and no change.

---

### Post by gnumdk on 2013-05-21
> **asayler said:**
> I also see the issue using google-chrome-beta instead of google-chrome-stable.

Upgraded to Version 27.0.1453.73 beta and no change.


Not Ubuntu related, same bug on ArchLinux.

---

### Post by James_Nodws on 2013-08-14
Also in PCManFM's tabs, makes tabs useless

---

### Post by coffeecat on 2013-08-14
> This forum is for the discussion of the development of the next version of Ubuntu.

This thread was started when 13.04 was the development version. We are now into the 13.10 dev cycle.

Thread closed.

---

