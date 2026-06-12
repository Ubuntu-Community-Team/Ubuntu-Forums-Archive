---
title: "PackageKit is horrible! Is everyone really so mislead?"
date: 2008-12-19
forum: The Cafe
---

### Post by Vadi on 2008-12-19
I thought PackageKit was the solution to one of the big problems in Linux - different package formats.

Turns out, I was wrong. It's nothing more but a GUI for all those different package formats. And no, it won't allow you to use them - if your system was .deb based before, it'll still be, if it was .rpm based, it'll still be. The only thing it adds is that people on a .rpm and .deb based system will have the same GUI.

And is this GUI even any good? Not when I tried it (just did on a fully updated Fedora 10). The application add/remove was done in a similar fashion to Ubuntu's Add/Remove (gnome-app-install) plus some obvious usability issues, like not being able to search in a category.

Personally, I'm horribly disappointed by this. It also claims "PackageKit is a system designed to make installing and updating software on your computer easier." - maybe it was hard on other distros, but on Ubuntu, I'd say the upgrading interface isn't exactly a problem (yes, interface, because packagekit won't fix your wireless after an upgrade).

So really, even if packagekit does manage to accomplish it's goal - provide 1 gui - it's solved a "not really pressing" problem.

Talk about disappointment :mad: 

[SIZE="1"](note: I thought for some reason that packagekit provided a feature to pause installation/upgrades for shutdownn and resume them at boot. However even after patiently reading the whole faq, I didn't find a single notice about it. Oh well, not like this is a big issue / bonus anyway)[/SIZE]

edit: to enlighten yourself, see [http://www.packagekit.org/pk-intro.html](http://www.packagekit.org/pk-intro.html) and [http://www.packagekit.org/pk-faq.html](http://www.packagekit.org/pk-faq.html).

---

### Post by bruce89 on 2008-12-19
> **Vadi said:**
> I thought PackageKit was the solution to one of the big problems in Linux - different package formats.

Turns out, I was wrong. It's nothing more but a GUI for all those different package formats. And no, it won't allow you to use them - if your system was .deb based before, it'll still be, if it was .rpm based, it'll still be. The only thing it adds is that people on a .rpm and .deb based system will have the same GUI.

[...]

Talk about disappointment :mad: 


I think that cross-distro UIs are a good thing, especially when it comes to things like codec / font installation. Previously, each distro would implement its own codec installer. Now, PackageKit can handle it on all distros (assuming Ubuntu see the light).

---

### Post by igknighted on 2008-12-19
The problem has nothing to do with deb vs. rpm... the problem is different distro's package things differently (as in, libraries are in different locations or broken up into different packages).  If those things were done the same, the package format (rpm, deb, etc) wouldn't matter at all.  So the solution is not that simple.

---

### Post by hanzomon4 on 2008-12-19
That's all package kit is? Can't be!

---

### Post by Rokurosv on 2008-12-19
I haven't had an issue with PackageKit so far, but when I'm installing breakable stuff, like the nvidia drivers, I use the command line.

---

### Post by Vadi on 2008-12-19
> **bruce89 said:**
> I think that cross-distro UIs are a good thing, especially when it comes to things like codec / font installation. Previously, each distro would implement its own codec installer. Now, PackageKit can handle it on all distros (assuming Ubuntu see the light).

The thing is though, I hope it "doesn't". Currently, PackageKit's UI is even worse than Ubuntu's :(

---

### Post by igknighted on 2008-12-20
> **Vadi said:**
> The thing is though, I hope it "doesn't". Currently, PackageKit's UI is even worse than Ubuntu's :(

1) It isn't done yet

2) Unless you are used to synaptic, it really really sucks.  Maybe packagekit isn't perfect, but I think starting fresh is better than trying to clean up a UI disaster.

---

### Post by Vadi on 2008-12-20
No, I don't use synaptic - it's "for advanced" users. I'm talking about Add/Remove and the Update Manager. Failing to see the ui disaster here really though. 

If it's not done, why is everyone pushing it so? I'm glad ubuntu devs are resisting the efforts to guniea pig test on ubuntu users *again*.

---

