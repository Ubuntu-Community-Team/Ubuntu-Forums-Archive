---
title: "W32codecs"
date: 2005-04-07
forum: The Cafe
---

### Post by Slapdash on 2005-04-07
In what reppository can i find these codecs
w32codecs and mp3?

---

### Post by TjaBBe on 2005-04-07
[QUOTE=Slapdash]In what reppository can i find these codecs
w32codecs and mp3?[/QUOTE]

I believe they are in universe. For warty:

```

deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

```

Could also be multiverse though.

See [the warty guide](www.ubuntuguide.org) for possible instructions...

---

### Post by Nis on 2005-04-07
[QUOTE=TjaBBe]I believe they are in universe. For warty:

```

deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

```

Could also be multiverse though.

See [the warty guide](www.ubutuguide.org) for possible instructions...[/QUOTE]
 The w32codecs are in hoary-extras on [Ubuntu backports](http://backports.ubuntuforums.org/).
gstreamer0.8-mad (which allows mp3 playback) is in universe or multiverse (as TjaBBe said).
gstreamer0.8-lame (which allows mp3 encoding) is in the marillat repo.

---

### Post by jobezone on 2005-04-07
You must add the marillat repository.
add this to your /etc/apt/sources.list:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

or through Synaptic -> Repositories

---

### Post by TjaBBe on 2005-04-07
To bad w32codecs aren't in the ubuntu repos though. I hate adding the marillat repos just for this.

---

### Post by jobezone on 2005-04-07
yes, sometimes it's a pain in the ass to launch synaptic, add a repository, wait for reload, install a single package, remove repository, wait for reload, close synaptic. It's a lot easier to do this in the command line, though.

---

### Post by TjaBBe on 2005-04-07
[QUOTE=jobezone]yes, sometimes it's a pain in the ass to launch synaptic, add a repository, wait for reload, install a single package, remove repository, wait for reload, close synaptic. It's a lot easier to do this in the command line, though.[/QUOTE]
I never use command line. If you do it the way you suggest it, the packages will be marked "obsolete" in the apt system as far is I know (at least it was that way in debian). I wouldn't want that.

---

### Post by jobezone on 2005-04-07
[QUOTE=TjaBBe]I never use command line. If you do it the way you suggest it, the packages will be marked "obsolete" in the apt system as far is I know (at least it was that way in debian). I wouldn't want that.[/QUOTE]
 i'm talking about adding the repository line to sources.list in /etc/apt/ ,
update, install, remove the line again, and update again.
It's the same process, but faster for me.

Does this make the packages obsolete?

---

### Post by TjaBBe on 2005-04-07
[QUOTE=jobezone]i'm talking about adding the repository line to sources.list in /etc/apt/ ,
update, install, remove the line again, and update again.
It's the same process, but faster for me.

Does this make the packages obsolete?[/QUOTE]

I believe so. Debian did it in anycase. You can check by starting aptitude if you like. (This is somewhat of a console-gui for apt) It is sorting packages by state.

---

### Post by jobezone on 2005-04-07
You're right! I just removed the repository of marillat, and the packages I instaled from it are in section obsolete. But I don't see a problem with this...

---

### Post by Slapdash on 2005-04-07
Ok cool. can listen to music now. I'm happy  ;)

---

