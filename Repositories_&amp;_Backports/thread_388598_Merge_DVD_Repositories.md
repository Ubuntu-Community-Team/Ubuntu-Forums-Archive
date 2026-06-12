---
title: "Merge DVD Repositories"
date: 2007-03-19
forum: Repositories &amp; Backports
---

### Post by Trepex on 2007-03-19
Hey Folks!

We are deploying Ubuntu on an offline network and so I downloaded Edgy as well as DVD versions of the updates, security patches, and the multiverse/universe/main/restricted repositories. I've already tested adding DVD Repositories and it worked beautifully, but now I would like to create a central offline update mirror.

How do I go about merging the DVDs, like for the packages.gz files? Is there an easy way, so that I can regroup everything? I assume that they were originally separated with debpartial although I didn't do it myself (grabbed the ISO images off of a site).

I searched quite a bit but the best I could find was a rather confusing conversation from 2002 which didn't seem to yield a solution.

Thanks in advance!

Trep

---

### Post by Trepex on 2007-03-20
Is it possible that apt-get might work? I've been googling to the edge of the internet looking for possibilities and it seems like this is ALMOST what I need, what with the 'packages' switch to rebuild those files.

I guess I'll have to muck around with it and try to stumble across a config that works?

Can anyone confirm or otherwise?

Trep

---

