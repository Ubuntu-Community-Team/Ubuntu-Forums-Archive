---
title: "The psychology of Distros and Free Software"
date: 2008-01-22
forum: The Cafe
---

### Post by jeffus_il on 2008-01-22
Got to thinking about the psychology side, when I saw a recent thread where someone was determined a defrag a Linux file system. Despite many attempts to dissuade, there are still those determined to defrag, why? , the history of windows, the need to maintain, like regular car services, a need to satisfy oneself that one is a good computer owner, just like a good dog owner? I responded to the thread a little spicily, maybe too much so, I really don't want to hurt potential Ubuntians, This is what I wrote:
 > If someone feels an intense drive to defrag, maybe originating somewhere in the early childhood years, resulting from a negligent father who couldn't bring himself to defrag, simply do this, you need no extra software (compulsive installers are always looking for another piece of software to install, probably a result of strong marketing):[LIST]
[*]create a new temporary partition big enough to hold the content of the drive to be defragged.
[*]copy the whole filesystem to the new partition using a recursive copy which keeps permissions on files.      Code:
     cp -rpv /dir/source /dir/temp 
 r for recursive, p for preserve and v to keep your eyes busy while its alll happening.
[*]delete the original filesystem or create a new one on the same partition.
[*]copy the filesystem back using the same command reversed.
[*]the filesystem is now 100% defragged.[/LIST]Don't take this personally, some of my best friends have been known to defrag, I have also done it a few times, that's how I know how to do it, but I wouldn't admit it in public.
There's a mistake in the cp command, it needs a "*" somewhere.I also see a need to install more software, no matter if it's necessary or not. Of course this causes lots of  personal "suffering" and also is a weight on the forum support people, and also causes a lot of complaints about the product, which is really stable. Playing at the fringes with Alpha type software is not for the weak at heart. I wonder how much bandwidth on the forum has to do with  compiz, and eye candy issues, really unnecessary fancy partitioning issues, multiple booting just to try out another distro and so on.

Aren't most of us just overgrown kids looking for another toy to play with?

---

### Post by AnonCat on 2008-01-22
> I also see a need to install more software, no matter if it's necessary or not. Of course this causes lots of personal "suffering" and also is a weight on the forum support people, and also causes a lot of complaints about the product, which is really stable. Playing at the fringes with Alpha type software is not for the weak at heart. I wonder how much bandwidth on the forum has to do with compiz, and eye candy issues, really unnecessary fancy partitioning issues, multiple booting just to try out another distro and so on.

Aren't most of us just overgrown kids looking for another toy to play with?

Is there something wrong with customizing your personal computing environment to something you enjoy?  Some people enjoy the technical and novel challenges and experiences that come from pushing their computers in different directions in the same way some people enjoy sewing a new quilt or learning a new dance.  We all need some kind of "frivolous" pursuit to keep our sanity in this high-stress world that pounds the drums of productivity night and day.  People's willingness to play around wtih new software is a plus in my book since it brings many useful advances.  Linux likely wouldn't exist if Torvalds thought that tooling around at the fringes of software was a uselessm unproductive endeavour.

---

### Post by jeffus_il on 2008-01-22
No. nothing wrong, I do it myself. I have four desktops on my machine, Rox, Gnome, Xfce, and Kde, mainly to try and help people with problems and also because I'm inquisitive.

---

### Post by chewearn on 2008-01-22
For the longest time, I was stuck in Windowsboringland.  Then I jumped into Ubuntunirvana, and suddenly computer is exciting again.

But then, I ended up spending way to much time with my PC now, and way too little time on other things, like **spending* quality *time ****with the family**.

And I realised I have been installing too many things now compared to before, including full install of OS, and reinstallations.

Is it a bad thing?  I'm enjoying it too much to care.

---

### Post by keykero on 2008-01-22
Playing around with things has led me to an optimal setup for what I need to do (and that did include some of the compiz effects -- for example, I find the *true* transparency in terminal windows a boon to getting certain things done).  But I will continue the trial and error process to learn, experiment and continue to grow.

---

### Post by ExpatPaul on 2008-01-22
> **jeffus_il said:**
> Aren't most of us just overgrown kids looking for another toy to play with?

Yes. Great, isn't it :)

---

### Post by zcal on 2008-01-22
> **jeffus_il said:**
> I also see a need to install more software, no matter if it's necessary or not. Of course this causes lots of  personal "suffering" and also is a weight on the forum support people, and also causes a lot of complaints about the product, which is really stable. Playing at the fringes with Alpha type software is not for the weak at heart. I wonder how much bandwidth on the forum has to do with  compiz, and eye candy issues, really unnecessary fancy partitioning issues, multiple booting just to try out another distro and so on.

Debian Stable is good medicine for this type of compulsion.  Boy am I glad I broke that need-to-upgrade-every-six-months habit.  ;)

---

### Post by Darkhack on 2008-01-22
> **zcal said:**
> Debian Stable is good medicine for this type of compulsion.  Boy am I glad I broke that need-to-upgrade-every-six-months habit.  ;)

You don't need to update every six months on Ubuntu.  A standard release is supported for 18 months and a Long Term Support (LTS) release is supported for 36 months on the desktop.

---

### Post by zcal on 2008-01-23
> **Darkhack said:**
> You don't need to update every six months on Ubuntu.  A standard release is supported for 18 months and a Long Term Support (LTS) release is supported for 36 months on the desktop.

Good point.  Then again, I suppose you don't really *need* to upgrade every six months in between LTS releases either.  There are definitely a lot of people around here still using Feisty.  How long do those releases continue to get updates?

As far as Debian Stable vs Ubuntu LTS...I like the fact that I don't have to erase so much of my default Debian install (installing without the "Desktop Environment" option, that is) to set it up how I like it.  Starting with a cleaner palette and building from there is much more agreeable to me.  ...guess I *do* like to play with my toys then, eh?

---

### Post by aysiu on 2008-01-23
Non-LTS releases get security updates for 18 months after release. LTS releases get security updates for 36 months (for the desktop) or 60 months (for the server) after release.

---

