---
title: "Can't install synaptic"
date: 2015-10-21
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-10-21
Boy oh boy, this is proving to be a very buggy final test cycle. Tried to install synaptic in an install that I completed last night to see what changes to expect in the next build:

```
lance@lance-AMD-desktop:~$ sudo apt-get install synaptic
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docbook-xml libcairo-perl libept1.4.16 libglib-perl libgtk2-perl
  libpango-perl librarian0 libvte-2.90-9 libvte-2.90-common rarian-compat
  sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide libfont-freetype-perl
  libgtk2-perl-doc perlsgml w3-recs opensp dwww menu deborphan tasksel
The following NEW packages will be installed:
  docbook-xml libcairo-perl libept1.4.16 libglib-perl libgtk2-perl
  libpango-perl librarian0 libvte-2.90-9 libvte-2.90-common rarian-compat
  sgml-data synaptic
0 upgraded, 12 newly installed, 0 to remove and 4 not upgraded.
**[COLOR="#FF0000"]E: Can't find a source to download version '1.105-1' of 'libcairo-perl:amd64'[/COLOR]**

```

---

### Post by sgage on 2015-10-21
Synaptic installed here without incident just a couple of days ago on a fresh install of Ubuntu Gnome. When I get errors like that, they usually clear up when I try again even just a few minutes later.

---

### Post by flocculant on 2015-10-21
It installed fine in 2 vm's installed today with the current iso's - not Gnome, though that shouldn't be an issue.

---

### Post by mc4man on 2015-10-21
libcairo-perl is in universe so make sure it's enabled. That package hasn't been updated since april so not like it's a new vversion somewhere.
Overall synaptic works but due to no Ubuntu side care is slowly falling apart.

---

### Post by ventrical on 2015-10-21
> **mc4man said:**
> libcairo-perl is in universe so make sure it's enabled. That package hasn't been updated since april so not like it's a new vversion somewhere.
Overall synaptic works but due to no Ubuntu side care is slowly falling apart.

It is becoming less and less. Obviously snappy and convergence are drawing most resources previously committed elsewhere.

---

### Post by mc4man on 2015-10-21
> **ventrical said:**
> It is becoming less and less. Obviously snappy and convergence are drawing most resources previously committed elsewhere.
Well they should attempt for 16.04 to do right by Desktop install users. If need be hire a couple of people to help out.

---

### Post by ventrical on 2015-10-21
> **mc4man said:**
> Well they should attempt for 16.04 to do right by Desktop install users. If need be hire a couple of people to help out.

My sentiments exactly. err.. ummm .. what programming language do they usually use to write these programs?  Is it all lock-stepped? Perhaps I may be able to offer help. I see it in this way : that developers are using a clawing back method to parse out user_space items so that they do not have to re-write large libraries and depends... I mean maybe if a few of us were to offer up some help to debug some of these issues they are having we can have some of these dialog items and menus back for the Desktop experience.

In all fairness I can see where developers depend on the community for  helps with the different flavors and there always seems to be some new brain child that has to get adopted into the fold to bring up older machines and hardware - and this is where the resources get lost in translation. That means that  current resources have to get backstepped  to fix 'n tweak some dialog box that is misbehaving .. etc... and so younger developers as well as more senior developers get bored having to retrace over old ground so out comes the wood chipper and Occam's razor and we are stunned that our installs break after a point release ;)  I know .. it's not funny .. it's ridiculous.

I am on the snappy mailing list and I will tell all now that the largest sum of the parts of Canonical are working on IoT, Beagle Bone Black. RasberryPi Turbo with gadgets and snappy.  I am assuming that after the next Developers Symposium they will fork out an even share of resources back to convergence and desktop improvements.

Regards..

whoops .. my apologies .. I am way off topic here .

---

### Post by ronacc on 2015-10-21
lets hope so , they have just about wrecked ubuntus usefulness to me as it stands now .

---

### Post by QDR06VV9 on 2015-10-21
@mc4man +1
@ventrical +1
@ronacc +1

---

### Post by sammiev on 2015-10-21
> **sgage said:**
> Synaptic installed here without incident just a couple of days ago on a fresh install of Ubuntu Gnome. When I get errors like that, they usually clear up when I try again even just a few minutes later.

Install Synaptic a few days ago on a fresh install gnome 15.10 with no issues to report.

---

