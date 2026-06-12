---
title: "apt-get install git-all FAIL."
date: 2018-03-22
forum: Repositories &amp; Backports
---

### Post by Ronald_F._Guilmett on 2018-03-22
I was hoping to help out and hack together a small enhancement or two into one particular open source application, and then contribute my code changes.

The project in question is hosted on github.

I'm really not a git user, nor even a git fanboy.  So I'm kind of starting from scratch here, and just hoping to learn the ropes along the way.

As instructed by one web site, I took the first step by performing the following (while su'd to root... I don't waste time with prefixing everything with sudo) on my Ubuntu 16.04 LTS desktop system:

apt-get install git-all

Now, call me naive, but I kinda/sorta expected this to just work.  I mean, don't a few people DEPEND on this working??

Well, anyway, it didn't.  It crashed and burned with a bunch of errors I can't even begin to understand.  I am attaching just the tail end of the stuff that got printed to the relevant xterm window as this install attempt was finishing up.  (Everything prior to the very tail end of this log info seemed to complete successfully.)

Can anyone explain to me why merely attempting to install a pre-built binary for what would appear to be such a critical package (for software developers, at least) crashes and burns in such a horrible and (ultimately) perplexing way?

More to the point can anyone tell me how to get all of this git stuff installed despite whatever issues are causing all of these failures?


P.S.  I think I know now why I've managed to totally avoid using any of the git stuff for all these years.  Obviously it's WAY too complicated and elaborate for its own good.

---

