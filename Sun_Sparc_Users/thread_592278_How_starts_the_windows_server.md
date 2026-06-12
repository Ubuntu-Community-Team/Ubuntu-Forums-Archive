---
title: "How starts the windows server?"
date: 2007-10-26
forum: Sun Sparc Users
---

### Post by gnikol on 2007-10-26
Hi, 
I installed Ubuntu on a Sun sparc ultra 60 
The machine boots normally but it brings me to command line 
How can I start the windows server?

---

### Post by netztier on 2007-10-26
> **gnikol said:**
> Hi, 
I installed Ubuntu on a Sun sparc ultra 60 
The machine boots normally but it brings me to command line 
How can I start the windows server?

You can't, because it's not installed by default. Ubuntu-Sparc is a server-oriented distribution and for this reason it doesn't have a graphical UI.

However, you can manually install one of the packages **ubuntu-desktop**, **kubuntu-desktop** or **xubuntu-desktop** with this command:

```
sudo aptitude install ubuntu-desktop
```

This will download a large number of packages (~300, if I remember correctly) and will take some time to install. A warning however:

[LIST]
[*] Depending on which graphics card you have, configuration of X.org can be easy, difficult or even impossible. 
Search the forum for advice, there have been a few questions about it.
[*] There is absolutely no 3D acceleration for any of the graphics cards that fit into a Sun Ultra. Your desktop is going to be quite slow to use.
[*] There are issues with GNOME and HAL. Some installations won't work and will always bring an error about "could not initialize hal".
[/LIST]

Try your luck

best regards

Marc

---

### Post by gnikol on 2007-10-29
Thanks

---

### Post by KRJ on 2007-12-07
> **netztier said:**
> You can't, because it's not installed by default. Ubuntu-Sparc is a server-oriented distribution and for this reason it doesn't have a graphical UI.

However, you can manually install one of the packages **ubuntu-desktop**, **kubuntu-desktop** or **xubuntu-desktop** with this command:

```
sudo aptitude install ubuntu-desktop
```

Try your luck

best regards

Marc

Thanks Marc.  I was wondering the samething myself and this tip helped me out.

Thanks,
Kevin.

---

