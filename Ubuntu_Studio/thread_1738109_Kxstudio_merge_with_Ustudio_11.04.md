---
title: "Kxstudio merge with Ustudio 11.04?"
date: 2011-04-24
forum: Ubuntu Studio
---

### Post by barisurum on 2011-04-24
Back in the days of Ustudio 10.04 I was able to add the kxstudio repos and make my Ustudio installation a kxstudioed monster. 

When I tried the same thing with Ustudio 11.04, although there are repos for natty in the kxstudio ppa, I ran into many package problems which ended up with removing jack server along with tons of packages that depend on it. So I had to restore my system by installing ubuntustudio-desktop and -audio metapackages.

My question is: Will it be possible to merge natty Ustudio with kxstudio in the future? 

FalkTX or anyone informed about the future please answer this if you read this post.

---

### Post by Excds on 2011-04-28
Some info here:
[http://kxstudio.sourceforge.net/tmp/KXStudio-Team.odt](http://kxstudio.sourceforge.net/tmp/KXStudio-Team.odt)

And here:
[https://launchpad.net/kxstudio/+announcement/8205](https://launchpad.net/kxstudio/+announcement/8205)

Also, there's an ongoing discussion in this thread:
[http://ubuntuforums.org/showthread.php?t=1670196](http://ubuntuforums.org/showthread.php?t=1670196)

---

### Post by sgx on 2011-04-28
> **barisurum said:**
> Back in the days of Ustudio 10.04 I was able to add the kxstudio repos and make my Ustudio installation a kxstudioed monster. 

When I tried the same thing with Ustudio 11.04, although there are repos for natty in the kxstudio ppa, I ran into many package problems which ended up with removing jack server along with tons of packages that depend on it. So I had to restore my system by installing ubuntustudio-desktop and -audio metapackages.

My question is: Will it be possible to merge natty Ustudio with kxstudio in the future? 

FalkTX or anyone informed about the future please answer this if you read this post.
I've learned over the years, it's better to record, edit, and master,
than to upgrade just because it's possible. Regardless which OS is in use. Once the daw is stable, let the tunes begin. Set up secondary systems, install on extra drives, or usbsticks, for experiments, and
make changes after stability is carved in stone.
Cheers

---

### Post by fedexnman on 2011-04-29
> **sgx said:**
> I've learned over the years, it's better to record, edit, and master,
than to upgrade just because it's possible. Regardless which OS is in use. Once the daw is stable, let the tunes begin. Set up secondary systems, install on extra drives, or usbsticks, for experiments, and
make changes after stability is carved in stone.
Cheers

you got that one right !

---

### Post by barisurum on 2011-04-29
[QUOTE=sgx]I've learned over the years, it's better to record, edit, and master,[/QUOTE]

I totally agree. Actually installed 10.04-3 three days ago and it works very well. The only worry I had in mind was would my relatively new nvidia gfx card (GTS450) work with a system that old. But testing it revealed that it indeed works (2.6.31-11 rt kernel). And with the joy of having this goodness all in place I made a promotional video to propagate KXStudio's usage:

[http://www.youtube.com/watch?v=l6ftjmyjQW4](http://www.youtube.com/watch?v=l6ftjmyjQW4)

cheerz to KXStudio enjoyers! :D

---

### Post by falkTX on 2011-05-03
Hey guys,

I've been very busy lately, but I think I'll have some free time soon to fix any last things before the big release(s).

There are some update issues, but mostly are already taken care of (you shouldn't really expect kxstudio+natty to be working before natty release...)

Please report any upgrade issue you found (I just fixed ia32-libs).
I'm just one guy maintaining 3 Ubuntu versions, I surely need some testers.

Once you find something interesting, drop by the KXStudio bug reports page:
[https://bugs.launchpad.net/kxstudio/](https://bugs.launchpad.net/kxstudio/)

Thanks

---

### Post by m.lp.ql.m on 2011-05-06
> **sgx said:**
> I've learned over the years, it's better to record, edit, and master,
than to upgrade just because it's possible. Regardless which OS is in use. Once the daw is stable, let the tunes begin. Set up secondary systems, install on extra drives, or usbsticks, for experiments, and
make changes after stability is carved in stone.
Cheers

Where's the fun in that? :)

No, seriously, for some of us, a lot of musical creativity comes from the serendipity of screwing around with all these free, little-known, OSS audio apps, broken or not.

Plus, falkTX needs help breaking and fixing things.

---

### Post by sgx on 2011-05-07
Slow that reader machine thingie down, did I actually suggest that one should not use "free, little-known, OSS audio apps, broken or not"? Dude, thats ALL WE HAVE!!! :wink:

Playtime, lab experiments, and educational ventures are great, even necessary, but on ones main computer or daw, backups, and
separate /home partitions should be the norm. It's become
easy to learn how to boot from usbsticks and other extra devices,
so it is like backing up important data, how much value can you afford to loose? Someone who has struggled, and persevered, and finally achieved a stable working system, should tread very lightly, and preferably on different soil.

Myself, I'm a perpetual OS tweaker, 2 new distros a month, plus revisits to rejected dogs, in case they improved, and also being a linux newbie, I always learn from the generous guidance found here, a small fraction of which I can repeat, on good days :D If I don't, it vanishes, and I'm back to square one. :(
Cheers

---

