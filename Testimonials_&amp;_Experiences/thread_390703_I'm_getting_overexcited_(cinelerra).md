---
title: "I'm getting overexcited (cinelerra)"
date: 2007-03-22
forum: Testimonials &amp; Experiences
---

### Post by blippy on 2007-03-22
Forgive me whilst I just bubble over like a madman.

I had XP installed on my machine, and it started going belly up after only 3 days. I got cheesed off, and decided to install Kubuntu Edgy. I did an upgrade, and now the taskbar on KDE doesn't work properly. So I'm switching to WindowMaker for now.

I discovered cinelerra - a free full-featured video editor. Oh man, oh man, oh man, what a great piece of software. This is what Open Source should be all about. It took me some time to figure WTF was going on, but it's a really good piece of software. It's not in any of the standard repos - you have to add an extra sites to apt-get it. It would be a shame if it ever became unusable on Ubuntu through bitrot.

Here's what I want to see in Ubuntu:
* more media codecs
* PROPER support for my Quickcam Pro 5000
* Yahoo Messenger
* more bug fixes - general all-round tidy up


Can't wait to try out Feisty when it is fully released.


:guitar:

---

### Post by 3rdalbum on 2007-03-23
> **blippy said:**
> 

I discovered cinelerra - a free full-featured video editor. Oh man, oh man, oh man, what a great piece of software. This is what Open Source should be all about. It took me some time to figure WTF was going on, but it's a really good piece of software. It's not in any of the standard repos - you have to add an extra sites to apt-get it. It would be a shame if it ever became unusable on Ubuntu through bitrot.

I believe it will be available in Feisty - it's a program that will be included in the upcoming Ubuntu Studio distribution.

> 
Here's what I want to see in Ubuntu:
* more media codecs

You haven't got everything set up then. Do a search for Automatix online, download it and install all the media codecs, and then install the Kaffeine media player (you might already have it).

Since I did that, I have not come across a single video that I haven't been able to play.

---

### Post by blippy on 2007-03-24
> **3rdalbum said:**
> I believe it will be available in Feisty - it's a program that will be included in the upcoming Ubuntu Studio distribution.

Interesting - although I am not looking for a specialised studio distribution per se. I see that a studio distro is something marked as a meta-package.

I'm wondering if the whole meta-packaging is an idea that needs to be developed further. It seems an interesting way of compartmentalising things in order to produce spinoff distros. People are getting all sorts of ideas about what they want Ubuntu to be. I've borked my KDE, for instance, and I am currently using Englightenment. I notice that there is a distro trying to produce something Enlightenment-based. Everybody's got their own ideas.

With meta-packaging, it will hopefully save distro developers some work; and hopefully make the life of a humble user more pleasant, allowing them to pick-and-mix what sort of things they are interested in, in varying degrees of granularity as the meta-packagers anticipate.

Food for thought?

---

### Post by 3rdalbum on 2007-03-25
I see metapackages as potentially more than that, actually.

Right now, if you try to install a Fedora RPM on Mandriva, you usually get dependency problems. This is because the distributions use different names for the same package (for instance, Vorbis support on one might be called *libvorbis* and on the other might be called *libogg-vorbis*.

However, let's say there was a metapackage on all distributions called "mp-vorbis-support". This would depend on whatever the real Ogg Vorbis packages are. People developing and packaging programs that require the Vorbis libraries could make their RPMs depend on "mp-vorbis-support", so they would always install and run on all distributions.

---

### Post by KoRnholio on 2007-03-26
Actually, Cinelerra's inclusion into Ubuntu repos was deferred until license issues can be worked out.  It won't make it into Fiesty - hopefully it could make it into Fiesty +1, but who knows.

And while Cinelerra's packaging is being done by the Ubuntu Studio project benefits other Ubuntu studio users as well.  Once its in whatever Ubuntu repo that it goes in, any Ubuntu user will be able to apt-get it.  This is because Ubuntu Studio uses the same repos as regular Ubuntu.

But that will have to wait till Fiesty + 1 at the earliest.  For now, users have to add the 3rd-party repo, or compile from source.

---

