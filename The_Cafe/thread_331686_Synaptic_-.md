---
title: "Synaptic - ???"
date: 2007-01-04
forum: The Cafe
---

### Post by BarfBag on 2007-01-04
For package management, I've always used apt-get or aptitude.  It gives me more detail - which I like.  Recently, I've been running into tiny problems which bugged the crap out of me.  For example, the issue I had with Xine.  The picture was all messed up when there was a lot of movement in the video.  This evolved into a bigger problem, where Xine didn't work at all.  I don't feel like going into details.  I reinstalled the apps that were causing trouble through Synaptic, and the problems are GONE!  I also reinstalled Beryl through it (out of curiosity), and it's running much smoother and annoying little bugs have cleared up.  What's going on here?  What does Synaptic do that's different from aptitude?  :confused:

---

### Post by aysiu on 2007-01-04
Synaptic acts more like *apt-get* than *aptitude*.

*aptitude* is pretty smart about dependencies but sometimes isn't as smart as it thinks it is, and it'll bring in dependencies you don't want or remove a bunch of things you do want.

If you're using Edgy, I'd recommend *apt-get*, as *apt-get autoremove* allows you to remove unused dependencies along with an application (one of the main selling points of *aptitude*).

---

### Post by maniacmusician on 2007-01-04
if apt-get becomes as smart about dependencies than aptitude, I'll start using it again...it's faster at least.

---

### Post by seijuro on 2007-01-04
my memory of synaptic is getting fuzzy but as for adept you can watch all the "details" just like running apt-get in terminal simply by clicking the details button perhaps there is a view like this for synaptic as well.

---

### Post by ice60 on 2007-01-05
this is abit off topic, but i use smart in suse and if you look at the credits it says this -
> Canonical Ltd. - Funding Smart development since September of 2005.
i heard mark s. say ubuntu may well start using smart soon, but i didn't realise Canonical was funding the development until i saw that the other day.

is the main smart dev one of the old synaptic devs? i thought i heard something like that. i haven't had any problems with smart at all in about 6 months of using it.

---

### Post by mykalreborn on 2007-01-05
> **ice60 said:**
> this is abit off topic, but i use smart in suse and if you look at the credits it says this -

i heard mark s. say ubuntu may well start using smart soon, but i didn't realise Canonical was funding the development until i saw that the other day.

is the main smart dev one of the old synaptic devs? i thought i heard something like that. i haven't had any problems with smart at all in about 6 months of using it.

hmm:-k  ineresting. i had suse a while ago and smart sure makes your life easier :D

---

### Post by slimdog360 on 2007-01-05
> **aysiu said:**
> if you're using Edgy, I'd recommend *apt-get*, as *apt-get autoremove* allows you to remove unused dependencies along with an application (one of the main selling points of *aptitude*).
I thought that that was a new feature of apt-get, I just didnt want to say anything just incase it wasnt and I looked like a fool.

---

