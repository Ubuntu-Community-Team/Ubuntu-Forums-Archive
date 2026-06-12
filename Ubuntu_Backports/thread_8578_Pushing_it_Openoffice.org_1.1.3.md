---
title: "Pushing it: Openoffice.org 1.1.3"
date: 2004-12-18
forum: Ubuntu Backports
---

### Post by jdong on 2004-12-18
I'm planning a openoffice 1.1.3 backport, because I love the GNOME/GTK+ integration this version from Hoary brought!

Needless to say, this is a LOT of compiling, so I'll blog my progress here.

---

### Post by jdong on 2004-12-18
Downloading sources!!!

10 mins left.

---

### Post by jdong on 2004-12-18
Resolving dependencies....

---

### Post by jdong on 2004-12-18
Yuck, need at least 2 libs to be backported!

Since they are slotted, I think I'll proceed.

---

### Post by jdong on 2004-12-18
```

dpkg-checkbuilddeps: Unmet build dependencies: libcurl3-dev libaltlinuxhyph-dev (>= 0.1.1-6) libebook1.2-dev libxkbfile-dev libxinerama-dev
dpkg-checkbuilddeps: Build conflicts: libidn11 (<< 0.5.2-3)

```

I'm gonna continue and backport these libraries.

---

### Post by jdong on 2004-12-18
ok, this is going too far outside my comfort zone. I'm **NOT** going to backport any libraries just for this!!


Forcing no-deps checking... Seeing if OOo will build.

---

### Post by jdong on 2004-12-18
forget it -- this is going absolutely too far...

OOO 1.1.3 backports are SCRAPPED.

---

### Post by TravisNewman on 2004-12-19
Too bad, the Gnome integration is sweet!!

Can't blame you really though. I wouldn't want to deal with that either!

---

### Post by flibblesan on 2004-12-19
[QUOTE=panickedthumb]Too bad, the Gnome integration is sweet!!

Can't blame you really though. I wouldn't want to deal with that either![/QUOTE]
 shame, but I understand backporting libs can caused a lot of problems.

Good attempt though!

---

### Post by Hikaru79 on 2004-12-19
Aaw, shucks ;_; You got me all excited reading the first post :)

Ah well, that's OK ^ ^ One can always compile from source on their own, right?

---

### Post by jdong on 2004-12-19
It's nasty source to compile...

I got all the dependencies packaged -- 15 libraries -- most of them in main, most of them not binary compatible with Warty's, most of them not slotted.... It was unacceptable. Sorry.

---

### Post by regeya on 2004-12-19
[QUOTE=jdong]It's nasty source to compile...

I got all the dependencies packaged -- 15 libraries -- most of them in main, most of them not binary compatible with Warty's, most of them not slotted.... It was unacceptable. Sorry.[/QUOTE]

I don't think anyone in their right mind could blame you for not wanting to package the mess; after all, it'll probably cause a lot of problems that'll need to be resolved; I for one will just look forward to the improved OO.o when Hoary is released.   :)

---

### Post by kja on 2004-12-22
I dont know if other folks will find this aceptable or not , but I installed OOo 1.1.3 from debian unstable (excluding the Evo Address book intergration , which I dont use ) .

Sid's Libs are close to Warty's than Hoary's are and IIRC I only had to get one lib (libcurl3 I think ) . The installation was flawless , and no more or less scary than using backports or Hoary versions . 

I also got firefox 1.0 from sid as well with zero hassels ,

kja

---

### Post by cpinto on 2004-12-22
I did most of the OOo Portuguese L10N team builds for Linux, so if in any way I can lend a hand, let me know...

---

### Post by jdong on 2004-12-22
If I uploaded those 15 dependency libs, I could've easily gotten a build of OOo 1.1.3 working. However, these new libs would be binary-incompatible with existing Warty packages -- and I have no right to be breaking Warty packages!

I did manage to get OOo 1.1.3 to compile, by bypassing dependency checks. However, I really don't **WANT** to know how much stuff could be broken!

So, I'll leave OOo to be.

---

### Post by cpinto on 2004-12-22
[QUOTE=jdong]If I uploaded those 15 dependency libs, I could've easily gotten a build of OOo 1.1.3 working. However, these new libs would be binary-incompatible with existing Warty packages -- and I have no right to be breaking Warty packages!

I did manage to get OOo 1.1.3 to compile, by bypassing dependency checks. However, I really don't **WANT** to know how much stuff could be broken!

So, I'll leave OOo to be.[/QUOTE]
 AFAIK, the dependencies are defined by the original packager with regards to the most stable packages of the distribution. OOo by itself doesn't have any special requirements when it comes to GTK dependencies, therefore I'm willing to give it a go, and try to compile OOo during the night. 
Where can I download the source package?

**[UPDATE:]**
maybe it's a bit too premature, but OOo 1.1.3 seems to be compiling as I write this. If it gets to build the debian packages, evolution support is gone. I can't say I see this as a major issue, because the official OOo 1.1.3 build doesn't support it.

---

