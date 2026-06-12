---
title: "mp3gain missing from 16.04 repositories ?"
date: 2016-04-26
forum: Ubuntu Studio
---

### Post by nik.charles on 2016-04-26
Have been trying to work on having a simple method for newbies to install Ubuntu Studio 16.04 for streaming radio, but hit a problem. Only been full time on Linux for couple of years myself. Not sure of where to go next

got all essential applications installed - primarily idjc and skype - but idjc has a strange bug of not wanting to play mp3's if it is missing an APE tag. mp3gain on command line has been my method to get the mp3 tags fixed.

Studio does have gui options for the newbies, so i went for easymp3gain-qt. Was surprised to find that although it installed, it doesn't get the mp3gain dependency and just doesn't work. Also tried the gtk version just in case, but no luck with that either. Both versions also install easymp3gain-data package

If it were just for my use, I would attempt to compile mp3gain from source, but am trying to make it easy for some friends interested in switching from windows. 

am i missing something? has the mp3gain package been overlooked? or is there an alternative package or gui app that can solve this?

---

### Post by jejeman on 2016-04-27
If I understood correctly you want Tag editor?
EasyTag is program for working with mp3 tags.

---

### Post by nik.charles on 2016-04-29
thanks for reply jejeman, but it isn't precisely a tag editing problem

Have been looking at tag editors suggested by friends in last couple of days. most do not handle the APE tag needed for idjc, often the only option is to remove the APE tag to only use standard ID3 tag. I suspect that even if i find a tagger application that can do replaygain, it will have dependency on the unavailable mp3gain package 

This is really an idjc bug i have been working around for couple of years. It has been flagged to the idjc developer before, but i suspect it is one guy running the project and getting it fixed at source may take a long time

Replaygain is something i was using on windows for a long time. I could run foobar in wine to get this function working easily, but i would really prefer a native Linux option. I really don't want to be telling linux newcomers to add a windows application.

I still have couple of other things to look into about this. Will repost again soon if get any further info

---

### Post by nik.charles on 2016-04-29
Looks like I have got a working solution on this for now

Found the required mp3gain package at:
[https://pkgs.org/ubuntu-14.04/ubuntu-universe-amd64/mp3gain_1.5.2-r2-6_amd64.deb.html](https://pkgs.org/ubuntu-14.04/ubuntu-universe-amd64/mp3gain_1.5.2-r2-6_amd64.deb.html)

It won't install via gnome-software, so have to install gdebi as well to get it in there

This problem has also given me some new options to look into for the future. 

There is a new package (BS1770gain) that looks like good alternative for mp3gain. Not considered it before as only been command line tool. Had a friend has point me to [http://beets.io/](http://beets.io/) which looks like a good toolkit for tinkering with audio files, and can use mp3gain or BS1770gain. IDJC has this new gain standard included already. Time for some extended software and listening tests

---

### Post by holto2go on 2016-06-26
pretty poor that mp3gain was overlooked fro the standard repos, it is and has been the gold standard for equipoising mp3 libraries.

anyway the 14.04 deb works fine, just sloppy to have to add an old deb.

---

### Post by kazakore on 2016-06-27
I also have installed this from the 14.04 repo. Please bring it back as a standard package!

Although for now I have just found there is this user ppa you could add to install it and a couple of other removed audio bits.
[https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio](https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio)

---

### Post by yrjo1 on 2016-12-09
There is easymp3gain-gtk in Ubuntu 16.04 official repo.

---

### Post by naught101 on 2017-03-14
> **yrjo1 said:**
> There is easymp3gain-gtk in Ubuntu 16.04 official repo.

easymp3gain-gtk is just a GUI, and has a dependency on mp3gain, so it won't work for mp3s (just ogg, flac, etc).

---

### Post by mc4man on 2017-03-14
Get it here, packages for all recent Ubuntu releases+
[https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio](https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio)

---

