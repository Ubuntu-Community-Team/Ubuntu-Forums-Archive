---
title: "Threaded browsers"
date: 2009-07-20
forum: The Cafe
---

### Post by lukeiamyourfather on 2009-07-20
Firefox has been getting on my nerves lately performance wise. For example opening a new tab and page will cause a video in another browser window to stop playing for a fraction of a second. A dozen or two tabs and everything starts to drag with delays after clicking and random stuttering. Several dozen tabs and its a miserable and sluggish experience.

The performance tweaks of Firefox 3.5 are impressive but it still feels lacking and its not a hardware thing (8 cores at 2.1GHz, 16GB memory). After doing some research I've found out Firefox is a single threaded application (not what I was expecting), even if there are multiple browser windows and tabs they all are a single process without threads. Other modern browsers like Chrome and Internet Explorer 8 run a separate process for each browser or maybe even tab from what I understand. Seems like this would make multiple tabs and browser windows much more manageable and responsive, no?

Are there plans for multiple threads or processes in Firefox's future? Five years ago I didn't care if anything was threaded. Funny how times change. Cheers!

EDIT: More direction question is why Firefox doesn't already take advantage of multiple processors or cores? Seems like an important thing.

---

### Post by Arup on 2009-07-20
I would say Swiftfox is more CPU optimized, give that a try.

---

### Post by cdekter on 2009-07-20
> **lukeiamyourfather said:**
> After doing some research I've found out Firefox is a single threaded application (not what I was expecting), even if there are multiple browser windows and tabs they all are a single process without threads.

Not sure where you found this information, but there's no way on earth that Firefox runs in a single thread - otherwise the entire GUI would freeze up whenever the program is waiting on data from a web site. GUI apps always run in multiple threads, and Firefox probably runs each tab in its own thread (in addition to other threads dedicated to other tasks).

---

### Post by apoth on 2009-07-20
> **cdekter said:**
> Not sure where you found this information, but there's no way on earth that Firefox runs in a single thread - otherwise the entire GUI would freeze up whenever the program is waiting on data from a web site. GUI apps always run in multiple threads, and Firefox probably runs each tab in its own thread (in addition to other threads dedicated to other tasks).

I believe the JS engine is single threaded.

---

### Post by Mohamedzv2 on 2009-07-20
Actually, Mozilla is already trying to incorporate each tab as it's own process. I can't remember the name of it, but it's in the works.

---

### Post by Sand &amp; Mercury on 2009-07-20
Yeah, Firefox is not single-threaded, but it does run in a single process, unlike Chrome. 

Last I heard was that Mozilla is experimenting with multi-process browsing and will probably be incorporating it in a future release. It's a huge thing to implement though, so it may be a bit further down the line. If you're after a multi-process browser, Chrome appears to be just a few months from getting out the door.

---

### Post by SunnyRabbiera on 2009-07-20
> **lukeiamyourfather said:**
> Other modern browsers like Chrome and Internet Explorer 8 run a separate process for each browser or maybe even tab from what I understand.

How the crap does IE8 classify as a "modern browser"?
Its the same thing as IE7 witch in turn is the same crap as IE6.
IE8 is IE6 will more bells and whistles but the same basic flaws.

---

### Post by Sand &amp; Mercury on 2009-07-20
> **SunnyRabbiera said:**
> How the crap does IE8 classify as a "modern browser"?
Its the same thing as IE7 witch in turn is the same crap as IE6.
IE8 is IE6 will more bells and whistles but the same basic flaws.
What a *gloriously enlightening post*

---

### Post by lukeiamyourfather on 2009-07-20
> **cdekter said:**
> Not sure where you found this information, but there's no way on earth that Firefox runs in a single thread - otherwise the entire GUI would freeze up whenever the program is waiting on data from a web site. GUI apps always run in multiple threads, and Firefox probably runs each tab in its own thread (in addition to other threads dedicated to other tasks).

Maybe threaded is the wrong word. Firefox doesn't seem to render anything in parallel. If it did then opening Gmail on an 8 core machine wouldn't cause other browser windows with streaming media to pause, and opening multiple pages at once in multiple browser windows wouldn't use just one core in the system. Semantics aside, I think you understand my question.

---

### Post by lukeiamyourfather on 2009-07-20
> **Mohamedzv2 said:**
> Actually, Mozilla is already trying to incorporate each tab as it's own process. I can't remember the name of it, but it's in the works.

Any information or links would be greatly appreciated if you still have them. Cheers!

---

