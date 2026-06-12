---
title: "How Are You Putting Up With Ubuntu"
date: 2009-10-26
forum: The Cafe
---

### Post by Khakilang on 2009-10-26
I am a newbie to Ubuntu and I look I couldn't keep up with things like updates and installation software. I seem to get a lot of broken dependencies and error of such. I manage to solve a few here and there. But I lost my Open Office suite and I don't know how to get it back. Its gone missing from the panel. Do many of you facing this kind of problem and how to put up with it?:confused::confused::confused:

---

### Post by joeval on 2009-10-26
Nah man, never had any of that before.  What version are you using?

It might be worth backing up all your data and just doing a fresh install if it keeps acting up.  Or, wait a few days and then the stable release of Karmic is out, so update to that maybe.

---

### Post by RichardLinx on 2009-10-26
I have always found Ubuntu to be extremely stable on my machine, and updates haven't broken my system even once. Perhaps I've been lucky.

Are you using 9.04 or the 9.10 RC?

I don't know how else you could have such issues unless you removed some important dependancies manually through Synaptic/Apt.

---

### Post by mivo on 2009-10-26
My problems with Ubuntu were always with the installation and upgrades, but once it worked, it worked.  Linux does take more time investment than Windows, but it's hard to say that here without getting attacked. You learn more, though, and get a better understanding of the inner workings. Just use the available resources, like the forums here. There is a wealth of knowledge.

---

### Post by SunnyRabbiera on 2009-10-26
What version are you running and what applications werre giving you dependency issues?

---

