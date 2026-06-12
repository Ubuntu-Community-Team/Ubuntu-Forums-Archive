---
title: "necessity of unstable packages in backports"
date: 2006-01-11
forum: Ubuntu Backports
---

### Post by aledin on 2006-01-11
Hello all,
in backports there are some unstable packages like eog (2.13.x) and gthumb (2.7.x). Is there realy necessary to backports unstable packages (as they are considered unstable versions by the developers)? Eog backported crashes easily, Gthumb backported has problems with directory full of images imported from a camera; then, I must pin stable version in /etc/apt/preferences, downgrade packages hoping that no other backport software will be bugged as them.

IMHO, think about that backported packages are often installed automatically by apt-get upgrade. It's not a better choice to backport stable versions and give links to debs of unstable ones?

Thanks

---

### Post by dolson on 2006-02-05
Just thought I'd bump this and state that I agree with you.

---

### Post by kanem on 2006-02-05
Some users want those newest versions. They were probably requested explicitly. Backports is supposed to be for the latest and greatest.

My suggestion is don't leave backports enabled. When you want something from backports, enable them, get what you want and then disable them. Why would you upgrade a bunch of other stuff that you don't need upgraded?

---

### Post by bluenova on 2006-05-04
Hmm, was just going to add backports, to get the lastest STABLE versions, think I'll change my mind now I've read this. Someone should add to the sticky post that backports contains unstable software.

---

### Post by jobezone on 2006-05-12
Or perhaps users should be guided to disable the backports repository once they upgrade the specific application they want upgraded.

---

