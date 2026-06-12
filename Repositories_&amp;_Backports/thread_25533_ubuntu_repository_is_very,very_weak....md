---
title: "ubuntu repository is very,very weak..."
date: 2005-04-10
forum: Repositories &amp; Backports
---

### Post by Vertical on 2005-04-10
Hello. Just installed kubuntu 5.04 and found out that software repository in ubuntu is so weak, that I can't imagine how this distro can be so popular.
In FC/MDK I could use apt4rpm and DAG, freshRPMs, Newrpms, At and other gigantic repositories. And What did I find in ubuntu? "You can't use rpm repositories" - thare was the answer when I asked how to use DAG and all other repositories in debian-based systems.
So, are there any good repositories for apt?

[http://www.apt-get.org/main/](http://www.apt-get.org/main/) this link shows 3rd party repos, but Install every one of them to get only one software aviable to install is madness..

---

### Post by maqi on 2005-04-10
First of all ... wrong forum for this post - you really should read the stickies.

Second ... if you want rpms what are you doing using a debian based distro?

Hope this helps,
maqi :)

---

### Post by Spif on 2005-04-10
Have you enabled Universe and Multiverse in Synaptic?

---

### Post by Bob D. on 2005-04-10
[QUOTE=Vertical]Hello. Just installed kubuntu 5.04 and found out that software repository in ubuntu is so weak, that I can't imagine how this distro can be so popular.
In FC/MDK I could use apt4rpm and DAG, freshRPMs, Newrpms, At and other gigantic repositories. And What did I find in ubuntu? "You can't use rpm repositories" - thare was the answer when I asked how to use DAG and all other repositories in debian-based systems.
So, are there any good repositories for apt?

[http://www.apt-get.org/main/](http://www.apt-get.org/main/) this link shows 3rd party repos, but Install every one of them to get only one software aviable to install is madness..[/QUOTE]
<sigh>
Nice first post.  :roll:

Well, since the Ubuntu repositories (main, restricted, universe, and multiverse) mirror all of Debian's packages (.deb files, not .rpm) and beyond, my current check of available packages for Ubuntu is **16,277**. That's without the Marilatt repository active in my repo sources (for restricted items such as codecs, dvdcss, etc.).  And you can always try "alien" if there is some obscure RPM package that you just have to use that somehow isn't available as a DEB file.

So what exactly are you looking for that you can't find in the repos I just listed? If you actually want to look for yourself, read the Unofficial UbuntuGuide ([http://ubuntuguide.org/)](http://ubuntuguide.org/)), educate yourself, activate the universe and multiverse repos, and see what you can find.

Oh, and welcome to Ubuntu and UbuntuForums!  :grin:

Bob

---

### Post by az on 2005-04-10
"apt4rpm and DAG, freshRPMs, Newrpms, At and other gigantic repositories. And What did I find in ubuntu? "You can't use rpm repositories"

apt4rpm means "apt for rpm" as opposed to regular apt which is meant for debs.

---

### Post by c_dog on 2005-04-10
You're kidding me, right? This has got to be a troll statement. Sorry, Vertical,. April 1st has come and gone.

---

### Post by daniels on 2005-04-10
```
daniels@rookery:/srv/archive.ubuntu.com/ubuntu% find pool/ -name \*.deb | cut -f1 -d_ | sort -u | wc -l
18515
```

---

### Post by Leif on 2005-04-10
Is this for real ? Please consult ubuntuguide.org before taking shots at the software available - Ubuntu/Debian has a huge range, definitely more than most distros out there.

---

### Post by skoal on 2005-04-11
If it weren't for the 'search' button in Synaptic, I think I'd grow a beard while scrolling through the list...

---

### Post by KiwiNZ on 2005-04-11
I some times feel we are getting targeted by folks wanting to take a stab at Ubuntu.
I guess tall poppy syndrome . Ubuntu is growing so fast  that this will happen .

KiwiNZ looks for his box of padlocks

---

