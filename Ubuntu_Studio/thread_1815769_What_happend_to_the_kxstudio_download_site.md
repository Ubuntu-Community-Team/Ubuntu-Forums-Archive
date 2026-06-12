---
title: "What happend to the kxstudio download site?"
date: 2011-07-31
forum: Ubuntu Studio
---

### Post by bikodog on 2011-07-31
I was tinkering around with a fresh install on another machine a few weeks ago. I installed lucid and then followed the handy guide on the kxstudio download page to add the kxstudio-gnome variety. Everything went well except that that box has a crummy soundcard etc.

With that trial run a success, I've backed up everything on my main box (with all the studio frills) and started over fresh. Now the page is down for an overhaul and i need the install sequence / repos.

Does anyone have a copy of the install instructions from the former download page? [http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/)

...hint hint falkTX :)

Thanks in advance!

---

### Post by akavir on 2011-08-01
I was bugging him a few days ago with this doing a fresh install.  The guys is really busy working on the new tools, but the first thing that probably have gone back up on the site was the install process.  I'll run down all the commands as I understand them.

Here are the PPA's you will need
**ppa:kxstudio-team/ppa**
[B]ppa:kxstudio-team/kxstudio
[/B]**ppa:kxstudio-team/latest(This one is not necessary, it's bleeding edge stuff.)**
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get update
sudo apt-get install kxstudio-desktop-gnome(or kde, lxde, unity)
sudo apt-get install kxstudio-meta-all

The last command will get all stable audio, plugins, graphics, and video apps.  There are more choices to not install everything, but I can't remember them off the top of my head.

P.S. @falkTX, I'd be happy to help you keep your site up to date and help take some pressure off!

---

### Post by bikodog on 2011-08-01
Thanks akavir, that's exactly what I needed!

---

