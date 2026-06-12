---
title: "A question of stability..."
date: 2009-03-19
forum: The Cafe
---

### Post by civillian on 2009-03-19
I'm looking at trying out another distro (alongside ubuntu...I'm not ready to give up the wealth of packages yet...) and I have 2 options firmly in my mind at this time.

The first choice I had/have is debian, I know aptitude well, I like the package choice, I know it works well, but If I was going to choose it I'd probably 'upgrade' it to sid/unstable, and I was wondering how 'unstable' it actually is...I would pin packages like the kernel and probably nvidia drivers etc (the nvidia driver install looks a bit complex but I'm sure it can't be that bad if I write a script to automate the thing)

My second choice is foresight linux. I like the fact it's a rolling release (like debian testing) and uses gnome (and conary sounds like a rather good package managemer), but when I looked onto the forums it doesn't look like a very active community. I was concerned about the lack of available packages (compared to ubuntu) but it has the apps I need/want (quod-libet, transmission).

Mostly, I'm concerned about the debian stability, and the foresight linux community's activity (I relaise I'm spoiled now after using ubuntu...)

Cheers
Civ

---

### Post by Mehall on 2009-03-19
If you're concerned about stability then use Debian Testing rather than unstable, imo.

---

### Post by snowpine on 2009-03-19
I have never heard of Foresight Linux. Debian, on the other hand, is well known for its stability. As far as which branch of Debian is right for you, Testing (Squeeze) is probably the best choice for most desktop users--think of it as a more stable version of Ubuntu. I have never tried "vanilla" Unstable/Sid, but I am a big fan of Sidux, which is sort of a "stabilized Sid." Sidux is an excellent transition for Ubuntu users, in my opinion. Whichever you choose, definitely check out the smxi script. Smxi will help you navigate the upgrade process by walking you through step by step; a very helpful utility.

---

### Post by civillian on 2009-03-19
I was looking at sidux, but i wanted to use the debian netinstall, and then install only what I wanted from the command line (under sid) to help make a more 'clean' system, as opposed the the ubuntu install which has loads of apps I rarely use, and others which I install and use all the time.
It's only really some apprehensions regarding the stability of sid which is keeping me from dualbooting/switching over 100% possibly in the future, but for now I want ubuntu as a fallback incase sid gets messed up...

Foresight linux is a rolling release distro that uses conary package managerment and is based on rpath linux. I think it was designed so that the new 'vanilla' gnome could be demonstrated as the gnome people had designed it. It's good because when you upgrade a package, it keeps old versions so you can "roll-back" if anything goes wrong, and also it only replaces the changed bits of the package so you don't end up with any/as many orphaned packages, or defunct ones. Again, it looks great but some of the most recent posts in it's forums are from last year, and the most recent ones are from last month, so I don't know how active development is (although I'd be more than happy to package up some apps I use regularly if they don't exist in the foresight repos)

---

