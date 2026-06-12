---
title: "A CS major's experience of 3 months"
date: 2007-05-22
forum: Testimonials &amp; Experiences
---

### Post by Cappy on 2007-05-22
I've been using Ubuntu for around 3 months now. I stopped using XP about a month after I tried Ubuntu. I had tried Ubuntu a couple of years ago but I couldn't ever get my programs to share the sound and I gave up. It was probably because I used a USB headset at the time. I'm still not sure if they are supported now since I have a really cheap Audigy 4 now.

I've found Ubuntu to be VERY good OS. More so than XP because I now have control over everything I WANT to have control over. It took me a couple of weeks to adjust to the differentness of Linux and get everything working.

Here is my list of things Ubuntu could improve on:

---

(Common complaint)
**Documentation.** There needs to be a page of documentation of very common common problems in Ubuntu. Problems such as "my video drivers stopped working", "X won't start", "grub gives an error", "how to change my undetected screen resolution". The CORRECT ways to do these things are documented but they are scattered around and not easily accessible, especially if you don't even know the terms for what the problem is. This is a long standing argument against Linux that is unfortunately still true.


(Another common complaint)
**64-bit.** Yes, 64-bit works well but not as easily as 32-bit. A lot of people badmouth 64-bit because they can't get a program to work and they are too lazy to goto packages.ubuntu.com to download the one package they need for some proprietary program. Not a problem for me but I'm tired of people saying "don't go with 64-bit it is a lot harder!". Clearly, there needs to be a way for ubuntu to automatically be able to get 32-bit packages. This has been going on since the 64-bit OS was created, everyone knows it is there, I don't know why I bother even mentioning it.


(Uncommon complaint)
**Package Dependencies.** If a program errors out with "needs blahblah.so.2" I think it would be fantastic if Ubuntu would download it automatically. I had trouble with this at first, before I found out I could "apt-cache search xxx" and find it myself.** I think this should be a priority on the next Ubuntu version!** This could also be the method to implement the automatic downloading of 32-bit packages for 32-bit programs running on a 64-bit OS (as described above). I've always thought the debian package manager is probably one of the most compelling reasons to use Linux in the first place. There would need to be an option that could turned this feature off for security reasons.

**What I especially love:** I love the newest Ubuntu with automatic video card driver installation (even though I ended up installing the newest nvidia ones anyway) and automatic codec installation. "sudo apt-get install nvidia-glx-new" to upgrade to the nvidia drivers honestly kicks MAJOR azz.

I'm glad Ubuntu has made it a lot easier to transition completely to Linux from Windows =)

---

### Post by lazyart on 2007-05-23
You've got great points there.  Inevitably I end up searching the forums here when I have an issue i can't solve, but it is sometimes a minefield wading through threads that barely touch the subject.  A FAQ thread might be nice.  Maybe we already have one and I haven't found it.  That would support your complaint, wouldn't it?

As for dependencies, some more guidance might be in order.  I remember when I found this neat little nugget:```
sudo apt-get install -f
```

Apparently when you try to install a package that has unresolved dependencies, apt-get makes note of it.  That little command will fetch whatever packages you need (provided they are in in the defined repositories) and install them for you.  Maybe it's part of the security model to not download them automatically, but tell me "Try apt-get install -f to resolve" would help.

---

### Post by Cappy on 2007-05-23
I'm thinking about proprietary programs. Things like UT2004, other games, skype, etc.
I've always been able to find the problem but it could definitely annoy someone who didn't know what they were doing. I thought Ubuntu was going to have some kind of click2install program that was going to take care of this problem. I don't remember the name so I can't even google it.

---

### Post by lamalex on 2007-05-23
you're thinking of CNR probably, it should be in the next release.

---

