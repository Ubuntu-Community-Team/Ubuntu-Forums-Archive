---
title: "Garageband Equilivant"
date: 2008-09-17
forum: Ubuntu Studio
---

### Post by Neon612 on 2008-09-17
I've become fairly familiar with Garageband due to my school having mainly iMacs. I'd like to know if there is any Open Source (linux) based app that has the drag-and-drop loop type of interface.

And, also, if possible, could someone point me in the direction of a site with free, royalty free loops?

Thank you.

---

### Post by olskar on 2008-09-19
I have not used garageband but [http://www.ardour.org/](http://www.ardour.org/) would work I think

---

### Post by Patrick793 on 2008-09-19
I don't know about Garageband, but [LMMS](http://lmms.sourceforge.net/) is like FL Studio.

---

### Post by Neon612 on 2008-09-20
I've got LMMS, and it doesn't quite work out the way I'd like it to.

I've got Ardour as well, but I can't get it to start up. Something to do with JACK.

---

### Post by Neon612 on 2008-09-22
bump

---

### Post by paulg on 2008-09-23
> **Neon612 said:**
> 
I've got Ardour as well, but I can't get it to start up. Something to do with JACK.

From what I understand the capabilities of Ardour are more along the lines of Pro Tools, Logic, Cubase etc. You'll probably find there's a [steep?] learning curve but definitely worth it if you plan on doing recordings (or mixing or mastering or !?) for the long run. For Ardour you need to start JACK (JACK Audio Connection Kit) first to start Ardour. You should also install the realtime kernel (linux-rt) (you should really should be using linux-rt for any of these programs). This and some other Ubuntu Studio configurations are described [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation"). 

[Here's]("https://help.ubuntu.com/community/UbuntuStudio/") the general studio help and an [overview]("https://help.ubuntu.com/community/HowToJACKConfiguration") for configuring JACK.

Other programs you might be interested in are Hydrogen (drum machine/drum loops), Rosegarden (haven't used it but haven't use LMMS either and there may be some overlap here), jamin' (mastering - eq, compression, limiting). 

You haven't said what type of workflow you are trying to accomplish (e.g. live recording, sequencing). Some people might be able to recommend some workflows/programs to you. I use Ardour to do some recording/mixing/effects and route jamin into Ardour to master the final mix.

---

### Post by mondoUNC on 2008-09-25
Jokosher might suit your needs. It was recommended to me as a Garageband equivalent. I'm pretty sure its in the repos.

---

### Post by edajai on 2009-03-17
[http://www.jokosher.org](http://www.jokosher.org)

its awesome and very intuitive to use.

---

### Post by eric71 on 2009-03-17
> **edajai said:**
> [http://www.jokosher.org](http://www.jokosher.org)

its awesome and very intuitive to use.

I had given up on Jokosher a while back. Your post made me re-investigate. It looks like the 0.11 release has made a nice leap in functionality. I haven't tried it, but the fact that it can use jack now is big. Can't wait to give it a try. Wish I was still using Gnome, but what's a few extra libraries. With Qtractor and Jokosher coming along and new goodies coming to Ardour, home recording with linux looks like it has a bright future.

---

### Post by simtaalo on 2009-03-18
> **Neon612 said:**
> I've got LMMS, and it doesn't quite work out the way I'd like it to

how exactly do you want it to work? and do you have the latest 0.4.3 ver?

---

### Post by Stochastic on 2009-03-19
> **eric71 said:**
> I had given up on Jokosher a while back. Your post made me re-investigate. It looks like the 0.11 release has made a nice leap in functionality. I haven't tried it, but the fact that it can use jack now is big. Can't wait to give it a try. Wish I was still using Gnome, but what's a few extra libraries. With Qtractor and Jokosher coming along and new goodies coming to Ardour, home recording with linux looks like it has a bright future.

I'd also say Jokosher is the closest to a Garage Band equivalent.  I did find earlier releases quite buggy, and have yet to try 0.11.  But 0.11 is in Jaunty's repositories, so I'd wait until Jaunty comes out for that program, or compile it from source (there's probably debs floating around for hardy if you need them).

Audacity comes close, but I hate it.

LMMS really isn't garage band, but it's user friendly (also wait til jaunty or compile from source for this one).

Ardour can do anything - but takes some learning. (okay maybe not ANYTHING, but soon it will, sooon it wiiilll)

Qtractor I've never used, but from screenshots, should also be considered.

MusE might also be considered, but is kinda clunky for beginners I think.

The devil on my shoulder tells me I should mention ecasound as the ultimate garage band replacement. :twisted:

---

### Post by simtaalo on 2009-03-19
> **Stochastic said:**
> LMMS really isn't garage band, but it's user friendly (also wait til jaunty or compile from source for this one)


no need to compile from source, deb files here [http://ppa.launchpad.net/tobydox/ppa/ubuntu/pool/main/l/lmms/](http://ppa.launchpad.net/tobydox/ppa/ubuntu/pool/main/l/lmms/)

---

