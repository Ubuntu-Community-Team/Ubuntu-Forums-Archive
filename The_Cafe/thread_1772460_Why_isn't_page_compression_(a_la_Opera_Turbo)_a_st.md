---
title: "Why isn't page compression (a la Opera Turbo) a standard?"
date: 2011-05-31
forum: The Cafe
---

### Post by ean5533 on 2011-05-31
A random question popped up into my head today. One of the Opera browser's key features is its "turbo" mode which is aimed at users with slow connections, where downloading the webpage itself is the bottleneck. For those who don't know, the main premise of Opera Turbo is that pages are first sent to Opera's servers and compressed before being sent to the user who requested the page. The user's browser (Opera) then decompresses the page before rendering it.

My question is, why isn't page compression a standard? If all browsers supported it, there would be no need for middle men (like Opera's servers) to do the compressing; it would just happen on the webserver.

It could easily be implemented as a backwards compatible feature. When a user requests a page from the webserver, there would just be another parameter added to the header showing what compression types were supported, and the webserver would pass back pre-compressed data. If that parameter wasn't passed, the webserver would know that the browser doesn't support compression and it would pass back uncompressed data. If the parameter was passed to a webserver that didn't support compression, the webserver would ignore it and it wouldn't matter.

It seems so easy from a high level perspective, but I know there are much smarter people than me who would've proposed this idea 100 times if it was actually a good idea. What is the barrier that I'm not seeing?

---

### Post by Paqman on 2011-05-31
> **ean5533 said:**
> 
My question is, why isn't page compression a standard? If all browsers supported it, there would be no need for middle men (like Opera's servers) to do the compressing; it would just happen on the webserver.


Why use compression then? Just optimise the actual site.

---

### Post by ean5533 on 2011-05-31
> **Paqman said:**
> Why use compression then? Just optimise the actual site.

By "optimizing the site" I assume you mean manual optimization by the website developers? Well, the answer is because that would require manual optimization by the website developers. Not everyone who makes websites are veterans, nor do they have the time for those types of optimizations. Page compression would be automatic, requiring zero time on the part of site developers.

Besides, even perfectly optimized pages can be compressed further.

---

### Post by forrestcupp on 2011-05-31
Back in the dial-up days, there was a lot of interest in page compression, and it seemed like it would be the next gen technology. Then DSL and broadband became widespread and nobody cared anymore.

---

### Post by 3Miro on 2011-05-31
A thought:

How sensitive to errors is compression. Most browsers will display partially broken sites, with compression, if part of the binary file gets lost, you may be unable to display the page at all.

---

### Post by ean5533 on 2011-05-31
> **forrestcupp said:**
> Back in the dial-up days, there was a lot of interest in page compression, and it seemed like it would be the next gen technology. Then DSL and broadband became widespread and nobody cared anymore.

Sounds about right. It wouldn't the first time people said "XYZ is the way of the future!", but then ABC came along and made XYZ completely irrelevant.

Although it's a bit ironic, as in this situation we've looped back to making XYZ relevant again. A large portion of internet viewers are now viewing pages via 3g cellphones, which still aren't really that fast. It's too bad page compression didn't catch on.

---

### Post by ean5533 on 2011-05-31
> **3Miro said:**
> A thought:

How sensitive to errors is compression. Most browsers will display partially broken sites, with compression, if part of the binary file gets lost, you may be unable to display the page at all.

Ah, that's an **excellent** point. Drop a few characters out of an HTML tag and the browser can usually still make a readable page. However, drop a few characters out of a compressed file and you can't even uncompress the damn thing. For any kind of unreliable connection, page compression would go horribly.

Good call.

---

### Post by Joe of loath on 2011-05-31
Also, resources are key. I run a busy forum on a cheap VPS, if each user were downloading highly compressed pages (forums aren't static, so each hit has to be compressed individually), the overheads would be massive.

Some forums allow gzip compression, however this isn't terribly resource intensive, as the pages aren't compress by a huge amount. Even 10% would make a difference in terms of overall bandwidth used.

---

### Post by krapp on 2011-05-31
No thanks. I'd prefer my browsing history not being stored in yet another place, in yet another party's hands.

Chrome/Chromium have pre-fetching enabled by default. No thank you.

---

### Post by Joe of loath on 2011-05-31
Prefetching != compression and tracking. Prefetching is done on the local end.

[http://en.wikipedia.org/wiki/Link_prefetching](http://en.wikipedia.org/wiki/Link_prefetching)

---

### Post by ean5533 on 2011-05-31
> **krapp said:**
> No thanks. I'd prefer my browsing history not being stored in yet another place, in yet another party's hands.
What exactly are you saying "no thanks" to? The idea I'm discussing would eliminate the middle man from Opera's model. There would be no other party.

> **krapp said:**
> Chrome/Chromium have pre-fetching enabled by default. No thank you.

As mentioned by someone else, pre-fetching is a completely different topic and really has nothing to do with what we're talking about.

---

### Post by Paqman on 2011-06-01
> **krapp said:**
> 
Chrome/Chromium have pre-fetching enabled by default. No thank you.

Only DNS pre-fetching AFAIK. How could that possibly be a bad thing? You can use any DNS you like, including one with ultra-paranoid privacy rules.

---

