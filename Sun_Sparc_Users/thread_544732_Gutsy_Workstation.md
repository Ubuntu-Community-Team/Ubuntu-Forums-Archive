---
title: "Gutsy Workstation"
date: 2007-09-06
forum: Sun Sparc Users
---

### Post by jcastill on 2007-09-06
Hi, I installed gutsy beta to check the next release (as I always do, got my beta machine hehe) and as I only installed the minimum (net install) I decided to install "ubuntu-desktop"

Well, after making the "apt-get update ; apt-get install ubuntu-desktop"

I get the following error, "The following packages have unmet dependencies"
"gnome-power manager"
"gnome-session"

As I checked, the problem is directly "gnome-power-manager" that has this unmet dependency "libwnck18 >= 2.15.90"

I wonder if there's a way to check if this dependency would be met with Feisty repositories and how to use them (since this is beta I don't know if the package isn't there because of a bug OR because it's not made yet)

Any ideas?

Thanks

---

### Post by jcastill on 2007-11-26
It ended being a build error that was fixed and works on the final gutsy version.

---

### Post by zanderred on 2007-11-27
Hi, I had same problem, I got round this by installing Xubuntu desktop, configured the screen saver, power manger then installed ubuntu desktop, but have since done clean install with no problems.

---

### Post by moe_syzlak on 2007-12-07
What type of work do you guys/girls do on your Linux workstations?

---

