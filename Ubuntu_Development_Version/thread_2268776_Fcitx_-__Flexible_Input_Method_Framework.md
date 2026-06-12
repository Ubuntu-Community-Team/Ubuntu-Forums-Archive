---
title: "Fcitx -  Flexible Input Method Framework"
date: 2015-03-11
forum: Ubuntu Development Version
---

### Post by zika on 2015-03-11
Should we all get FCITX installed?

---

### Post by rrnbtter on 2015-03-11
Well! You didn't let us down with systemd so might as well go with this too:)

---

### Post by grahammechanical on 2015-03-11
I would rather have sweet and sour prawn balls.

It is in the software centre and there is also a launchpad PPA. But what would be the purpose of installing it? Some form of testing? What tests can we do?

---

### Post by dino99 on 2015-03-11
most packages have been added by unity

---

### Post by zika on 2015-03-11
> **grahammechanical said:**
> I would rather have sweet and sour prawn balls.

It is in the software centre and there is also a launchpad PPA. But what would be the purpose of installing it? Some form of testing? What tests can we do?It came automagically to my attention, I did not ask for that. Hence my question as opener in this thread... ;)> **rrnbtter said:**
> Well! You didn't let us down with systemd so might as well go with this too:)> **9d9 said:**
> most packages have been added by unity```
:~$ sudo apt-get purge -s fcitx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fcitx*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
**Purg** fcitx [1:4.2.8.5-6]
```There is a typo in apt-get's response... ;) Still waiting, it so, as You can see, possible to purge it, but I'll try it for some time... ;)
Interestingly enough, I found, by mere serendipity, these days, that using UpStart entry in Grub I get a bit more responsive system than with systemD... ;) That is known fact: fast things gets slower with development... ;)```
1 root      20   0   29464   3976   2396 S   0,0  0,0   0:01.69 upstart
```I still do love SystemD more because it made lots of administrative stuff much easier, to me, of course... ;)
Update&#8321;: [http://ubuntuforums.org/showthread.php?t=2268348&p=13243456#post13243456](http://ubuntuforums.org/showthread.php?t=2268348&p=13243456#post13243456)
Update&#8322;: No, SystemD is as responsive as UpStart (or even a tad more) and my impression was due to some changes that happened in the meantime. Disregard my false observation above.

---

### Post by cariboo on 2015-03-12
I just did a fresh install again on my new Toshiba notebook, and instead of the language indicator I get a keyboard indicator. On my now dead netbook I always got the language indicator. Is this normal on a full sized notebook. See the attachment.

---

### Post by zika on 2015-03-12
[http://ubuntuforums.org/showthread.php?t=2268776](http://ubuntuforums.org/showthread.php?t=2268776)
To disable use gnome-session-properties... ;) 
Merge of threads proposed... ;)

---

### Post by cariboo on 2015-03-12
After seeing Zika's post, I merged the two threads. It seems Fcitx originally stood for Free Chinese Input Toy for X, but was changed for 12.04.

---

### Post by dino99 on 2015-03-12
Discussion about it  Bug lp:1430971

---

