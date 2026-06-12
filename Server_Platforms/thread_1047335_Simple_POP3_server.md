---
title: "Simple POP3 server"
date: 2009-01-22
forum: Server Platforms
---

### Post by pksings on 2009-01-22
I upgraded to 8.04 and courier-pop refused to authenticate. I tried all sorts of options over the last two or three months, yes,that long as I only get a few minutes here and there to work on it. I moved my primary email to Gmail since I could no longer collect from my own server.  Anyway, I removed courier, tried dovecot, much, much more difficult to configure. The developer's decscription said it's "easily configurable", it probably is to him, but not to me. Qpopper was next, nope. Back to courier, it worked before, removed all traces of it and re-installed it. It just would not take a known good password even after it passed the authcheck or authtest, whichever it was. So in Synaptic I did a search for Pop3 server and started down the list. The first one to work immediately after install wins.

The winner is....solid-pop3d. Congradulations and thank you whoever developed this and whoever packaged it. It works "out of the box". And I was able to collect all the emails sitting in my in-basket.

The other side of this is that Courier, Cyrus, Dovecot and a few others don't work "out of the box".  And labeling of them as "easy" or "easily configured" seemingly apply to the developers or someone who does it frequently. Somehow I doubt that is the intention. 

So the Linux model of lot's of packages and programs to meet different user's needs once again proves itself. There is someone out there who saw the need for a truly "easy" pop3 server, and met it. To those people I again would like to say, Thank you very much!

---

