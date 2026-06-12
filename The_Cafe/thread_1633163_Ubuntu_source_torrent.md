---
title: "Ubuntu source torrent"
date: 2010-11-28
forum: The Cafe
---

### Post by bonfire89 on 2010-11-28
is there anywhere that I could get a file that would be like this

ubuntu-10.10-src-1.iso.torrent ?

I'm curious in seeing what make my computer tick :)


Thanks

---

### Post by Mr. Picklesworth on 2010-11-28
There is no such file, unfortunately, because there are so many different components; sticking them all into one disk would be _weird_ :)

However, you can quickly get the source code for any package in Ubuntu by running
```
apt-get source PACKAGENAME
```

Normally, you'll probably want to use Bazaar. In Ubuntu we use that, along with Launchpad, to manage source code. (Version control systems like it are nice since they keep track of revisions, merging, etc). Bazaar has [a really nice website]("http://bazaar.canonical.com/en/") if you want to learn more about that.
My favourite thing with bzr is the command &#8220;bzr branch lp:SOMETHING&#8221; will usually get you the source code for something that is hosted on Launchpad ;)

[Ubuntu itself]("https://launchpad.net/ubuntu") is developed on Launchpad.net, so the source code for each component is available there. There's no real root to it all, except maybe the machine that builds all the packages (or perhaps [the installer]("https://launchpad.net/ubiquity")).

Searching for the package &#8220;gnome-activity-journal&#8221; from Ubuntu's overview leads me to a page [all about that package in Ubuntu]("https://launchpad.net/ubuntu/+source/gnome-activity-journal").
From that page we can get to gnome-activity-journal's "upstream" project (where its core developers do shiny new stuff), the source code for the version we ship in Ubuntu (sometimes Ubuntu's developers apply extra patches), any bugs and questions attached to it that are specific to Ubuntu, and other fun stuff.

Probably not quite the answer you're looking for, but hopefully it gives you an idea :)

---

