---
title: "Scribus 1.4.8 on 20.04"
date: 2020-04-03
forum: Ubuntu Development Version
---

### Post by william_nbg on 2020-04-03
After upgrading to 20.04, I'm able to install 1.5.5, but not able to install the anything from the 1.4 series which I still need. I was just wondering if anyone knows why this? I've even downloaded the 'deb install file, but it won't install due to missing dependencies.

---

### Post by CelticWarrior on 2020-04-03
> **william_nbg said:**
> After upgrading to 20.04, I'm able to install 1.5.5, but not able to install the anything from the 1.4 series which I still need. I was just wondering if anyone knows why this?

You answered your own question:
> it won't install due to missing dependencies.

---

### Post by acheronuk on 2020-04-04
Scribus 1.4.x depends on Qt4. Qt4 has been removed from both Debian and Ubuntu.

[https://wiki.debian.org/Qt4Removal](https://wiki.debian.org/Qt4Removal)

---

### Post by dino99 on 2020-04-04
Some advices: [https://launchpad.net/~scribus/+archive/ubuntu/ppa](https://launchpad.net/~scribus/+archive/ubuntu/ppa)

---

### Post by acheronuk on 2020-04-04
> **dino99 said:**
> Some advices: [https://launchpad.net/~scribus/+archive/ubuntu/ppa](https://launchpad.net/~scribus/+archive/ubuntu/ppa)

There is no 1.4.x build for Focal in that ppa, and builds for earlier releases with Qt4 will not be installable on Focal.

@william_nbg why can't you use the 1.5.x branch?

---

### Post by william_nbg on 2020-04-04
Wow, thanks for all the info/feedback. I appreciate it.

**The problem was:** The 1.5 series was fine for flyers, posters (which I sometimes need), but If I tried to load a 200 page manuscript into it, things would slow to a crawl and eventually crash. Though, the old 1.4 series worked fine for typesetting books of any size.

After searching and reading up on the topic, I guess, I solved the issue. **Using 1.5.5** - If I unlink the text boxes between pages (instead of using page breaks) that don't need to be linked; chapters, front and back parts, etc ... It's working fine. The new text engine they built for the 1.5 series doesn't like 200 pages of text boxes linked together.

I have to change my work flow a bit, but it's probably a cleaner way to do it.

I'll go ahead and mark this as solved and hope it helps someone who has the same predicament.

---

