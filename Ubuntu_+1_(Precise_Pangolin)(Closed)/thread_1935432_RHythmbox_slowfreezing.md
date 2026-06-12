---
title: "RHythmbox slow/freezing"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by screaminj3sus on 2012-03-04
Does anyone notice rhythmbox in 12.04 is super slow? When I first open it (while it scans for changes) it goes totally unresponsive for like 10 seconds.

It also freezes for 5 seconds or so when I search the library. This seems even slower than banshee was.

---

### Post by screaminj3sus on 2012-03-04
Hmm, clean installed the beta again and it seems fine now.:p

---

### Post by John Coulthard on 2012-04-26
Same situation for me with 11.10. I have 13,109 songs in 1250 albums. ~/.local/share/rhythmbox/rhythmdb.xml is up to 9.2mb. Tried renaming it to .old and let Rhythmbox rebuild the file (I seem to remember having this problem before and this helping). It was brisk enough importing several thousand files then ground to a crawl and was consuming all the cpu.So restored the file and tried changing the preferences to not watch the library for new files. That didn't do any good either.

(later) Did a "complete removal" of Rhythmbox using the Synaptic Package Manager (This does not remove the above file) and then reinstalled it. That fixed the problem.

---

