---
title: "A possible solution for Spotify freezing?"
date: 2013-01-12
forum: Ubuntu Development Version
---

### Post by xeizo on 2013-01-12
I've tried numerous methods but for some reason Spotify still freezes rapidly when playing music on Raring Ringtail. 

BUT, I got myself a hint from the Spotify forums where SuSe-Linux was discussed, featuring the same freezing issues. In SuSe:s case it was because of Spotify being linked to a wrong version of libopenssl1.  So I tried to install libopenssl on Raring, but there seemed to be no candidate but instead apt suggested that I should install libruby. I did.

And, to my astonishment, now I've been using Spotify for a couple of hours without issues. But why in the world should a missing libruby be the cause of all this freezing? I have absolutely no idea, but I'm glad that Spotify now seems to work alright.

Anyone with any idea of the mechanism behind this issue?

---

