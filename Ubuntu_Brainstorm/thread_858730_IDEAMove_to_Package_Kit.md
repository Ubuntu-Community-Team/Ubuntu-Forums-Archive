---
title: "IDEA:Move to Package Kit"
date: 2008-07-13
forum: Ubuntu Brainstorm
---

### Post by sicofante on 2008-07-13
I would like to suggest Ubuntu uses Package Kit in Intrepid Ibex.

Why?

1- Because it really looks like a simple upgrade from "Add/Remove..." so it won't disturb old Ubuntu users.

2- Because it makes Linux more of a platform by being "backend independent", so more distros will look alike from a user's point of view. What's good for Linux in general is good for Ubuntu.

3- Because it has both GTK and QT interfaces, so both Gnome and KDE users will feel at home.

4- Because it might finally become a single software for managing simple AND advanced package management tasks, maybe removing in the future the duality of "Add/Remove..."+Synaptic. While PackageKit evolves, though, there's no reason to remove Synaptic.

5- Of course, because it's more powerful than "Add/Remove..." while [keeping it simple]("http://en.wikipedia.org/wiki/KISS_principle").

---

### Post by psyke83 on 2008-07-13
> **sicofante said:**
> I would like to suggest Ubuntu uses Package Kit in Intrepid Ibex.


Does PackageKit have robust apt/deb support, though? I've used it in Fedora 9 and while it does obey the KISS principle, it obeys it too strictly ;). It could certainly replace Add/Remove, but most certainly not Synaptic in its current form.

---

### Post by RAOF on 2008-07-13
And the really, really big *Why not*s would be:
*) that the apt backend needs quite a lot of love, and 
*) that PackageKit, by design, is unable to handle some debian packages[1].

It seems unlikely that PackageKit will be able to fully replace the existing tools in the short term, and maybe not ever.  Also, my PackageKit experience on Fedora 9 was that it took quite a long time to do anything, that you could only do one operation at a time, and that there wasn't a lot of feedback.

With some improvements it could possibly replace Add/Remove.  I think it's unlikely to replace Synaptic/Adept in the next couple of years.

[1] Some (not very many) .deb packages get configuration from stdin.  There aren't a lot of them, and there are better ways to get configuration, but last I heard on this PackageKit's design essentially forbade this from working.

---

### Post by Eclipse. on 2008-07-13
Over time it will eventually take over add/remove I think but as for the now its still pretty slow and like said the apt backend still isnt in great shape.

---

### Post by sicofante on 2008-07-13
I don't really know the current status of apt support in PK, but that's one area where Ubuntu devs or Canonical itself might contribute.

---

### Post by plun on 2008-07-14
Well.. PackageKit is already within Intrepid.

Apparently its going to be used for some functions
such as for Jockey.

It gives "seg faults" for the moment.  (bug filed)

Martin P apparently also works with this.

[http://martinpitt.wordpress.com/2008/07/11/argh-dbus-python/](http://martinpitt.wordpress.com/2008/07/11/argh-dbus-python/)


Have not seen any blueprint for this...:confused:

---

### Post by PmDematagoda on 2008-07-14
> **RAOF said:**
> It seems unlikely that PackageKit will be able to fully replace the existing tools in the short term, and maybe not ever.  Also, my PackageKit experience on Fedora 9 was that it took quite a long time to do anything, that you could only do one operation at a time, and that there wasn't a lot of feedback.

Those are the biggest reasons why I don't like Package Kit, it looks like it is capable of quite a lot, but at it's current state it just cannot compare to Update Manager and Synaptic together.

---

### Post by olskar on 2008-07-14
> **plun said:**
> 

Have not seen any blueprint for this...:confused:

[https://blueprints.launchpad.net/ubuntu/+spec/packagekit-intrepid](https://blueprints.launchpad.net/ubuntu/+spec/packagekit-intrepid) :)

---

### Post by plun on 2008-07-14
> **olskar said:**
> [https://blueprints.launchpad.net/ubuntu/+spec/packagekit-intrepid](https://blueprints.launchpad.net/ubuntu/+spec/packagekit-intrepid) :)

Thanks...  didn't go down to  low priority  :)

[https://blueprints.launchpad.net/ubuntu/intrepid](https://blueprints.launchpad.net/ubuntu/intrepid)

One essential issue must be to remove the GUI entrance
for PackageKit if its not possible to use.

Its a terrible mess for the moment with different GUIs.

Perhaps Gnome 2.24 fixes this ?

---

### Post by sicofante on 2008-07-14
> **PmDematagoda said:**
> Those are the biggest reasons why I don't like Package Kit, it looks like it is capable of quite a lot, but at it's current state it just cannot compare to Update Manager and Synaptic together.
Agreed. The point is, since Fedora now uses it we can expect a push on its development, and I think it's undeniable that the idea and design are impeccable and it just has to mature. If it has gone far enough to substitute "Add/Remove..." and Update Manager in Intrepid (let's say by early October), I still sustain it's a better option and should be considered. Let's keep a big eye on it.

---

### Post by zekopeko on 2008-07-16
i tried PK in fedora and it was a dreadful experience. so was the rest of the distro.

---

