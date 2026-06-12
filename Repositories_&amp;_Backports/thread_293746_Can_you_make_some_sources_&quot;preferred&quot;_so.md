---
title: "Can you make some sources &quot;preferred&quot; sources?"
date: 2006-11-05
forum: Repositories &amp; Backports
---

### Post by Firli on 2006-11-05
I have access to local mirrors of the ubuntu packages, which cost me less download, cost the university here less money and cost the main ubuntu servers less upload if I use them.

Now I added them to my sources.list and they seem to be working fine. Only one thing, I don't know whether I'm using the ubuntu servers or the local mirror when I update though.

So erm, how do I know which source I am using?

---

### Post by ciscosurfer on 2006-11-05
If I understand your question correctly, you can place a pound sign (#) in front of the line you want to comment out thereby preventing that line from being read-in by apt.  For example, the first line below would be commented out (not read by apt) and the second line would be read-in and used```
#deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://ftp.osuosl.org/pub/ubuntu/ edgy main restricted universe multiverse
```There's also [the idea of apt-pinning that you can read about here]("http://jaqque.sbih.org/kplug/apt-pinning.html") (sort of like a preference selector).

---

### Post by Firli on 2006-11-10
Thanks (now why didn't I think of that?).

The pinning thingie is very interesting, though it would require some more research on my part. On the link they only use it to pick a version, but the apt-get man told me it's possible.

I'll go with the commenting for now :). And I'm going to look into the pinning later.

---

### Post by savohead on 2006-11-14
i didn't know about apt-pinning, it's simple and great!!! thanks!!

---

