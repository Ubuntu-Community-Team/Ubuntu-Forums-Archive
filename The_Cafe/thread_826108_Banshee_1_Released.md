---
title: "Banshee 1 Released"
date: 2008-06-11
forum: The Cafe
---

### Post by kevin11951 on 2008-06-11
Its official; Banshee 1.0 has been released

[http://banshee-project.org/download/archives/1.0.0/](http://banshee-project.org/download/archives/1.0.0/)

also, has this been mentioned before, i haven't heard of it till now.

---

### Post by bufsabre666 on 2008-06-11
i saw it on reddit earlier, im happy for it, i love banshee myself, its pretty sweet

---

### Post by zmjjmz on 2008-06-11
Want.

---

### Post by kevin11951 on 2008-06-11
> **zmjjmz said:**
> Want.

Banshee also has a new site:

[http://banshee-project.org/](http://banshee-project.org/)

and a binary for ubuntu

Hardy:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main

Gutsy:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main

simply install "banshee-1"

---

### Post by happy-and-lost on 2008-06-11
Banshee completely screwed over my whole media collection last time I used it (6 months ago). Is it safe to say it's more stable now?

---

### Post by zmjjmz on 2008-06-11
> **kevin11951 said:**
> Banshee also has a new site:

[http://banshee-project.org/](http://banshee-project.org/)

and a binary for ubuntu

Hardy:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main

Gutsy:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main

simply install "banshee-1"
Dumb question I'm sure, but [http://ppa.launchpad.net/banshee-team/ubuntu/dists/hardy/main/binary-i386/](http://ppa.launchpad.net/banshee-team/ubuntu/dists/hardy/main/binary-i386/) doesn't seem to have any packages?

---

### Post by damoxc on 2008-06-11
[http://ppa.launchpad.net/banshee-team/ubuntu/pool/main/b/banshee-1/](http://ppa.launchpad.net/banshee-team/ubuntu/pool/main/b/banshee-1/)

That's where they are.

---

### Post by FuturePilot on 2008-06-11
> **zmjjmz said:**
> Dumb question I'm sure, but [http://ppa.launchpad.net/banshee-team/ubuntu/dists/hardy/main/binary-i386/](http://ppa.launchpad.net/banshee-team/ubuntu/dists/hardy/main/binary-i386/) doesn't seem to have any packages?

That's just the apt package lists. The actual packages are kept under /pool

---

### Post by zmjjmz on 2008-06-11
Upon trying to install it, I get that lib002.0-cil isn't satisfiable or something.

---

### Post by YaPaY on 2008-06-11
> **zmjjmz said:**
> Upon trying to install it, I get that lib002.0-cil isn't satisfiable or something.

same problem here.

---

### Post by Mateo on 2008-06-11
> **zmjjmz said:**
> Upon trying to install it, I get that lib002.0-cil isn't satisfiable or something.

you installing from source?  the PPA has that package.

---

### Post by YaPaY on 2008-06-11
no from source. From deb package. I have added these:

```
deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
```

I've also downloaded these: libboo2.0-cil_0.8.1.2865-2~hardy1_all.deb and banshee-1_1.0.0-1ubuntu1~hardy3_i386.deb packages.

No success.

---

### Post by SomeGuyDude on 2008-06-11
Can I use it with conky yet??

---

### Post by Mateo on 2008-06-11
Absolutely fantastic.  I always thought Banshee was a bit bizarre.  I could never figure out how to get the older versions to have an artist/album browser, it seemed to only work on playlists (which is absurd, IMO).  This new version is absolutely fantastic. The last.fm integration seems to be even better than in bmpx.

The only thing that seems off is the still way-too-small progress bar.  Otherwise, Gnome might have found it's Amarok.

---

### Post by Tom--d on 2008-06-11
> **YaPaY said:**
> same problem here.

Again, same

---

### Post by kevin11951 on 2008-06-11
> **YaPaY said:**
> no from source. From deb package. I have added these:

```
deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
```

I've also downloaded these: libboo2.0-cil_0.8.1.2865-2~hardy1_all.deb and banshee-1_1.0.0-1ubuntu1~hardy3_i386.deb packages.

No success.

im pretty sure your not using intrepid...

```
deb http://ppa.launchpad.net/banshee-team/ubuntu **intrepid** main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu **intrepid** main
```

try this:

Hardy:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main

Gutsy:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main

---

### Post by zmjjmz on 2008-06-11
I added the hardy sources in the launchpad page, but that gave me version 0.13.2+dfsg-9 or so?
EDIT: I should've y'know, **read** the PPA info.

---

### Post by kevin11951 on 2008-06-11
> **zmjjmz said:**
> I added the hardy sources in the launchpad page, but that gave me version 0.13.2+dfsg-9 or so?

are you installing banshee-1?

---

### Post by DizzyTech on 2008-06-11
I love Banshee 1, but there's a bit of a showstopper for me.  Me and my Windows buddies, iTunes and Windows Media Player, tag all of the correct album art to my music.  So does Banshee, mostly.  Half of my (fairly mainstream) albums either don't have art period or use the wrong one.  See my image below.  Why won't it let me change it on my own?  I understand GNOME-like apps are intended to be very simple, but why not include basic features?  Even Rhythmbox fetches the correct album art.

---

### Post by zmjjmz on 2008-06-11
It means that the repository for album art prolly doesn't have the correct covers, and thus it uses the one from earlier or something.

---

### Post by drsaamah on 2008-06-16
I've had the incorrect album art problem myself although not to a ridiculous extent.  The problem lies with last.fm having the incorrect artwork associated with an album.  There's some way around this involving saving the album art file in the same folder as the music files or something but I can't remember exactly how.

---

