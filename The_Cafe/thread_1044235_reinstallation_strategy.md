---
title: "reinstallation strategy"
date: 2009-01-19
forum: The Cafe
---

### Post by uberdonkey5 on 2009-01-19
So, if you are reinstalling ubuntu or upgrading in a way that will over-ride some of your changes (e.g. changes to bootup), whats your strategy for keeping everthing you have e.g. whats the best way to avoid having to find all the codecs, to get the software you want reinstalled etc.

I am wondering whether people keep a disk with installed software so don't have to go through repositories again, or if they have documents with drivers and software locations etc. What about changes (e.g. I have altered bootup considerably), you just do these again? Fire-fox plugins??? etc etc

Just wanna know PRACTICALLY what people do (P.S. did see a thread on creating a live disk that has all your changes and options and software on it, though not sure if that can be used for reinstallation).

thanks

---

### Post by Lod on 2009-01-19
I've made my own install scripts which installs everything I need, including some configuration files. I've several seperated ones because I have several machines which do not require all software.

This is also a very interesting solution:
[http://mybrainrunslinux.com/node/2](http://mybrainrunslinux.com/node/2)
It worked for me very good but I still use my own scripts.

---

### Post by mips on 2009-01-19
One option would be to image your drive once you have fully completed a fresh install. Next time round you will only have the security updates.

---

### Post by adamlau on 2009-01-19
Depends on what the issues were that led to the decision to reinstall. Generally speaking, I keep notes as I go along and replicate my changes manually.

---

### Post by uberdonkey5 on 2009-01-19
> **Lod said:**
> I've made my own install scripts which installs everything I need, including some configuration files. I've several seperated ones because I have several machines which do not require all software.

This is also a very interesting solution:
[http://mybrainrunslinux.com/node/2](http://mybrainrunslinux.com/node/2)
It worked for me very good but I still use my own scripts.

wow, well maybe something that will help me learn more, but does it work? I mean, if repositories change between reinstalls does the whole script crash??

> **adamlau said:**
> Depends on what the issues were that led to the decision to reinstall. Generally speaking, I keep notes as I go along and replicate my changes manually.

Me too, but recently I have become bored with doing that so not sure what I've written down and what I haven't.

> **mips said:**
> One option would be to image your drive once you have fully completed a fresh install. Next time round you will only have the security updates.

Thats good idea,but if I want a reinstall but with a more recent version of ubuntu?

---

### Post by gn2 on 2009-01-19
I just have a separate /home partition and use the same username & password for the new installation.

From 8.10 onwards, the Ubuntu installer has an option to keep the existing /home even if it's not on a separate partition.

---

### Post by Lod on 2009-01-19
> **uberdonkey5 said:**
> wow, well maybe something that will help me learn more, but does it work? I mean, if repositories change between reinstalls does the whole script crash??
It should not because of the use of metapackages. Selecting the package openoffice.org should always install the latest version of openoffice, independent of repository changes. Then again, I always make new scripts for new releases because of minor changes in installation procedures.

---

### Post by twright on 2009-01-19
> **gn2 said:**
> 
From 8.10 onwards, the Ubuntu installer has an option to keep the existing /home even if it's not on a separate partition.
Does it? I wish I had known about that a few days ago :-)

I normally just use a reinstall as a chance to set everything up differently but I am considering keeping notes in the future (I used to when I still needed to manually setup my wifi card with ndiswrapper) because some things like installing the banshee from its repo (to get the latest version) and OpenOffice.org 3.0 can get a bit repetative. A script to do these might be a good idea too.

---

