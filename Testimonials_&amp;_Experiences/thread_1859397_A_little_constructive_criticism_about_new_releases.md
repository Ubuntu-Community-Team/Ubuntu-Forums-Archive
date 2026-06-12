---
title: "A little constructive criticism about new releases"
date: 2011-10-13
forum: Testimonials &amp; Experiences
---

### Post by someitalian123 on 2011-10-13
I think ubuntu should allow for unattended upgrades. Before left home today I saw that there was an upgrade available for 10.10 I clicked upgrade then I typed in my password hit enter and left home. I get home 3 hours latter to see a window asking me if I would like to start the upgrade now. Now I'm stuck here waiting for 1717 packages to download and apparently my computer has been doing nothing for three hours when I thought it was upgrading, this is very annoying and I think it needs to be fixed in 12.04.

---

### Post by cariboo on 2011-10-13
I'm not sure I'd let any operating system make major changes to my computer, without me authorizing it.

---

### Post by IWantFroyo on 2011-10-13
You're supposed to say you're sure **before** you go read a book or something.

What I hate about upgrades is the constant windows asking if you want to change this or that... I don't do upgrades anymore.

---

### Post by s.fox on 2011-10-14
Thread moved to [Ubuntu Testimonials & Experiences]("http://ubuntuforums.org/forumdisplay.php?f=103")

---

### Post by dniMretsaM on 2011-10-14
```
sudo apt-get --yes upgrade
```

This will automatically answer yes when it asks if you want to confirm the changes. This also works for removing, installing, dist-upgrading, etc. And this is not an Ubuntu thing, it's built into APT.

---

### Post by collisionystm on 2011-10-14
Upgrades take to long. backup your home folder and do a fresh install. 9/10 times an upgrade breaks your system anyways. Why take 5 hours to figure that out?

---

### Post by 3rdalbum on 2011-10-15
While I don't think the upgrade should have happened without your definite confirmation of what packages would be changed, I do think computers should be smarter.

After not seeing any user input for a few minutes, Update Manager should have queried the screensaver system using Dbus and discovered that there had been no user input to the whole system for a while. Assuming that the user had walked away from the system, it should have at least started downloading packages. That way, if it takes five hours for the user to return, all the packages are at least ready for installation.

Oh, and dist-upgrading works nine times out of ten. I've only had it fail once, and that was going to an early development version. My most recent upgrade, to Beta 1, worked pretty well perfectly.

---

### Post by Sef on 2011-10-16
> dist-upgrading works nine times out of ten.

Dist-upgrading has not been supported for years. Best to use the proper ways to upgrade.

---

