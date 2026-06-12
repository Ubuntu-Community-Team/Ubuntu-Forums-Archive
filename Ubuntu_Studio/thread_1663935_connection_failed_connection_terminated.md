---
title: "connection failed: connection terminated"
date: 2011-01-10
forum: Ubuntu Studio
---

### Post by ericmo on 2011-01-10
I'm using Ubuntu Studio 10.04 with an HDA Intel soundcard. Often, my audio crashed while listening to music or playing flash movies, returning an error: "connection failed: connection terminated". 

Searching on several forums and websites, I found a simple solution: to upgrade ALSA to version 1.0.23, as explained in here: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

I just wanted to point out that now my audio has been working fine, in case someone is having the same problem.

---

### Post by AutoStatic on 2011-01-10
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/#comment-521](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/#comment-521)

Really, try installing the backports package first, upgrading ALSA the hard way like described on that blog should be your last resort.

Best,

Jeremy

---

### Post by ericmo on 2011-01-10
So, actually updating ALSA wasn't such a great idea. Apparently Dmix doesn't work quite right in ALSA 1.0.23, so I have to use PulseAudio if I want to play sound from more than one source.

---

