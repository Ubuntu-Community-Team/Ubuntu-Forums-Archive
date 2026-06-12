---
title: "Best way to install E17 in Karmic??"
date: 2009-11-01
forum: The Cafe
---

### Post by kevdog on 2009-11-01
Looking for a little advice the best way to install e17 on Karmic.  I used to use install e17 from svn using the RuisPais thread: [http://ubuntuforums.org/showthread.php?t=916690](http://ubuntuforums.org/showthread.php?t=916690) however this seems not to be the preferred way anymore.  Any suggestions?

---

### Post by worldwithoutgurus on 2009-11-02
Why?

Svn still the best way to run E17 on karmic. 
Runs fine on my machines.

---

### Post by kevdog on 2009-11-02
Any problem with the svn releases of late being broken?

---

### Post by Tux Aubrey on 2009-11-03
> Any problem with the svn releases of late being broken? 

Not really.  There were some pretty fundamental changes a month or so ago and they broke lots of svn-reliant systems (those that, like Rui's e17-svn, are based on the easy_e17 script).

Rui did some patching and it is working fine for me and I haven't heard of many other problems.

I did update the [cafelinux how-to]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os") just recently - but it was mainly to include some karmic-workarounds for the oz-desktop packages that aren't necessary for a "vanilla" e17 install (just follow steps 1 to 4 for e17).

I have used this script (and the oz-desktop packages) on the Ubuntu, Xubuntu and the server versions of Karmic without a problem (provided you also replace network-manager with wicd or another platform independent network tool).  The only time I struck problems was with the netbook-moblin-remix - and I guess that should have been expected. I have also used the .debs from packages.enlightenment.org and had much the same result.

Rui's script is pretty conservative in terms of the extra packages and modules it installs (eg no entrance or ecomorph or anything that is still under heavy development) and that means less scope for bad updates. You can always add those extras if you want to.  By using the version of the script in the cafelinux repos, you get the benefit of any changes (although we have all been a bit slack for six months or so!)

If a problem does arise and it persists for a few updates, I will generally try to post a workaround or warning on the cafelinux forums or on [this thread]("http://ubuntuforums.org/showthread.php?t=916690").

Cheers.

---

### Post by Zezu on 2009-11-16
Installing e17 is described in detail for Karmic here:

[http://ubuntuforums.org/showthread.php?t=1280189&highlight=enlightenment+karmic]("http://ubuntuforums.org/showthread.php?t=1280189&highlight=enlightenment+karmic")

---

### Post by stanca on 2010-01-22
I chose E17-Ecomorph in Ubuntu Karmic: ;)

---

