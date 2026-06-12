---
title: "Webkit Browser For Gnome?"
date: 2009-03-25
forum: The Cafe
---

### Post by myusername on 2009-03-25
I am currently looking for a good, stable webkit  based web browser for gnome (perferably with an adblocker but not a necessity). Im using Arora right now and its pretty good but im looking for a better one. (Don't turn this into a flame war about how i should use firefox/opera/some crazy web browser nobody has heard of in wine)

---

### Post by ghindo on 2009-03-25
I know that Epiphany is working towards a WebKit backend, but I'm not sure if it's stable yet.

---

### Post by SpriteSODA on 2009-03-25
hmm, Opera10 is not webkit, but it does pass the Acid3 test 100/100 plus is a very modern browser with tons of features, and by benchmark it has double the speed of my firefox.

---

### Post by mcduck on 2009-03-25
Epiphany-webkit is in the repositories, although I wouldn't call it very stable.. (at least not the version available for 8.10)

---

### Post by Closed_Port on 2009-03-25
Give midori a try. It's really getting quite good lately:
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

As it can use userscripts, you also might be able to get some adblocking working, though I haven't really tried it.

---

### Post by Naiki Muliaina on 2009-03-25
+1 Midori, love it :)

---

### Post by ghindo on 2009-03-25
Midori isn't exactly "stable" at the moment, especially the version(s) in the Ubuntu repositories.

---

### Post by Closed_Port on 2009-03-25
> **ghindo said:**
> Midori isn't exactly "stable" at the moment, especially the version(s) in the Ubuntu repositories.

Well, use the one from the ppa I linked to. It's very stable for me.

---

### Post by artir on 2009-03-25
Epiphany is the way to go. Try it in Jaunty, is quite stable.

---

### Post by chucky chuckaluck on 2009-03-25
> **ghindo said:**
> Midori isn't exactly "stable" at the moment, especially the version(s) in the Ubuntu repositories.

and in order to retain cookies between sessions, it needs to be compiled with libSoup 2.25.2 or newer, is my understanding.

---

### Post by gnomeuser on 2009-03-25
The first webkit only release of epiphany will be 2.27.x from then on, where we are going we don't need no geckos.

---

### Post by luc0zade on 2009-04-15
I realise this may be so obvious that I should have worked out the answer myself, but is it possible to install a 2.27.x package for epiphany-webkit in older releases, e.g. Hardy and Intrepid ?

The webkit-team PPA linked in a previous post currently includes epiphany-webkit-2.27.1-1 for Jaunty, but with Intrepid, getting epiphany from the Ubuntu universe repository using Synaptic only installs 2.24.1-0ubuntu1.

I appreciate nightly builds can be compilied from source but is the more up-to-date package only available for Jaunty ?

---

### Post by gnomeuser on 2009-04-15
> **luc0zade said:**
> I realise this may be so obvious that I should have worked out the answer myself, but is it possible to install a 2.27.x package for epiphany-webkit in older releases, e.g. Hardy and Intrepid ?

The webkit-team PPA linked in a previous post currently includes epiphany-webkit-2.27.1-1 for Jaunty, but with Intrepid, getting epiphany from the Ubuntu universe repository using Synaptic only installs 2.24.1-0ubuntu1.

I appreciate nightly builds can be compilied from source but is the more up-to-date package only available for Jaunty ?

It depends, if epiphany 2.27.x depends on new functionality in gtk or glib e.g. then you would have to backport these in the PPA. Doing this is not simple and it greatly harms QA for the stable release. If it does not, then chances are good that a PPA build could work very well.

---

