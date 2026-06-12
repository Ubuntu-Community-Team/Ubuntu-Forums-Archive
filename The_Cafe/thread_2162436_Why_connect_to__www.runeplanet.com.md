---
title: "Why connect to  www.runeplanet.com?"
date: 2013-07-14
forum: The Cafe
---

### Post by vasa1 on 2013-07-14
I just noticed that opening a page at ubuntuforums.org involves connecting to "runeplanet.com". What's that about?

---

### Post by The Cog on 2013-07-14
I'm pretty sure it doesn't do that for me. I ran "watch lsof -i" in a command prompt while loading a forum page.

---

### Post by vasa1 on 2013-07-14
> **The Cog said:**
> I'm pretty sure it doesn't do that for me. I ran "watch lsof -i" in a command prompt while loading a forum page.
Please try this page: [http://ubuntuforums.org/search.php?do=getnew](http://ubuntuforums.org/search.php?do=getnew)

It may not appear on subsequent pages.

But this is what I see when I look at "open blockable items" in AdBlock Plus. I also saw it show up in the little status bubble that appears in the bottom left of pages in Firefox when a pages is loading or when the mouse cursor is over a link:

---

### Post by Erik1984 on 2013-07-14
It takes a script from there called vb.js NoScript blocks runeplanet here by default as I've not whitelisted it. I see no difference in appearance when allowing or disallowing the script.

---

### Post by vasa1 on 2013-07-14
> **Euroman said:**
> It takes a script from there called vb.js NoScript blocks runeplanet here by default as I've not whitelisted it. I see no difference in appearance when allowing or disallowing the script. This is de direct link to the script: [http://www.runeplanet.com/at/vb.js](http://www.runeplanet.com/at/vb.js)
Thanks for confirming. My question was *why* does this occur. As you can see from the image I put up, I've blocked it as well until I know more about why it's linked to ubuntuforums.org..

---

### Post by Erik1984 on 2013-07-14
-

---

### Post by The Cog on 2013-07-14
It's a script linked to in a post "Test" posted by DiegoTc in Honduras announcements.
I'm not that good with javascript, but I do see a function called "stealPassword()".
The script is [http://www.runeplanet.com/at/vb.js](http://www.runeplanet.com/at/vb.js)

---

### Post by The Cog on 2013-07-14
By the way,

Nice catch, vasa1.

---

### Post by vasa1 on 2013-07-14
> **The Cog said:**
> By the way,

Nice catch, vasa1.
Thank you! I don't know much about how these things work but isn't it a bit scary that a script in a post, a post I noticed but didn't open, is loaded?

---

### Post by Copper Bezel on 2013-07-14
Even if you don't have any kind of prefetching active in your browser, the first post in each thread visible on the page is loaded to create the tooltip preview of the post. I would have assumed that all happened serverside, though - I wouldn't think that the previews are being generated locally, which I'd think would mean moving around a lot more data than necessary.

The script wouldn't be running, of course, just called as part of the content of the post and then omitted from the preview.

---

### Post by vasa1 on 2013-07-14
> **Copper Bezel said:**
> Even if you don't have any kind of prefetching active in your browser, the first post in each thread visible on the page is loaded to create the tooltip preview of the post. I would have assumed that all happened serverside, though - I wouldn't think that the previews are being generated locally, which I'd think would mean moving around a lot more data than necessary.

The script wouldn't be running, of course, just called as part of the content of the post and then omitted from the preview.
Thanks! Yes, that was the first post (in a new thread) on the page and I didn't see the script appearing on other "internal" pages.

(I stopped bothering about prefetching after I got an "unlimited" internet account.)

---

### Post by coldraven on 2013-07-15
Ghostery tells me that it has blocked the "Facebook Connect" tracker on **this** page. What is that about?

---

### Post by vasa1 on 2013-07-15
> **coldraven said:**
> Ghostery tells me that it has blocked the "Facebook Connect" tracker on **this** page. What is that about?

Ubuntu Forums now has a Facebook page. Look at the top of the page for "Social Media". So that's legit. Whether you wish to block it or not is up to you.

---

### Post by sffvba[e0rt on 2013-07-15
> **vasa1 said:**
> Ubuntu Forums now has a Facebook page. Look at the top of the page for "Social Media". So that's legit. Whether you wish to block it or not is up to you.

+1 er like

404

---

