---
title: "Broken Latex installation after atempted upgrade"
date: 2018-10-02
forum: Ubuntu/Debian BASED
---

### Post by Daneel.Olivaw on 2018-10-02
I'm on elementary OS 0.4.1 Loki (Built on "Ubuntu 16.04.5 LTS"). 

I tried to update my latex installation by adding [Jonathon F]("https://launchpad.net/~jonathonf/+archive/ubuntu/texlive") PPA, but it didn't work (I left mi PC updating the 1.6gbs via Software Centre and when I came back it was cancelled with no error). Now I seem to have left with a broken installation. After purging that PPA I could not install texlive-full:

```

The following information may help to resolve the situation:

The following packages have unmet dependencies:
 texlive-full : Depends: purifyeps but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Using aptitude didn't work either. No solution involved installing texlive-full.

I could install texlive-base but the software I use for compiling (R) throws me an error and I cannot compile files manually. I seem to be in some dependency hell (or limbo). How should I do a clean installation of the latest possible version of Latex (I had encountered a problem that some users resolved by updating)? 

Thanks!

---

