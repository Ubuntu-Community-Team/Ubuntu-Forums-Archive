---
title: "How can I make my own GPG key?"
date: 2006-11-03
forum: The Cafe
---

### Post by zachtib on 2006-11-03
I'm now running a repository for my open source project, Deluge

One person asked me where to download the GPG key for the repo,
and it occurred to me that I didn't have one, so how do i go
about making one? And then, what do I do with it / Where do I
put it?


On a related note, what's an easy method for hosting apt mirrors?

Currently, I have repo's on two servers, and so I manually update
each of them when I build a new release, but is there an easy way
I can automate this?

Thanks, 

zach

---

### Post by jpeddicord on 2006-11-03
```
gpg --gen-key
```This should get you started, and when it asks, pick **(1) DSA and Elgamal (default)**. Post that to your server (not sure on how to do this correctly, though) and then people can import keys and such.

---

