---
title: "I &#9829; Compiling from source!"
date: 2009-04-19
forum: The Cafe
---

### Post by dragos240 on 2009-04-19
Even though I have the ubuntu repositories on my side, compiling from source is so fun! Especially when you can customize it any way you see fit. Man I [SIZE=4]&#9829;[/SIZE] Linux so much!

---

### Post by Sand &amp; Mercury on 2009-04-19
I've always found it to be very messy and cumbersome as opposed to using packages. For power users and developers only.

---

### Post by dragos240 on 2009-04-19
> **Sand & Mercury said:**
> I've always found it to be very messy and cumbersome as opposed to using packages. For power users and developers only.

Or programs that aren't in the repositories! I found quite a few little known packages that needed to be compiled from source.

---

### Post by bp1509 on 2009-04-19
d

---

### Post by dragos240 on 2009-04-19
> **bp1509 said:**
> you should try out gentoo.  It's a fun experience.

I can't because of the way my network works :(

---

### Post by RATM_Owns on 2009-04-19
I use Gentoo and Arch. :P

Gentoo is good once it's setup.

---

### Post by Eisenwinter on 2009-04-19
Don't have to try Gentoo just yet, you can try Arch with ABS.

---

### Post by RichardLinx on 2009-04-19
> **Eisenwinter said:**
> Don't have to try Gentoo just yet, you can try Arch with ABS.

What's ABS? Nevermind, I googled "Arch + ABS" and got the answer. (Arch Build System). The first search I did "ABS" gave me "Australian Bureau of Statistics" :P

---

### Post by dragos240 on 2009-04-19
Huh, interesting, are you actually on the moon, I looked at your location.....

---

### Post by RiceMonster on 2009-04-19
I don't mind compiling, but if I won't do it without a PKGBUILD because it annoys me if I have something installed that the package manager is not aware of.

Anyway, if you love compiling, why don't you try a source distro like Gentoo, CRUX or Lunar? Oh wait, you said you were having problems with Gentoo.

---

### Post by Josef_A on 2009-04-19
> **dragos240 said:**
> Or programs that aren't in the repositories! I found quite a few little known packages that needed to be compiled from source.
Package them for the rest of us, maybe?

---

### Post by sarang on 2009-04-19
You should write software for the FOSS community. I have a feeling you will enjoy it.

---

### Post by 3rdalbum on 2009-04-19
I prefer to go to the repos, but I'm comfortable with compiling and sometimes I like adding extra options to the configure script.

I don't seem to be as comfortable with it as I thought though; I compiled a new ffmpeg and for some reason it didn't work properly. Very strange as I compiled it before once with good results.

---

### Post by sharathpaps on 2009-04-19
@ dragos240,
                Maybe you should write a good how to on compiling from source. I'm relatively new to Linux and I'd like to learn how to compile from source although I know that it is in no way necessary to use Ubuntu. This is what I know of compiling

```
tar xvzf or tar xvjf
cd package
./configure
make all
```

But this does not work in all situations. I'd love to know the basics behind compiling.

---

### Post by swoll1980 on 2009-04-19
Compiling is nice when it works. When it doesn't it can make me want to rip my hair out.

---

### Post by amitabhishek on 2009-04-19
> **swoll1980 said:**
> Compiling is nice when it works. When it doesn't it can make me want to rip my hair out.

Most of the time it doesn't...

---

### Post by Daisuke_Aramaki on 2009-04-19
> **amitabhishek said:**
> Most of the time it doesn't...

Of course, if you don't know what you are doing, it won't. you should know a little about what the software does, and what it depends on and such. Besides, when you run into configure error, you are gonna end up knowing what failed.

---

### Post by mamamia88 on 2009-04-19
i don't mind compiling from source as long as detailed instructions to install are included in the package and i can find the dependencies easily enough in synaptic

---

### Post by BigSilly on 2009-04-19
> **mamamia88 said:**
> i don't mind compiling from source as long as detailed instructions to install are included in the package and i can find the dependencies easily enough in synaptic

Same here. I don't mind doing it if the author has outlined what's needed first, otherwise I don't do it. I don't find it much fun trying to decipher cryptic error messages with Google.

---

### Post by WatchingThePain on 2009-04-19
That is so Kinky.;)

---

### Post by smartboyathome on 2009-04-19
I love it too! It makes my machine that much faster, especially when you set -march=native for your CFLAGS in Arch. I don't mind much the dependancies, but that is becuase I can usually find out wha they are if they aren't there already.

---

### Post by FakeOutdoorsman on 2009-04-19
> **3rdalbum said:**
> ...I compiled a new ffmpeg and for some reason it didn't work properly. Very strange as I compiled it before once with good results.

A little off-topic, but did you see this?

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by kevdog on 2009-04-19
How much faster does this make things compared to when its not included:

-march=native

I'm skeptical

---

### Post by namegame on 2009-04-19
> **kevdog said:**
> How much faster does this make things compared to when its not included:

-march=native

I'm skeptical

I've just tried out Lunar Linux and my entire system is compiled with CFLAGS tailored to my system. This is purely anecdotal evidence, but right now, Firefox with 3 tabs open is using a little less than 100 MB of RAM. I never got it that low in Arch or any other system.

---

### Post by kevdog on 2009-04-19
Hey I'm always willing to learn a few lessons so teach me if you can.  What cflags should I be using on a regular basis, or LD flags for that matter?  I usually don't mess with such options, but when I have for various reasons, I usually don't see a difference (unless a particular LD flag is necessary to move the linking process forward!).

---

### Post by namegame on 2009-04-19
> **kevdog said:**
> Hey I'm always willing to learn a few lessons so teach me if you can.  What cflags should I be using on a regular basis, or LD flags for that matter?  I usually don't mess with such options, but when I have for various reasons, I usually don't see a difference (unless a particular LD flag is necessary to move the linking process forward!).

That depends mostly upon your processor architecture. Here are two good links for Intel and AMD processors:

[http://en.gentoo-wiki.com/wiki/Safe_Cflags/AMD](http://en.gentoo-wiki.com/wiki/Safe_Cflags/AMD)

[http://en.gentoo-wiki.com/wiki/Safe_Cflags/Intel](http://en.gentoo-wiki.com/wiki/Safe_Cflags/Intel)

---

