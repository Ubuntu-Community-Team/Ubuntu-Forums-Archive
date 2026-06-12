---
title: "Need help! A central repository for files?"
date: 2006-06-12
forum: The Cafe
---

### Post by naked on 2006-06-12
So I work on about 4 different computers all on different networks.  I'd like to have access to all of my files all the time.  I have working on a file at work, then throwing it on my website, going home and downloading it, working on it, and then re-uploading it so I can have access to it from my laptop while on the road.

If I am working with any file for more than I short time, it becomes difficult to know which copy of the document is the most recent.

What does everyone else do?  I've thought about having a USB memory stick, but I'd much rather have all my files online somewhere, accessible from anywhere.  

Hum, I guess my dream would be to have all of my files synchronized.  Anyone have any thoughts?

Luke

---

### Post by Patsoe on 2006-06-12
I started using bazaar for that sort of thing. It's meant for code developers really, but it can work well with anything that's text (not binaries like worddoc's). 

The package is in the main repo, called bzr.
Website is here: [www.bazaar-vcs.org](www.bazaar-vcs.org)

Nice things: you can "check out" files to your laptop, work on them without a connection to the main machine, then come back and load the changed version back up. It can also merge changes that you made in several copies of the same document and warns if there are problems with that. Oh, and I'd almost forget... it is really a revision control system, so the most important thing it does is keeping track of changes to your documents.

So, very powerful stuff. It takes some time to get to grips with it though (few days I guess), and sort of requires that you're a CLI guy :)


edit: oops, typo in the weblink :)

---

