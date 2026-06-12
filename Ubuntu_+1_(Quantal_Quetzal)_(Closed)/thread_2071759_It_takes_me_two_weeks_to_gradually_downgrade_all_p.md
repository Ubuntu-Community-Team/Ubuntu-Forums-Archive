---
title: "It takes me two weeks to gradually downgrade all packages from ricotz and gnome3 ppa"
date: 2012-10-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by funicorn on 2012-10-16
About 2 or 3 weeks ago I added ricotz-stable ricotz-testing and gnome3 ppa repository and did the upgrade, after which I got to see system inconsistencies here and there. As a result I had to downgrade some package to the official release from time to time. Till today I found all packages from above three ppa's have been downgraded and replaced with the officials. And my desktop goes normal again.

So it's a negative experience from which others should learn that gnome3 has gone apart from Unity to certain extent, in terms of the inconsistent gnome desktop utilities such as gnome-settings-daemon and gnome-control-center etc. Anyone used to switch between the two should be more careful about package upgrade, especially those serving as desktop basics.

For one example, gnome-settings-daemon 3.6.0 from gnome3 official release cannot work normally under Unity. In my case it crashes every time on pressing Fn+left/right arrow tuning screen brightness,  sometimes even on power supply switching from AC to Battery. 

So there is good reason for Ubuntu to prevent certain packages from upgrading to gnome 3.6.0 versions. Try not to geek it.

---

### Post by dino99 on 2012-10-16
thats how noobs learnt :P

and you seems to have better knowledge now  :)

that explain why ubuntu devs have so huge hard work to make packages working together (ubuntu is for humans) compared to pure vanilla ones.

---

### Post by Frogs Hair on 2012-10-16
I went a little crazy with PPAS on my first release . I stay away from desktop environment PPAS  with the exception of E17 because it's simple to remove. If I get curious about the next release I beta test the new release and 12.10 comes with Gnome 3.6. Installing and removing the other Ubuntu DEs was another learning experience I had to go through also. You definitely should avoid experimenting with an operating system you need to get work done with.   :)

---

### Post by cariboo on 2012-10-16
@funicorn, do you know about ppa-purge? It's a wonderful package, that automagically removes a ppa, and replaces the experimental packages with the packages from the repositories.

---

### Post by funicorn on 2012-10-16
I know that thing, just don't trust it. It takes long to work things out, and is liable  to fail for random reasons.  It's obviously a waste of time to update whole apt repository and wait 10 minutes just for preparing to downgrade 5  packages. I'd rather downgrade manually for single ppa. Generally this may lead to dependency problems, but it could be done with awareness of dependency itself, i.e., not to downgrade one package, but a bunch of them.

---

### Post by sgage on 2012-10-16
"So it's a negative experience from which others should learn that gnome3 has gone apart from Unity to certain extent"

I think you have that backwards - it's Unity that has gone apart from Gnome 3.

---

### Post by xebian on 2012-10-16
Instead of 2 weeks downgrading, you could have just installed fresh in minutes.

---

### Post by Harry33 on 2012-10-17
> **funicorn said:**
> About 2 or 3 weeks ago I added ricotz-stable ricotz-testing and gnome3 ppa repository and did the upgrade, after which I got to see system inconsistencies here and there. As a result I had to downgrade some package to the official release from time to time. Till today I found all packages from above three ppa's have been downgraded and replaced with the officials. And my desktop goes normal again.

So it's a negative experience from which others should learn that gnome3 has gone apart from Unity to certain extent, in terms of the inconsistent gnome desktop utilities such as gnome-settings-daemon and gnome-control-center etc. Anyone used to switch between the two should be more careful about package upgrade, especially those serving as desktop basics.

For one example, gnome-settings-daemon 3.6.0 from gnome3 official release cannot work normally under Unity. In my case it crashes every time on pressing Fn+left/right arrow tuning screen brightness,  sometimes even on power supply switching from AC to Battery. 

So there is good reason for Ubuntu to prevent certain packages from upgrading to gnome 3.6.0 versions. Try not to geek it.

Well well,
- do you mean by "gnome3" this PPA: Gnome3 Team
  ([https://launchpad.net/~gnome3-team/+archive/gnome3)?](https://launchpad.net/~gnome3-team/+archive/gnome3)?)
- what is exactly ricotz-stable ppa?
- ricotz-testing is (I think) Gnome Testing PPA
   ([https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing))

I can find gnome-control-center_3.6.1 and gnome-settings-daemon_3.6.1 from ricotz staging PPA ([https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging)),
but not from gnome3 ppa.

The 3.6.1 versions work well with Gnome-shell DE. It is, however, a known issue that they do break Unity DE. But is it a Unity issue, I do not know.

---

