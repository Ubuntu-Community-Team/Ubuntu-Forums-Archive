---
title: "TorrentLinux"
date: 2008-02-11
forum: The Cafe
---

### Post by 1337455 10534 on 2008-02-11
Seeing as many people torrent lots of things (in my case the Ubuntu and Fedora  ISOs), often times all-night, their computers **waste a lot of power** on CPU, screen, RAM etc.. Screen savers or "just turn the monitor off" works, but is it possible to go a step further (below...)?

I have been greatly impressed by Mininux's accomplishment in creating a very functional Linux rescue distribution in under 1.4 MB. Granted it does almost nothing, but you can edit files, download, and do a small variety of essential tasks. :D!!!

To come to my point, why not make TorrentLinux; a Linux-console-based Torrent Client + miniShell to boot into? Possibly of a floppy for minimal resource consumption?

Given the vast variety of distros, I was surprised not to find a console+torrent only Linux. I mean, look at VirginLinux (yes, there is a virgin everything [http://en.wikipedia.org/wiki/Virgin_Group](http://en.wikipedia.org/wiki/Virgin_Group)).

So, to recap, TorrentLinux;
1. Will load appropriate kernel modules
2. Mount its host's HDD(s)
3. Get into a root console
4. Provide a robust shell
4.b: Provide a torrent client
It would be cool if TL would be able to prod a directory on the HDD to find a .torrent file, load it, and begin torrenting and save its goodies back to the HDD, though unrealistic.

This is all speculation; any comments not related to the (il)legality of torrenting? :)

Much appreciated!

---

### Post by Ek0nomik on 2008-02-11
> **1337455 10534 said:**
> Seeing as many people torrent lots of things (in my case the Ubuntu and Fedora  ISOs), often times all-night, their computers **waste a lot of power** on CPU, screen, RAM etc.. Screen savers or "just turn the monitor off" works, but is it possible to go a step further (below...)?

I have been greatly impressed by Mininux's accomplishment in creating a very functional Linux rescue distribution in under 1.4 MB. Granted it does almost nothing, but you can edit files, download, and do a small variety of essential tasks. :D!!!

To come to my point, why not make TorrentLinux; a Linux-console-based Torrent Client + miniShell to boot into?

Given the vast variety of distros, I was surprised not to find a console+torrent only Linux. I mean, look at VirginLinux (yes, there is a virgin everything [http://en.wikipedia.org/wiki/Virgin_Group](http://en.wikipedia.org/wiki/Virgin_Group)).

So, to recap, TorrentLinux;
1. Will load appropriate kernel modules
2. Mount its host's HDD(s)
3. Get into a root console
4. Provide a robust shell
4.b: Provide a torrent client
It would be cool if TL would be able to prod a directory on the HDD to find a .torrent file, load it, and begin torrenting and save its goodies back to the HDD, though unrealistic.

This is all speculation; any comments not related to the (il)legality of torrenting? :)

Much appreciated!

You can set yourself up with a minimalistic distro in Gentoo and just use rTorrent which is a console based torrent client.  This way it's simple and fits your needs.

---

### Post by 1337455 10534 on 2008-02-11
So I would need to compile my own kernel, rtorrent, and bash and stuff it in an .ISO? How would I use Gentoo to make it boot?
I'm gonna look this up!

---

### Post by OoooMatron on 2008-02-11
maybe this is also interesting in your goal

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by hyper_ch on 2008-02-12
Get this:  [http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)

Equip it with debian ( [http://www.nslu2-linux.org/wiki/Debian/HomePage](http://www.nslu2-linux.org/wiki/Debian/HomePage) )

Install rTorrent

Attach a huge drive to it and be happy ;)

---

### Post by AndyCooll on 2008-02-12
> **hyper_ch said:**
> Get this:  [http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)

Equip it with debian ( [http://www.nslu2-linux.org/wiki/Debian/HomePage](http://www.nslu2-linux.org/wiki/Debian/HomePage) )

Install rTorrent

Attach a huge drive to it and be happy ;)

Indeed that's exactly what I've done! Works great.

I do use it for a few other things as well though (e.g. file server).

On the original point, it's possible to do a minimal install of Ubuntu or Debian and then install rtorrent. Indeed Debian does a business card edition (about 35mb) which must be about as minimal as it's possible to get!

:cool:

---

### Post by 1337455 10534 on 2008-02-12
> **hyper_ch said:**
> Get this:  [http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)

Equip it with debian ( [http://www.nslu2-linux.org/wiki/Debian/HomePage](http://www.nslu2-linux.org/wiki/Debian/HomePage) )

Install rTorrent
That's pretty awesome!

---

### Post by macogw on 2008-02-12
Why not just kill X (not ctrl alt backspace, but actually sudo /etc/init.d/gdm stop) and use an ncurses torrent client?  That wouldn't really use much more memory that that live cd with nothing running on it idea.

---

### Post by zachtib on 2008-02-12
> **hyper_ch said:**
> Get this:  [http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)

Equip it with debian ( [http://www.nslu2-linux.org/wiki/Debian/HomePage](http://www.nslu2-linux.org/wiki/Debian/HomePage) )

Install rTorrent

Attach a huge drive to it and be happy ;)

hmmm... that's cool

but i wish they offered one with a gigabit network port.  I've got gigabit networking at my house, and it makes a huge difference in transfer speeds

---

### Post by 1337455 10534 on 2008-02-12
> **macogw said:**
> Why not just kill X (not ctrl alt backspace, but actually sudo /etc/init.d/gdm stop) and use an ncurses torrent client?  That wouldn't really use much more memory that that live cd with nothing running on it idea.

I thought of something similar, but I guess easier.
Just boot into recovery mode, and use said console-baed  torrent client.
Better yet; see if I can find a good Python library and write my own :D.

---

### Post by zachtib on 2008-02-12
> **1337455 10534 said:**
> I thought of something similar, but I guess easier.
Just boot into recovery mode, and use said console-baed  torrent client.
Better yet; see if I can find a good Python library and write my own :D.

libtorrent has python wrappers

---

### Post by 1337455 10534 on 2008-02-12
EDIT: On the other hand rTorrent is just fine!

---

### Post by macogw on 2008-02-12
> **1337455 10534 said:**
> I thought of something similar, but I guess easier.
Just boot into recovery mode, and use said console-baed  torrent client.
Better yet; see if I can find a good Python library and write my own :D.

That sounds like a bad idea.  Recovery mode is single user mode.  It runs entirely as root.  Running as root is a bad idea.

---

### Post by hyper_ch on 2008-02-13
Well, the NSLU2 is good if you don't need a high priority server... when there's much cpu invovled it's not the right thing... but if you want to run just some server services with a low power usage, it's perfect.

---

