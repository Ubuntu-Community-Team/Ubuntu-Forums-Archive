---
title: "Replacement for Tomboy"
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lucazade on 2012-01-19
What will replace Tomboy in 12.04? Gnote? nothing?!
I'm wondering about UbuntuOne support for notes... any ideas?

---

### Post by fjgaude on 2012-01-19
As Gnote is fully finished it should be a direct replacement for Tomboy. I've yet to remove Tomboy from my system to see actually how Gnote works. It uses the same database as Tomboy but doesn't auto into the Tray in Unity. We'll see...

---

### Post by ventrical on 2012-01-19
It automatically locks itself in launcher and also when you click <start here> it says <Welcome to Tomboy>


EDIT-Wow .. it blotted out  <Welcome to Tomboy>

---

### Post by ventrical on 2012-01-19
Got it.

---

### Post by tekstr1der on 2012-01-19
From [http://live.gnome.org/Gnote](http://live.gnome.org/Gnote)

> Gnote

Gnote is a port of Tomboy to C++.

It is the same note taking application, including most of the add-ins (more are to come). **Synchronization support is being worked on**. 

It may be a direct replacement in the future, but for now (and likely 12.04 LTS) is still lacking sync, a key feature of Tomboy. Useless for my needs without it. Being able to sync Tomboy notes on U1 servers is fantastic.

OT: Looks like I'll need to pull in Mono just to have this. Might as well stick to Banshee too at that point. I've found that to be much more reliable than my years debugging Rhythmbox.

---

### Post by lucazade on 2012-01-19
> **ventrical said:**
> It automatically locks itself in launcher and also when you click <start here> it says <Welcome to Tomboy>


EDIT-Wow .. it blotted out  <Welcome to Tomboy>

then? what's the point of it? :confused:
more than welcome is goodbye tomboy...

---

### Post by lucazade on 2012-01-19
> **tekstr1der said:**
> From [http://live.gnome.org/Gnote](http://live.gnome.org/Gnote)



It may be a direct replacement in the future, but for now (and likely 12.04 LTS) is still lacking sync, a key feature of Tomboy. Useless for my needs without it. Being able to sync Tomboy notes on U1 servers is fantastic.

OT: Looks like I'll need to pull in Mono just to have this. Might as well stick to Banshee too at that point. I've found that to be much more reliable than my years debugging Rhythmbox.

Agree, sync is an important feature and without this gnote is not that great alternative.
mmh.. maybe a lense for unity? :)

---

### Post by effenberg0x0 on 2012-01-19
When I gave up Mono a while ago, I decided to try Nixnote. I installed (paid) Evernote app in my Android Phone, installed free Evernote browser plugins in all my PCs/Browsers, converted notes from Tomboy/Other Apps to it, etc. It took me a while to make an organised folder structure, tag everything and get comfortable with using it. Now I'm completely dependent of it:

- My bookmarks are backed-up, synchronised to Evernote every 1 hour.
- I have  Snippets lib that is also in sync between devices
- Personal folders with contacts / addresses / Telephone numbers of people
- Personal finances info, PINs and etc
- Clipping, acount/clients info
- Reminders
- Etc...

I'm not too much into Java apps. Everyday I wonder why didn't they code Eclipse in C... But Nixnote impressed me as Linux "clone" app that feels more powerful than the original app (Evernote). I saw some website that mentioned that Evernote is 100% usable via Wine too, but I have not tried it.

---

### Post by fjgaude on 2012-01-19
> **lucazade said:**
> Agree, sync is an important feature and without this gnote is not that great alternative.
mmh.. maybe a lense for unity? :)

My Tomboy notes are in my 'database' along with all my graphic designs and photos (over 65K of them) which is synced to all my computers, partitions, using grsync. Database is off 'home' on each computer, so gnote works for me now without having its own internal sync feature.

---

### Post by jfernyhough on 2012-01-19
> **effenberg0x0 said:**
> When I gave up Mono a while ago, I decided to try Nixnote.Was going to suggest trying Nevernote then I did a search for Nixnote. Looks like they're the same thing but I'd missed they'd moved to the Nixnote name. :D

I'll also put in a reference to Zim here. It's not strictly a Tomboy replacement but pretty nice all the same.

---

### Post by PhilGil on 2012-01-19
> **jfernyhough said:**
> I'll also put in a reference to Zim here. It's not strictly a Tomboy replacement but pretty nice all the same.I'm a big fan of Zim.

Replaced Tomboy with Zim when I was experimenting with XFCE. I find Zim more powerful than Tomboy and I like the single window interface. I share my data store in Dropbox and haven't had any problems with file corruption; should work the same in U1.

---

### Post by lucazade on 2012-01-20
> **effenberg0x0 said:**
> When I gave up Mono a while ago, I decided to try Nixnote. I installed (paid) Evernote app in my Android Phone, installed free Evernote browser plugins in all my PCs/Browsers, converted notes from Tomboy/Other Apps to it, etc. It took me a while to make an organised folder structure, tag everything and get comfortable with using it. Now I'm completely dependent of it:

- My bookmarks are backed-up, synchronised to Evernote every 1 hour.
- I have  Snippets lib that is also in sync between devices
- Personal folders with contacts / addresses / Telephone numbers of people
- Personal finances info, PINs and etc
- Clipping, acount/clients info
- Reminders
- Etc...

I'm not too much into Java apps. Everyday I wonder why didn't they code Eclipse in C... But Nixnote impressed me as Linux "clone" app that feels more powerful than the original app (Evernote). I saw some website that mentioned that Evernote is 100% usable via Wine too, but I have not tried it.

From screenshots nixnote looks great and really complete... too bad it is in java and like you I'm not a java lover.

I suppose Eclipse is written in java to be crossplatform without too much hassle, I use it everyday at work on ubuntu. The good thing is that uses SWT as gui instead of swing, so that look and feel is quite native, unfortunately memory consumption is crazy :)

---

### Post by lucazade on 2012-01-20
> **PhilGil said:**
> I'm a big fan of Zim.

Replaced Tomboy with Zim when I was experimenting with XFCE. I find Zim more powerful than Tomboy and I like the single window interface. I share my data store in Dropbox and haven't had any problems with file corruption; should work the same in U1.

I'll give zim a shot.. I used in the past and it was really good.
Also cherrytree was a good hierarchical note app: [http://www.giuspen.com/cherrytree/](http://www.giuspen.com/cherrytree/)

---

### Post by directhex on 2012-01-20
> **tekstr1der said:**
> From [http://live.gnome.org/Gnote](http://live.gnome.org/Gnote)

Sync has been "in progress" on Gnote for about 2 years. Don't hold your breath.

---

### Post by rojaasensei on 2012-01-21
> **PhilGil said:**
> I'm a big fan of Zim.

Replaced Tomboy with Zim when I was experimenting with XFCE. I find Zim more powerful than Tomboy and I like the single window interface. I share my data store in Dropbox and haven't had any problems with file corruption; should work the same in U1.

I installed the Zim PPA and installed.  Great app!  Thanks for the headsup :D

---

