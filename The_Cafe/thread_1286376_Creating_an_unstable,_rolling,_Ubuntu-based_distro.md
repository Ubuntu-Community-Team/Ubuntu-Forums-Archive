---
title: "Creating an unstable, rolling, Ubuntu-based distro?"
date: 2009-10-08
forum: The Cafe
---

### Post by sertse on 2009-10-08
Being an avid Debian Sid (and Sidux) user, but preferring Ubuntu due to the way things are going, I'm wonder if anyone is interested in making an rolling, unstable ubuntu based distro?

Some notes: 

We continually base ourselves to "Ubuntu+1" upgrading to it as soon as it becomes available.  

For common apps which have PPAs which offer even more updated versions of things, we switch to that 

We build off from the mini.iso as a starting point.The default desktop should be kept as simple as possible (modular), to minimise breaks and the chance one thing can take out the whole system. Xfce? Lxde? A bit of mix and match perhaps.

The purpose is to have a setup for someone who isn't afraid of having absolutely the latest things, (In many ways, Ubuntu +1 and PPA is even more ahead of Sid, particular for end user apps you actually use/care about) while keeping the familiarity of Ubuntu etc. Another point is that while sid, sidux etc all ask you to use the command line for upgrades etc (and one of their greatest comments about it), Ubuntu + 1  is a base where it was made with you using a gui in mind, which is convienent for many users. 

Thoughts?

---

### Post by madjr on 2009-10-08
a rolling release would be cool

you could probably also use sid or sidux as a base and port over ubuntu or mint tools to make it more user friendly

but using ubuntu +1 and a bunch of ppas (similar to ubuntu-tweak) would not be bad either

---

### Post by Xbehave on 2009-10-08
This has been discussed to hell and back recently, basically
*Most users are happy with Cyclic releases
*However some users would use a PPA that contains the latest versions of popular user apps (firefox, pidgin, etc),
*That sort of thing aint coming from canonical any time soon

I think the best way for you guys to go forward is to create a latest-PPA that you can add to your repo list to install the latest firefox and/or gimp, etc (key part there being OR so just adding the repo will not overwrite firefox AND gimp, I think thats best achived by packaging stuff in the "latest-PPA" as firefox-latest, gimp-latest, etc). However that idea still leaves you with a stagnant base.

If you want a fully Rolling Release I do have to ask why you thing adding a rolling release to ubuntu would be better than porting ubuntu style tweaks to sidux?

---

### Post by Dimitriid on 2009-10-08
Start from a base Arch system instead, I'd be easier to incorporate some of the Ubuntu features ( graphical install, live cd, etc ). 

In fact im certain something like this already exists, I'd be just a matter of switching from pacman to apt-get if you really want to be compatible with ubuntu repositories.

---

### Post by joey-elijah on 2009-10-08
Isn't this what the foresight distro is?

[http://www.foresightlinux.org/five-reasons-to-use-foresight-linux/](http://www.foresightlinux.org/five-reasons-to-use-foresight-linux/)

---

### Post by CJ Master on 2009-10-08
> **joey-elijah said:**
> Isn't this what the foresight distro is?

[http://www.foresightlinux.org/five-reasons-to-use-foresight-linux/](http://www.foresightlinux.org/five-reasons-to-use-foresight-linux/)

To the best of my knowledge it's not based on Ubuntu. :)

...plus, Conary is a pain in the butt.

---

### Post by joey-elijah on 2009-10-08
> **CJ Master said:**
> To the best of my knowledge it's not based on Ubuntu. :)

...plus, Conary is a pain in the butt.

Doh! You're right! My bad. Wasn't thinking

---

### Post by Xbehave on 2009-10-09
> **Dimitriid said:**
> Start from a base Arch system instead, I'd be easier to incorporate some of the Ubuntu features ( graphical install, live cd, etc )
damn arch fans :shakes fist: :P, I think sidux is a much better base to start from as it already has
[LIST]
[*]apt-get
[*]graphical installer
[*]live cd
[*]etc
[/LIST]

---

### Post by snowpine on 2009-10-09
A rolling release version of a stable distro based off a rolling release distro? My head hurts. ;)

---

### Post by tghe-retford on 2009-10-09
And to just to make your heads spin even further, I wouldn't mind seeing a choice of either rolling release for testers and developers and a rolling release of software when it is stable, but with all the support of Ubuntu and the community.

---

### Post by snowpine on 2009-10-09
Ubuntu already *is* rolling release... it just rolls slowly (like, it makes a complete revolution every six months). ;)

---

