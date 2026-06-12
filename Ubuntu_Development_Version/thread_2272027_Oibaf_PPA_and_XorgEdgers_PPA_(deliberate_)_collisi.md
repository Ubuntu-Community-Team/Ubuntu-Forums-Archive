---
title: "Oibaf PPA and XorgEdgers PPA (deliberate ?) collision"
date: 2015-04-03
forum: Ubuntu Development Version
---

### Post by zika on 2015-04-03
For years now I do follow these two PPAs.
[http://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=vivid](http://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=vivid)
[http://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=vivid](http://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=vivid)
If You take a close look You will see that (even though older) mesa & some other packages from XE will upgrade over Oibaf packages (even though there as considerably fresher) because of difference in numeration: 2015... instead of 15...
I tried to intervene with authors, but...
Just to make You aware of possible clashes, I've already survived several (not in this cycle)...
Any form of clarification would be greatly appreciated... ;)

---

### Post by bardo2 on 2015-04-03
without even taking a closer look... just sharing: i had a similar problem (and still could run into it). among the possible fixes are: apt-pinning (look that up on the net) and/or apt-mark (command... use manpages).
nice thing about pinning is, that it allows to prevent undesired updates, if you are using it correctly.

---

### Post by cariboo on 2015-04-04
Being the lazy type, I use synaptic to pin packages. It may tough to see, but the only package I have pinned is libdvdcss2. :)

---

### Post by zika on 2015-04-04
> **bardo2 said:**
> without even taking a closer look... just sharing: i had a similar problem (and still could run into it). among the possible fixes are: apt-pinning (look that up on the net) and/or apt-mark (command... use manpages).
nice thing about pinning is, that it allows to prevent undesired updates, if you are using it correctly.I do know about pinning (wrote several times about that here) and that is (kind of) a possible solution but not quite applicable here. I do not have a problem with all this, just wanted to point possible curva pericolosa to some new readers that we've got here. It would be much easier, of course, if numbering were consistent. Just that... ;)

---

### Post by monkeybrain20122 on 2015-04-04
Why do you need both?

---

### Post by zika on 2015-04-05
> **monkeybrain20122 said:**
> Why do you need both?Who wrote &#8222;need&#8220;? ;)

---

### Post by zika on 2015-04-05
> **bardo2 said:**
> without even taking a closer look... just sharing: i had a similar problem (and still could run into it). among the possible fixes are: apt-pinning (look that up on the net) and/or apt-mark (command... use manpages).
nice thing about pinning is, that it allows to prevent undesired updates, if you are using it correctly.
> **cariboo907 said:**
> Being the lazy type, I use synaptic to pin packages. It may tough to see, but the only package I have pinned is libdvdcss2. :)Found some free time to respond: Pinning is not the right answer in cases like this. There is a thing that gives different priorities to different ppa's and that is a nice tool that could (and have) been used in situations like this. I wrote about that when Mir was a topic...
```
cat /etc/apt/preferences.d/ppa_name
Package: *
Pin: o=LP-PPA-ppa_name
Pin-Priority: priority_value
```

---

### Post by mc4man on 2015-04-05
Doubtful. They both use semi informative package names but different styles. XO's make a bit more sense to me but both get the point across.

---

