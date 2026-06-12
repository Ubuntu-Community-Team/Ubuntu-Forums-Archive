---
title: "[SOLVED] Security issue running cross-desktop managers?"
date: 2008-01-21
forum: Server Platforms
---

### Post by nfox on 2008-01-21
I saw it mentioned but never explained. I was wondering if it was a security issue to run KDM to run Flux or Gnome, etc. Any display manager running another desktop might be an issue.

I'd like some insight on what's happening because I would like Flux but to have KDE's panel and a few other things (since it's so much faster). 

It just seems like there could be some holes or failure to communicate between the coders.

---

### Post by HermanAB on 2008-01-22
You can mix and match and make your own Frankenstein desktop.  Sometimes, it is required to do that for special application reasons, but generally it is too much hassle to swim against the tide.  There is no security issue with it though.

Cheers,

Herman

---

### Post by nfox on 2008-01-22
I didn't think that would be a problem since I like most do it anyways.

When I was trying to figure out how to get XDM to be the default for my laptop, I gave up and stuck with KDM since it's the hotter sister of the other two. 

I read somewhere (would love to reference where...) that crossing the managers was a known security issue. Something about how I can have a KDE window open and the DCOP assignation is tailored for a KDE program handler however only Flux is running. So Flux instinctively handles the call however there's a chance that the receiver will miss/add data that would have been provided if they were the same type.

An example (of what I would assume) would be a KDE app that uses KWallet. Having Fluxbox running the program, where there is no KWallet equivalent, the application could leak the stored password or at least point a crafty snooper in the right direction.

What about that?

---

