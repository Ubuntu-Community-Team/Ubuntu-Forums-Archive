---
title: "Automatix or Standard Repo?"
date: 2005-11-01
forum: Repositories &amp; Backports
---

### Post by jeffreyvergara.NET on 2005-11-01
Automatix edits the sources.list so it can install softwares not found in synaptic,  somehow, I think Automatix repo is more updated than the standard repo, I noticed that when I use Automatix, there will be updates available, I didnt update it at first, then I used my standard repo again but now, there's no update available. 

Do you think it's much better to use Automatix edited Repo than the standard repo? Automatix added this:
> deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

---

### Post by Kyral on 2005-11-01
That repo is basically like Debian Marillat. You may find legally questionable software there (w32codecs come to mind) but if a package in there is broken, the Ubuntu team cannot do a thing about it, whereas if a package in Main/Restricted/Universe/Multiverse/Backports was busted you could file a bug report with Ubuntu and we would handle it.

Using that repo is basically your call, but understand that Ubuntu cannot support those packages ;P

---

### Post by angrykeyboarder on 2005-11-01
[quote=jeffreyvergara.NET]Automatix edits the sources.list so it can install softwares not found in synaptic, somehow, I think Automatix repo is more updated than the standard repo, I noticed that when I use Automatix, there will be updates available, I didnt update it at first, then I used my standard repo again but now, there's no update available. 

Do you think it's much better to use Automatix edited Repo than the standard repo? Automatix added this:[/quote] 

The reason it was more "updated" (as far as official Ubuntu packages are concerned) is because the sources.list file used in that script uses the main Ubuntu archives (plus ones like you listed above).

Depending on your location, your default sources.list file is set to use one of Ubuntu's primary archive mirrors. (e.g. us.archive.ubuntu.com for the USA, au.archive.ubuntu.com for Australia and so on).

All of the mirrors periodicaly sync with the main archive and the schedules may vary. But the main archive is natuarlly going to be the first to have updates.

Using the main archive in your sources.list file defeats the purpose of the mirrors, which ultimatly slows everything down.

There are quite a few Ubuntu archive mirrors that aren't set up by default on anyone's system. Many of them are very fast with frequent updates. You might try a few out and see if one suits your needs. I'm in the US but abandoned us.archive.ubuntu.com a long time ago. I've found several other mirrors (also in the US) that are much faster and update more frequently.

Check out [https://wiki.ubuntu.com/Archive]("https://wiki.ubuntu.com/Archive") for a rather extensive list of worldwide Ubuntu mirrors.

---

