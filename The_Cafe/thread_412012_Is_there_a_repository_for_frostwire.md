---
title: "Is there a repository for frostwire?"
date: 2007-04-17
forum: The Cafe
---

### Post by TheRingmaster on 2007-04-17
I can't seem to get a straight answer. I searched on the frostwire forums and found that it is not in a repo, but that thread was a year old already. I am sure that frostwire is out of beta by now. Is this [link]("http://sourceforge.net/svn/?group_id=142481") what I want or what?

---

### Post by earobinson on 2007-04-17
The simple way to check is to search your repos using synaptic, and I can tell you that frostwire is not in the offical repos. Im sure I have seen it in some 3rd party repo or another.

---

### Post by Quillz on 2007-04-17
I don't know if it's in the repos, but you can get a Ubuntu .deb file right from their official site.

---

### Post by cstudent on 2007-04-17
> **TheRingmaster said:**
> I can't seem to get a straight answer. I searched on the frostwire forums and found that it is not in a repo, but that thread was a year old already. I am sure that frostwire is out of beta by now. Is this [link]("http://sourceforge.net/svn/?group_id=142481") what I want or what?

Download the Ubuntu .deb from here:
[http://www.frostwire.com/](http://www.frostwire.com/)

You'll want to have sun-java 1.5 or better installed as well.

---

### Post by karellen on 2007-04-17
should it be?

---

### Post by cstudent on 2007-04-17
> **karellen said:**
> should it be?

It's not listed at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by TheRingmaster on 2007-04-17
I don't want the deb, they don't update themselves. I want to know of some third party repos that would carry it.

---

### Post by leszek44444 on 2007-04-21
Related question that i always wondered:

What are the conditions and the steps required to put a program in the universe repository ? :-k

---

### Post by earobinson on 2007-04-23
[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by visionaire on 2007-04-23
I've installed with Automatix

---

### Post by TheRingmaster on 2007-04-23
which repository does automatix install frostwire from? Is it the canonical repo?

---

### Post by earobinson on 2007-04-26
who knows, it might just have its own deb file and not provide updates, I would check the automatix fourms

---

### Post by tango_ninja on 2008-02-16
i've searched far and wide and can't seem to find a repo for frostwire... looks like we're stuck using the downloadable package from the site(s)

---

### Post by phrostbyte on 2008-02-16
Is there a reason Frostwire isn't in universe already?

---

### Post by tango_ninja on 2008-02-16
OK well.... I managed to find a repository for Frostwire, but be forewarned I couldn't get it work and caved in to use the [www.frostwire.com](www.frostwire.com) site.

add the following to your   /etc/apt/sources.list

```
  deb http://apt.debian-cl.org/frostwire *version* main
  deb-src http://apt.debian-cl.org/frostwire *version* main
```

where version=**etch** (stable), **lenny** (testing) or **sid** (unstable)

```
 apt-get update
  apt-get install debian-chile-archive-keyring
  apt-get install frostwire
```

*** READ THIS ** READ THIS ***
I wasn't able to get frostwire to work from the repo. I tried installing the stable version and it installed halfway but wouldn't install completely and wouldn't remove completely. 

I'm still a n00b, perhaps some more experienced users could have gotten it working....

I gave up and downloaded the package from the [www.frostwire.com](www.frostwire.com) site but had to forceably remove my failed install from the repo. You might find this code handy if you're going to take a crack at it:

```
sudo dpkg --remove --force-remove-reinstreq frostwire
```

---

### Post by leszek44444 on 2008-02-17
Frostwire isn't included because of the inclusion of pre-compiled libraries in frostwire.

more information here: [[COLOR="RoyalBlue"]https://bugs.launchpad.net/ubuntu/+bug/94011[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/94011")

---

### Post by scorp123 on 2008-04-11
> **tango_ninja said:**
>  where version=**etch** (stable), **lenny** (testing) or **sid** (unstable)  You shouldn't mix Debian repos with Ubuntu ... chances are it's not going to work anyway and will just hose your system.

Yes, Ubuntu is based on Debian ... But not identical to Debian anymore. See the difference? Both Debian and Ubuntu use different versions and version numbers on their libraries, they package things in different ways and so on and so on. Installing things from Debian repos is bound to get you into trouble sooner or later.

---

### Post by gn2 on 2008-04-11
> **TheRingmaster said:**
> I don't want the deb, they don't update themselves. 

Frostwire doesn't update often and it will advise you with a message box if a newer version becomes available anyway.

---

### Post by AllenGG on 2008-04-12
latest version appears here, Debi helper will open:
[http://www.frostwire.com/?id=downloads](http://www.frostwire.com/?id=downloads)

---

### Post by antifaithstl on 2008-09-16
Another reason that Frostwire may not be included in the repositories is the usuall PSP=Piracy BS.  
On Hardy, going to [www.frostwire.com](www.frostwire.com) & downloading the DEB is fine.  It's all based on the old skool Gnutella protocol anyway, so it should still work for a long time after you install it..
Piece

---

### Post by earthpigg on 2008-09-16
> **TheRingmaster said:**
> I don't want the deb, they don't update themselves. I want to know of some third party repos that would carry it.

not as good as an actual repo, but frostwire bugs you to dload the latest version when it comes out... actually, that is much worse than a repo, now that i think of it.

anyways, woot True Blood episode 2.

---

### Post by HotShotDJ on 2008-10-04
> **antifaithstl said:**
> Another reason that Frostwire may not be included in the repositories is the usuall PSP=Piracy BS.This hypothesis is easily falsifiable by doing a quick search of the repositories.  In Synaptic, enter P2P into the search box and you will find several relevant hits (for example kmldonkey).  You can also search for gnutella.  With that search term, you will find several more P2P file sharing clients (for example, gtk-gnutella).  Furthermore, bittorrent is a P2P protocol for which you have several clients available from the official repositories, including one (transmission) that is installed by default.

It is unfortunate that Frostwire is not included, as it is one of the better (at least as far as ease of use for the end-user) file sharing packages out there.  HOWEVER, the explanation given earlier in this thread -- that Frostwire includes some pre-compiled binaries which invalidate the GPL under which they say it is released -- is the most parsimonious explaination and is well documented.

Having said all that... I DO wonder why they don't include it in the multiverse repository:
[QUOTE="http://www.ubuntu.com/community/ubuntustory/components"]The "multiverse" component contains software that is "not free", which means the licensing requirements of this software do not meet the Ubuntu "main" Component Licence Policy.

The onus is on you to verify your rights to use this software and comply with the licensing terms of the copyright holder.

This software is not supported and usually cannot be fixed or updated. Use it at your own risk.[/QUOTE]

---

### Post by sawkey on 2009-02-06
[http://www.tuxsoftware.com](http://www.tuxsoftware.com)
It's repo with frostwire
But every time I run frostwire it tells me theres a newer Linux version available 
So this repo seems to have a out of date package 
But the repo is still being updated and whatnot... 
So you can have up to date, or through a repo...

Ubuntu really should add it to it's repo's though

---

### Post by Foster Grant on 2009-02-06
> **sawkey said:**
> [http://www.tuxsoftware.com](http://www.tuxsoftware.com)
It's repo with frostwire
But every time I run frostwire it tells me theres a newer Linux version available 
So this repo seems to have a out of date package 
But the repo is still being updated and whatnot... 
So you can have up to date, or through a repo...

Ubuntu really should add it to it's repo's though

That's not really a repository ... in fact, it reminds me a bit of Linspire's old ClickNrun site.

I just download it from the Frostwire site. Too bad it's not in the Universe or Medibuntu repositories.

---

### Post by sawkey on 2009-05-10
> **Foster Grant said:**
> That's not really a repository ... in fact, it reminds me a bit of Linspire's old ClickNrun site.

I just download it from the Frostwire site. Too bad it's not in the Universe or Medibuntu repositories.

It has a repo along with a clinkNrun style site...

---

### Post by xenosaga456 on 2009-06-19
well i just downloaded the .deb so ya

---

### Post by xenosaga456 on 2009-06-19
well at first when i installed it it didnot work it said it was currupt so i downloaded a nother copy and installed then it worked lol

---

### Post by WatchingThePain on 2009-06-19
I vaguely remember running Frostwire in wine.
Is it on Getdeb.com maybe?.

---

### Post by BrMBr on 2009-07-08
> **WatchingThePain said:**
> I vaguely remember running Frostwire in wine.
Is it on Getdeb.com maybe?.

Yes, FrostWire is on Getdeb. 

Getdeb.net doesn't have an official repository, but there is one maintained by community. \\:D/

Hardy
         ```
deb http://getdeb.masio.com.mx/ hardy/  
```         Intrepid
         ```
deb http://getdeb.masio.com.mx/ intrepid/
```         Jaunty
         ```
deb http://getdeb.masio.com.mx/ jaunty/
```Add to your sources, update and get not only FrostWire, but all Getdeb.net updates.


Before someone asks, no, there is not an authentication key, so use at your own risk.


I've been using it for 5 months and it's **perfect** so far. :KS:KS:KS:KS:KS

---

### Post by scorp123 on 2009-07-10
> **BrMBr said:**
> Hardy
         ```
deb http://getdeb.masio.com.mx/ hardy/  
```         Intrepid
         ```
deb http://getdeb.masio.com.mx/ intrepid/
```         Jaunty
         ```
deb http://getdeb.masio.com.mx/ jaunty/
```
Add to your sources, update and get not only FrostWire, but all Getdeb.com updates. 

Nice find. :KS

BTW: It's "getdeb.net" ... Not ".com" <== baaaad site!  So again: the real thing has a ".net" top-level domain.

[http://www.getdeb.net](http://www.getdeb.net)

---

### Post by BrMBr on 2009-07-10
> **scorp123 said:**
> Nice find. :KS

BTW: It's "getdeb.net" ... Not ".com" <== baaaad site!  So again: the real thing has a ".net" top-level domain.

[http://www.getdeb.net](http://www.getdeb.net)

Fixed :P
Thanks!

---

### Post by Jordanwb on 2009-12-10
Sorry for necroposting but thanks for the frostwire repo. :guitar:

---

### Post by scorp123 on 2010-01-10
> **Jordanwb said:**
> Sorry for necroposting but thanks for the frostwire repo. :guitar:

Necroposting? I don't think so. At least I am still watching this thread. It can still be found via Google, it's the No. #1 result if you search for a "frostwire repository".

And because it is so let's update this thread with some useful info: In case anyone runs into this thread by finding it via Google:

"getdeb.net" now have their own official repos incl. GPG keys.

How to get the key:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

Then add this line below to your **/etc/apt/sources.list** file (or add it as separate file e.g. into **/etc/apt/sources.list.d/getdeb.list**):
```
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```

Voila, done. After that Frostwire is installable via "apt" or "Synaptic", e.g. for "apt" that would be:
```
sudo apt-get update
sudo apt-get install frostwire 
```

Output from my own system (running Ubuntu Server ... so only the bare minimum is installed. On a normal desktop system I imagine a lot less dependencies would be pulled in ... )

```
$ sudo apt-get install frostwire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgd2-noxpm
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ca-certificates-java icedtea-6-jre-cacao java-common libaccess-bridge-java libaccess-bridge-java-jni libasound2 libflac8 libgif4 libjline-java libogg0 libpulse0 libsndfile1 libvorbis0a libvorbisenc2 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib rhino tzdata-java
Suggested packages:
  equivs libasound2-plugins libjline-java-doc pulseaudio icedtea6-plugin libnss-mdns sun-java6-fonts ttf-baekmuk ttf-unfonts ttf-unfonts-core ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-wqy-zenhei
  ttf-indic-fonts-core ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts rhino-doc
The following NEW packages will be installed:
  ca-certificates-java frostwire icedtea-6-jre-cacao java-common libaccess-bridge-java libaccess-bridge-java-jni libasound2 libflac8 libgif4 libjline-java libogg0 libpulse0 libsndfile1 libvorbis0a libvorbisenc2 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib rhino tzdata-java
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.5MB of archives.
After this operation, 144MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
```

---

### Post by mordak13 on 2010-04-22
scorp123 thanks for this. I can confirm that it works with Lucid as well. if you substitute "karmic" for "lucid" in the sources.list file.

```
deb http://archive.getdeb.net/ubuntu lucid-getdeb apps
```

---

### Post by scorp123 on 2010-05-14
> **mordak13 said:**
> I can confirm that it works with Lucid as well. if you substitute "karmic" for "lucid" in the sources.list file. Yeap! I just upgraded from Karmic to Lucid ... a few smaller hickups and bumps, but now everything looks tip top and the instructions here definitely are still working on Lucid too.

---

