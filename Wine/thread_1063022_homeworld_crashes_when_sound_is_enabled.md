---
title: "homeworld crashes when sound is enabled"
date: 2009-02-07
forum: Wine
---

### Post by donkyhotay on 2009-02-07
I've been trying to resolve this issue both on the winehq appdb and bugzilla with no success so I'm hoping maybe someone here will have an idea that hasn't been tried yet. As per the post when I try to launch homeworld it almost immediately crashes unless I disable the sound first. I have tried changing the sound emulation settings in winecfg and also tried using padsp along with the /dsoundCoop option but nothing changes. Has anyone gotten homeworld to run under wine recently (it was flawless for me about 2 years ago) with sound and if so how? Or has anyone encountered a similar issue with another game and if so how did they resolve that?

---

### Post by donkyhotay on 2009-02-08
I found that the problem is directly related to the kernel. Using kernel 2.6.22 or before works while using any later kernel causes the problem to occur. It's kind of annoying having to download and install the kernel package manually then reboot into the other kernel anytime I want to play but at least it works now.

---