### Post by Exodist on 2009-10-26
Dependency Issue? He may be trying to compile from source, or he is using SuSE and little confuzed.. :(

---

### Post by Khakilang on 2009-10-26
> **SunnyRabbiera said:**
> What version are you running and what applications werre giving you dependency issues?

Ubuntu 9.04. My problem is from Firefox, Helix player, Galeon, Xulrunner ( I think) and now Open Office. My Firefox now is solved, Helix player doesn't come out, Galeon-common always give error and so is Xulrunner. Actually I am using Ubuntu on my old notebook and see how it hold up on Linux and I am pretty impress but its performance. Even my die hard Window friends is impress.

I don't know whether it is the hardware problem. I try this command apt-get clean, -f install but no luck. Appreciate anyone who can help.

---

### Post by RichardLinx on 2009-10-26
I have always found Ubuntu to be extremely stable on my machine, and updates haven't broken my system even once. Perhaps I've been lucky.

Are you using 9.04 or the 9.10 RC?

I don't know how else you could have such issues unless you removed some important dependencies manually through Synaptic/Apt.

Edit:
Whoa, what the hell happened? That was weird.

---

### Post by MelDJ on 2009-10-26
> **Koh Kook Loon said:**
> I am a newbie to Ubuntu and I look I couldn't keep up with things like updates and installation software. I seem to get a lot of broken dependencies and error of such. I manage to solve a few here and there. But I lost my Open Office suite and I don't know how to get it back. Its gone missing from the panel. Do many of you facing this kind of problem and how to put up with it?:confused::confused::confused:

where do you live? maybe you can get help from other linux users in your country?

---

### Post by Pasdar on 2009-10-26
> **Koh Kook Loon said:**
> Ubuntu 9.04. My problem is from Firefox, Helix player, Galeon, Xulrunner ( I think) and now Open Office. My Firefox now is solved, Helix player doesn't come out, Galeon-common always give error and so is Xulrunner. Actually I am using Ubuntu on my old notebook and see how it hold up on Linux and I am pretty impress but its performance. Even my die hard Window friends is impress.

I don't know whether it is the hardware problem. I try this command apt-get clean, -f install but no luck. Appreciate anyone who can help.

When did these problems start occuring? When you started to uninstall and install new things? Did you use the Add/remove from the panel or did you manually install/remove things?

---

### Post by RichardLinx on 2009-10-26
> **Koh Kook Loon said:**
> I don't know whether it is the hardware problem. I try this command apt-get clean, -f install but no luck. Appreciate anyone who can help.

"apt-get clean, -f"? I don't think that will work on Ubuntu. I think you mean:
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```
That will only fix the problem if it's conflicting packages though. I still don't understand how you got this strange problem in the first place.

Check if Openoffice is still installed by launching it from the terminal:
```
openoffice.org
```

> Dependency Issue? He may be trying to compile from source, or he is using SuSE and little confuzed..
You haven't used openSUSE or any RPM based distro in a long time, have you?

---

### Post by John Bean on 2009-10-26
As others have posted I too find Ubuntu to be very stable, at least as stable as (say) Windows XP, but also I think that any distribution of Linux tends to attract a much larger proportion of enthusiasts who like to continually meddle with the system. This is not bad in itself and indeed is a good learning experience in the long term, but it can and does often cause instability in some of the components or even in the core system itself.

  Linux in general gives you the freedom to meddle to your heart's content to make the system personal to your needs, but with that freedom comes personal responsibility to keep it working smoothly. Ubuntu helps the non-technical user (or any non-meddler!) by standardisation  but by doing so increases the opportunity to break something by "doing your own thing" without due care and attention.

---

### Post by koshatnik on 2009-10-26
> **Koh Kook Loon said:**
> I am a newbie to Ubuntu and I look I couldn't keep up with things like updates and installation software. I seem to get a lot of broken dependencies and error of such. I manage to solve a few here and there. But I lost my Open Office suite and I don't know how to get it back. Its gone missing from the panel. Do many of you facing this kind of problem and how to put up with it?:confused::confused::confused:

I've yet to have a single dependency issue in 5 years of using ubuntu. For info please then we can help :)

---

### Post by RichardLinx on 2009-10-26
> **koshatnik said:**
> I've yet to have a single dependency issue in 5 years of using ubuntu. For info please then we can help :)

My first experience of dependency hell with Ubuntu was with 8.04 while trying to get AssaultCube 1.0 running. The game, even though it had been packaged for Ubuntu just wouldn't run. In the end after installing about a million random lib files it finally magically worked. :)

---

### Post by stinger30au on 2009-10-26
in almost 100% of the time when ubuntu o/s does something wrong on my pc

its cos *I* did something i wasnt supposed to do

so yeah, after all these years, ubuntu still puts up with *ME*

---

### Post by lordyosch on 2009-10-26
the only times I have had problems is when I caused them by fiddling with things. When I leave things alone and just update etc then it runs fine.


Jay

---

### Post by maflynn on 2009-10-26
I wouldn't say dependency hell but I've loaded some apps that seemingly loaded a ton of libs that I questioned as to the need.  My concern with ubuntu or any system, is that it loads crap on my system that I really don't need or it will introduce instabilities.

---

### Post by hoppipolla on 2009-10-26
> **Koh Kook Loon said:**
> I am a newbie to Ubuntu and I look I couldn't keep up with things like updates and installation software. I seem to get a lot of broken dependencies and error of such. I manage to solve a few here and there. But I lost my Open Office suite and I don't know how to get it back. Its gone missing from the panel. Do many of you facing this kind of problem and how to put up with it?:confused::confused::confused:

very, very odd, I've never had broken dependencies, well I had it ONCE when I was on the early version of Karmic and the package manager broke mid-installation lol, but that took what... one command to fix? heh :)

What's the problem man? Just go into Synaptic and it will make everything better fairly fast! :)

---

### Post by JillSwift on 2009-10-26
This is very odd. The only time I've had to fight with dependencies is when I'm compiling from source. APT is too good at its job otherwise.

---

### Post by speedwell68 on 2009-10-26
> **JillSwift said:**
> This is very odd. The only time I've had to fight with dependencies is when I'm compiling from source. APT is too good at its job otherwise.

In for years of using Ubuntu I can't think of one single dependency issue.

---

### Post by JoshuaRL on 2009-10-26
Alright buddy, try this:
```
sudo aptitude update
sudo aptitude safe-upgrade
```

Now, I love APT more than anyone.  In fact, I kind of refuse to go away from Debian-based because of it.  But sometimes, when there's weird problems going on, aptitude can fix it for you.  The Debian devs actually encourage aptitude usage on a daily basis instead of apt-get for exactly that reason.  If any conflicts or issues come up, it gives you application ratings and the choice of what to do.  Excellent package manager, my personal favorite.

---

### Post by SuperSonic4 on 2009-10-26
My problems with kubuntu come from bloat, default crapware installed, stuff I'd never use etc. Plus it didn't seem as stable as other distros

---

### Post by macogw on 2009-10-26
> **RichardLinx said:**
> 
You haven't used openSUSE or any RPM based distro in a long time, have you?

Is 2 years a long time? At least as of then, the update manager would tell you, one package at a time, that not all updates could be installed. So uncheck the one package..try again. It names another package. Uncheck it, and try again...It names another package. And on and on!

---

### Post by Khakilang on 2009-10-31
I think I try too much. You know installing some software and see how it work. Uninstall it than try other, than upgrade to the highest version. All sort of things. Experiment some. Nothing seriously since I am not using this laptop for my main work and I got back up. Now I try Karmic Koala and see how it works. Thanks for all your reply. Now I try do do what you advice. Anyway I am happy despite all thing my computer is free of virus.

---

