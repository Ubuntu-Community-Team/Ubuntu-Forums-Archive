---
title: "Brasero broken? (with mp3's)"
date: 2012-12-05
forum: Ubuntu Development Version
---

### Post by screaminj3sus on 2012-12-05
I've noticed brasero 3.6.x seems totally broken when it comes to trying to make an audio cd with mp3 sources. It just says that the audio file is not suitable for audio or video media. I do have all the appropriate gstreamer 1.0 plugins installed.

---

### Post by ronacc on 2012-12-05
and where is the suprise in brassero being broken ? thats its normal condition . The fix is to use K3B ,it runs fine under unity and gnome-shell .

---

### Post by screaminj3sus on 2012-12-05
> **ronacc said:**
> and where is the suprise in brassero being broken ? thats its normal condition . The fix is to use K3B ,it runs fine under unity and gnome-shell .

Yeah but only brasero integrates with rhythmbox and banshee :(. 3.4 worked fine for me, but 3.6 has been broken every since it was released.

---

### Post by DukeOfMixture on 2012-12-06
Brasero is primarily a tool for making cup coasters, but they don't absorb moisture very well.

I generally use growisofs

---

### Post by madverb on 2012-12-06
Another vote to install K3B. Brasero is terrible, at one stage it worked for a while but it has been consistently terrible since then.

---

### Post by x-shaney-x on 2012-12-08
Yes, I have noticed it fails in 3.6.x also, using it from the Gnome 3 PPA in Shell Remix.  
Tried a few times, thinking I had dodgy CD's.
This was pretty bad as I was trying to burn some wedding music at very short notice.

Linux has always been fun but it always seems to let me down when I NEED it to work.
Sometimes I think it's better to stick with what you know rather than update top newer stuff.

Luckily, tried in 3.4.x and it worked fine.

---

### Post by cariboo on 2012-12-08
> **x-shaney-x said:**
> Yes, I have noticed it fails in 3.6.x also, using it from the Gnome 3 PPA in Shell Remix.  
Tried a few times, thinking I had dodgy CD's.
This was pretty bad as I was trying to burn some wedding music at very short notice.

Linux has always been fun but it always seems to let me down when I NEED it to work.
Sometimes I think it's better to stick with what you know rather than update top newer stuff.

Luckily, tried in 3.4.x and it worked fine.

That's why you should always have a stable version installed, just in case you need to do real work, and a testing version lets you down..

---

### Post by screaminj3sus on 2012-12-20
> **cariboo907 said:**
> That's why you should always have a stable version installed, just in case you need to do real work, and a testing version lets you down..

Well technically gnome 3.6 is stable, but its got so many ridiculous bugs you wouldn't think it is :p. This bug is also in 12.10 (if you use the gnome 3 ppa to upgrade braseron to the 3.6 version), and any other gnome 3.6 distro i've used. there's a bug report upstream but zero activity on it.

/rant

---

### Post by tuxor1337 on 2013-01-23
> **screaminj3sus said:**
> there's a bug report upstream but zero activity on it.
For further reference: [https://bugzilla.gnome.org/show_bug.cgi?id=687886](https://bugzilla.gnome.org/show_bug.cgi?id=687886)

---

### Post by craig10x on 2013-01-23
Seems like it's been a long time since Brasero worked well as a disc burner...i switched over to k3b long ago and never looked back...it's always been and still is, one of the best disc burners on linux you will find... :D

As others mentioned, i recommend switching to K3b and be done with it...It's a shame that Brasero doesn't seem to be maintained very well and that one has to go over to the kde side to get a great burner...

---

### Post by Yellow Pasque on 2013-01-24
xfburn is also a good alternative if you don't want a bunch of kde packages on your system.

---

### Post by tuxor1337 on 2013-01-24
Being on a Gnome Desktop, installing k3b for me is over 200 MB while installing xfbrun is only 7 MB (including the xfce libraries). But unfortunately, xfburn is not very stable here. When I create a new CD project, while my (ultrabay) CD burner is not attached, the software complains about a missing burner and even crashes at some point, if I click on the wrong buttons. :-/

---

### Post by jbicha on 2013-01-24
The problem is that many (most?) of the technical people that would work on improving and fixing GNOME or Ubuntu apps don't really burn CDs these days. So Brasero is undermaintained.

It looks like the root cause for the problem has been identified though (and it doesn't affect Ubuntu 12.10 unless you use the GNOME3 PPA or similar to install the new Brasero).

---

