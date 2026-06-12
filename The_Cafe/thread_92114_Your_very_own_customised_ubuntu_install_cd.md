---
title: "Your very own customised ubuntu install cd??"
date: 2005-11-18
forum: The Cafe
---

### Post by adam.tropics on 2005-11-18
A thought (it's rare so pay attention), travelling around the forums, and more often than not being moved around for posting in the wrong places!!), there are a huge number of postings relating to projects such as Arnieboy's automatix, plus things such as hardware drivers for video, sound etc etc. 

Now what would the difficultites be to offer an interactive setup  not unlike automatix, to customise the ubuntu download image. So that you went to a webpage, selected your exact hardware etc, and the use of the machine, and so downloaded a custom 'almost always fully working ootb'(!!) version of ubuntu specific to your needs. I would kind of imagine this would not be too impossible?? Probably not that useful, but it seemed a good idea when i considered it ! Really in terms of easing potential ex-windows users away from the dark side! (I personally have absolutely nothing against windows at all. I find that for me, the 'bespokeness' and cost of ownership of an individually setup linux system is preferable to the 'genericness' and expense of xp.Plus for my needs, it does everything i want, and quicker)

Any thoughts?

---

### Post by xequence on 2005-11-18
I thought of something similar to this awhile ago, and I was pointed towards PCLinuxOS. Aparently you can install it, then install and remove packages, and do a command to get an ISO you can burn to get a custom install.

---

### Post by adam.tropics on 2005-11-18
Had a look, seems to be based on [this project]("http://livecd.berlios.de/") and only good for mandrake/mandriva and PCLinuxOS installations. Unfortunately, it seems you have to install first, then make the future install cd, not really the point. Having said that, would be a useful backup tool, and distributed system installer (given identical architectures).

Really what I was getting at was a two-pronged attack!!

1)to download the ubuntu distro ensuring to include the ***specific*** (or i suppose more generic if there aren't any) drivers for your hardware. Have them be the ***default*** hardware setup, even if alternatives are there. (eg ati/mesa/fglrx/vesa, all work on my laptop, but I want specifically fglrx, which was not initially installed).

2)To allow someone to download for example the Ubuntu desktop, and only the programs they want to install. Then burn to cd. As opposed to downloading the lot, and then discarding half of it. Any extras after install can then be gotten live, as we know the correct drivers etc are there to get online (see 1)) and the more upto date versions are found online anyway.
If you burn the install cd and keep for backup/future installations, after a short time, the update after install will end up being so large you may as well start over!

The idea of the above is to firstly save bandwidth, phone bills, and time, and secondly, I honestly believe that it would lessen the fear many people have of linux installs (more common than you might think). Added to that, it is a feature that windows could never offer for a whole host of reasons. Windows gurus would say they don't have to, but to them i say come on, be honest, how many windows installs really go without a hitch, driver missing, computer restarting 50,0000 times, network issue....something. All OS's have install issues, just want to lessen them wherever possible.

---

### Post by az on 2005-11-19
That sounds like a project for Launchpad.net.

Progeny had tried to make something viable out of this.  A while ago they poured ressources into a debian graphical installer called PGI (Progeny Graphical Installer - PIGGY)

You would 
apt-get install pgi
edit the config file to reflect your install seed.
run it and it would download all the packages and makke a little repository for you.  It would then generate iso images for you with the installer on it.

[http://packages.debian.org/oldstable/admin/pgi](http://packages.debian.org/oldstable/admin/pgi)

I think they dropped development because it could only work with older debian systems.  They ditched it for Anaconda which they subsequently ditched.

Sounds like a good feature-request for launchpad, though.  The ubuntu installer scripts are accessible and AFAIK, it is somewhat straightforward to hack the seed files and build your own installer.  However, with Ubuntu-express and ubuntu-live, probably the favorite way to make a roll-your-own installer will be to install your system and then run the make-a-live-cd scripts.

For now, you can look at  how to make custom add-on cds.

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

I made that wikipage as part of this:
[http://ubuntuforums.org/showthread.php?p=504117](http://ubuntuforums.org/showthread.php?p=504117)

---

### Post by Arktis on 2005-11-19
Speaking for myself, I'd ***really*** like a tool like that.  As **adam.tropics** said, it would be a handy backup tool.

---

### Post by az on 2005-11-19
[QUOTE=Arktis]Speaking for myself, I'd ***really*** like a tool like that.  As **adam.tropics** said, it would be a handy backup tool.[/QUOTE]

While I have not tried this in a long time, it is supposed to clone your system onto a bootable cd for you.  I have not tried it since the 2.6 kernel came out.  I think it still works.

[http://packages.ubuntu.com/breezy/utils/bootcd](http://packages.ubuntu.com/breezy/utils/bootcd)

I am pretty sure that you will need this, too:

[http://packages.ubuntu.com/breezy/utils/bootcd-mkinitrd](http://packages.ubuntu.com/breezy/utils/bootcd-mkinitrd)

---

### Post by adam.tropics on 2005-11-19
> You would
apt-get install pgi
edit the config file to reflect your install seed.
run it and it would download all the packages and makke a little repository for you. It would then generate iso images for you with the installer on it.


Except of course ideally this would not only be a linux script.
If I know my hardware but only run windows, I still want to be able to download the custom install disc, burn it in windows etc etc

To be fair however, Ubuntu needs some credit on  this already. Not very many moons ago the idea of buying a new laptop, wiping it clean, and going straight to Linux of any sort would have typically involved a whole world of hurt! Now I can have this up and done in 3-4 hours. That's a hell of a leap right there.

---

### Post by adam.tropics on 2005-11-19
> [http://packages.ubuntu.com/breezy/utils/bootcd](http://packages.ubuntu.com/breezy/utils/bootcd)

I am pretty sure that you will need this, too:

[http://packages.ubuntu.com/breezy/utils/bootcd-mkinitrd](http://packages.ubuntu.com/breezy/utils/bootcd-mkinitrd)

It's on synaptic, so presumably dependacy taken care of. Will see how it goes......

---

