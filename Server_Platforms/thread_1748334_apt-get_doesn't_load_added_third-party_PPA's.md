---
title: "apt-get doesn't load added third-party PPA's"
date: 2011-05-03
forum: Server Platforms
---

### Post by ChrisBuchholz on 2011-05-03
Hey guys,

I have a server running Ubuntu Server 11.04, and when I add a PPA via `add-apt-repository`, apt-get doesn't load the PPA when I do `apt-get update`. It's specifically [_this_]("https://launchpad.net/~jerome-etienne/+archive/neoip?field.series_filter=natty") PPA I need to add, but same thing happens for all the PPA's I've tried.

I have checked that the .list files are in fact created in /etc/apt/sources.list.d/, and if I add the PPA's "string" directly in to /etc/apt/sources.list, it still doesn't work.

You can see [_here_]("https://gist.github.com/952345") in action that I first add the PPA and then update, but the PPA's is not on the list of loaded archives. I have also done a [_"s-trace"_]("http://paste.ubuntu.com/602496/") something, that some guy on #ubuntu-server said I could try, and the PPA's I add are actually shown in it and "handled", but for some reason, they are still not getting "punched in use".

I hope somebody can help me with this.

By the way, this server is originally a 10.04.1 installation that has been upgraded to 10.10 and then to 11.04, if that can have something to do with it.

Thank you so far,
ChrisBuchholz

---

