---
title: "[IDEA] You can import XP data from a fresh install, why not Ubuntu data?"
date: 2007-10-21
forum: Ubuntu Brainstorm
---

### Post by 1337455 10534 on 2007-10-21
People can do a dist upgrade via terminal, but what if their system is broken? What if there are files on their partition that could be salvaged, but there is no storage device available...
Ubuntu detects XP user accounts when installing Ubuntu.. why not Ubutnu ones?

In summation;
Detect Ubuntu accounts and offer to import their data from a fresh install.

---

### Post by Devz0r on 2007-10-21
Exactly.  Especially since it is recommended if one has a version that is more than two versions old that one does a fresh install.  This is especially true if people are staying with LTS releases.

---

### Post by SonicSteve on 2007-10-21
I was thinking this exact thing just 2 weeks ago. It makes complete and perfect sense.

---

### Post by screaminj3sus on 2007-10-22
yeah why would they implement the ability to import form windows but not other linux installs? wouldn't this be even easier than windows to implement??

---

### Post by 1337455 10534 on 2007-10-22
That makes... +4

---

### Post by smartboyathome on 2007-10-22
I thought it DID import stuff from Ubuntu installs. At least, it does for me as long as I am not overwriting the partition.

---

### Post by Twintop on 2007-10-22
> **smartboyathome said:**
> I thought it DID import stuff from Ubuntu installs. At least, it does for me as long as I am not overwriting the partition.
That's what I thought too, smartboyathome. When I upgrade or reinstall, I just don't format my /home partition and give myself the same username...that more-or-less imports all of my settings since Gnome and other apps still pull from the same file locations

---

### Post by m0eman on 2007-10-22
The migration assistant (i think is what its called) does have ubuntu as a category when your doing an install, but the options are very limited compared to those in the windows category.

Edit: I think the best approach to keep your settings is a seperate /home account. But for those who don't do that, or for people who don't know how, the migration assistant is helpful.

---

### Post by 1337455 10534 on 2007-10-22
I (we) meant doing a CD install and reformatting. ... I have never seen immigrate from XP option.

---

### Post by m0eman on 2007-10-22
When you install from the live cd, the migration assistant is one of the steps... (unless you don't have a XP or Ubuntu partition)

---

### Post by ryanVickers on 2007-10-22
You mean it doesn't already do this!?! Oh dear...

Well, then, I guess I'm saying great idea - someone get working on it :p

---

### Post by m0eman on 2007-10-22
> Migration-Assistant

Just in time for Feature Freeze, migration-assistant 0.3.1 was uploaded to main and the accompanying changes were merged into Ubiquity. Migration Assistant is a program that ties into Ubiquity and Debian Installer, and allows users to import documents and settings from their previous operating systems and convert them into their Ubuntu equivalents during a dual-boot installation. 

[http://www.ubuntu.com/testing/herd4](http://www.ubuntu.com/testing/herd4) (It's existed since feisty)

And it does have support for existing ubuntu partitions (though limited).

---

### Post by exile on 2007-10-22
nice idea +1 from me

---

### Post by Amon_Re on 2007-10-24
I don't see why this can't be done, "all" that's needed is to shove everything into an /OldInstall dir, install in / without formatting, move over the /OldInstall/home to /home and import the file with the users from /etc (iirc?)

I don't understand why that option is missing

---

