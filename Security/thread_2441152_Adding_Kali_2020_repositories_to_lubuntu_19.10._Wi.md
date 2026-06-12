---
title: "Adding Kali 2020 repositories to lubuntu 19.10. Will it work?"
date: 2020-04-20
forum: Security
---

### Post by lxflow-1 on 2020-04-20
It's been about 10 years since I used Ubuntu, and I was by no means an expert. But recently my windows box got a pretty serious worm and since I don't game anymore I decided to try Lubuntu 19.10. I'm in the process of changing all my passwords and re-organizing my accounts. Kali's tools easily installable through their meta-packages in their repositories would be good to use to check out my computer from the an attackers perspective to better lock it down. 

Is it possible to simply add Kali repositories in sources.list and download pen testing software that way? I want to use Lubuntu and have the tools available whenever with no rebooting or virtualization.

Thanks you have a good day

---

### Post by guiverc on 2020-04-20
I'm don't really know Kali (I think of it in terms of being Debian), but I know Debian and Ubuntu packages do not align, even if you only consider release time (which is very much **oversimplifying** the issues involved). 

I'm on Ubuntu *focal fossa* currently, and will bump myself to 20.10 this month (as this box stays on the Development release), but packages still do not align with my Debian sid/bullseye box (closest Debian to my Ubuntu). 

Adding sources alone will cause your system to upgrade packages to the latest version of that package from either OS, meaning you'll have a *frankensystem*. You won't be able *release-upgrade* when you need to (don't forget 19.10 isn't far from EOL), and will likely have other issues (I'm basing this on Debian & Ubuntu packages, and not Kali).

I don't know what's in Kali repositories, and if you'll only get their own packages (do they provide only their modified packages, or the Debian ones too?), but I'd expect it to be a minefield, so be aware you'll need to nuke & clean install every time you need to *release-upgrade (and I'd expect dep-hell issues)*.

I had a look at [https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/](https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/) and don't see that they use Debian, but would not expect different to what I'm* suggesting.*

---

### Post by EuclideanCoffee on 2020-04-20
It appears to be the case that you can do this if you follow some rules.

Understandably, you missed this [thread]("https://ubuntuforums.org/showthread.php?t=2435914"). I'll just quote it and link to this thread.

[QUOTE=deadflowr]
I think this really stems from the fact that the kali repos are meant to  be added and discarded after you install whatever kali packages you are  going to use.
Kali warns of this (sort of)
From [https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/](https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/)

I believe that works in reverse as well, so adding kali to another distros repo lists breaks the other system too.
Also katoolin warns to remove the kali repos before ever doing any system updating
From [https://github.com/LionSec/katoolin#warning](https://github.com/LionSec/katoolin#warning)

A possible fix is to remove the lists files from /var/lib/apt/lists and  disable the kali repos (as well as remove one of the duplicate entries.)
Once you remove the lists files they get regenerated when you run an apt update.

Unfortunately, I'm not sure what happens if by chance you have done an  update with the repos enabled, but I don't think it can be good.[/QUOTE]

So add the repository, install the packages you want, and then remove it.

---

