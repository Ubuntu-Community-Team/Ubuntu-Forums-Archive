---
title: "Multimedia HOWTO Help"
date: 2004-12-15
forum: Repositories &amp; Backports
---

### Post by ankitmalik on 2004-12-15
Hi!

Just caught hold of the Ubuntu Multimedia HOWTO and ... thanks!

But I am stuck now!

I am at the step $ sudo apt-get install x-window-system-dev! and have run into probs!

> root@tuxido:/home/maliks # apt-get install x-window-system-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  x-window-system-dev: Depends: libxrandr-dev but it is not going to be installed
E: Broken packages
root@tuxido:/home/maliks # apt-get install libxrandr-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxrandr-dev: Depends: libxrender-dev but it is not installable
E: Broken packages
root@tuxido:/home/maliks # apt-get install libxrender-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Package libxrender-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxrender-dev has no installation candidate
root@tuxido:/home/maliks # 

______________________________________________________________________

---

### Post by adbak on 2004-12-15
Are all of your repos enabled?  I don't think you need Universe, but I may be wrong about that.

---

### Post by ankitmalik on 2004-12-16
Yes I have all the repos (universe, security etc.) of ubuntu selected.

Please help me as the mplayer from merriliat repo doesn't work for me!

---

### Post by randy on 2004-12-16
Are you running Hoary or Warty?

---

### Post by adbak on 2004-12-16
The Marillat repo no longer has a functional MPlayer, but I do have some of the .debs from when it did work.  If you want, I can try and send them to you via email, but I don't know if I'll be able to since they are rather large files.

PM me or send me an email @ adam, dot, m, dot baker (at) gmail dotcom if you're interested.

---

### Post by p!=f on 2004-12-16
Does```
sudo apt-get install x-dev
``` work?

Can you post your /etc/apt/sources.list here?

Does```
sudo apt-get update
``` correct the problem?

What```
apt-cache policy libxrandr-dev
``` returns?

---

