---
title: "Is the move to Unity-3d-only kill Qt development in Ubuntu?"
date: 2012-08-04
forum: The Cafe
---

### Post by IsraeliHawk on 2012-08-04
I was wondering - since Unity 2d is [likely to be dropped]("http://www.omgubuntu.co.uk/2012/05/uds-q-summary-bye-bye-unity-2d-hello-gnome-shell-spin") in Ubuntu 12.10 - what will be the future of Qt development within the Ubuntu ecosystem - such as Ubuntu TV and Ubuntu for Android?

cheers.

Uri

---

### Post by Dylan1473 on 2012-08-04
Doesn't KDE (used in Kubuntu) make heavy use of Qt? And that's just if you choose to look at major Ubuntu flavours. It's used in lots of places. I wouldn't be too worried about the death of Qt.

---

### Post by IsraeliHawk on 2012-08-14
> **Dylan1473 said:**
> Doesn't KDE (used in Kubuntu) make heavy use of Qt? And that's just if you choose to look at major Ubuntu flavours. It's used in lots of places. I wouldn't be too worried about the death of Qt.

Great to hear. Yet, do you think that the path of Unity as a Compiz plugin will eventually stabilize?

---

### Post by MadmanRB on 2012-08-14
By all accounts yes Ubuntu and Canonical is dropping a lot of QT support and its not a good thing as there are a lot of QT apps that are superior to GTK ones such as VLC, UMplayer, Clementine, Amarok, QMC2, the KDE plasma workspace in general (far more customizable, configurable and easy to use for newcommers then Gnome Shell or Unity) plus some proprietary apps like opera and skype are coded in QT so Canonical has pretty much fallen back on inferior GTK3 apps.

---

### Post by thatguruguy on 2012-08-14
> **MadmanRB said:**
> By all accounts yes Ubuntu and Canonical is dropping a lot of QT support and its not a good thing as there are a lot of QT apps that are superior to GTK ones such as VLC, UMplayer, Clementine, Amarok, QMC2, the KDE plasma workspace in general (far more customizable, configurable and easy to use for newcommers then Gnome Shell or Unity) plus some proprietary apps like opera and skype are coded in QT so Canonical has pretty much fallen back on inferior GTK3 apps.

What accounts are these, exactly? It would be neat if you could cite some sources.

---

### Post by vexorian on 2012-08-14
> **thatguruguy said:**
> What accounts are these, exactly? It would be neat if you could cite some sources.
Need studies to show KDE is easier to use for newcomers than Unity.

I don't see any reason at all to see Canonical dropping QT support. The deprecation of unity-2d was to avoid duplication of efforts. I wish they dropped the compiz plugin because unity-2d is more standalone. But I doubt it has anything to do with QT itself.

Canonical would prefer GTK apps as opposed to QT apps in the default , for the obvious reason that they integrate better with the gnome desktop ubuntu uses (unity is just a shell for gnome, most of the DE is still gnome)

---

### Post by rg4w on 2012-08-14
> **vexorian said:**
> I don't see any reason at all to see Canonical dropping QT support. The deprecation of unity-2d was to avoid duplication of efforts. I wish they dropped the compiz plugin because unity-2d is more standalone. But I doubt it has anything to do with QT itself.
When I asked Ted Gould about Unit 2D at UDS in May he didn't mention QT at all.  In fact, he did make a point of clarifying that Unity 2D isn't being dropped per se, but merely that its functionality is being rolled into the main Unity effort, so one project will provide the UI with greater similarity to each other than the current separate projects.

---

### Post by vexorian on 2012-08-14
What functionality exactly? Will I be able to run Unity-"3d" without compiz?

---

### Post by rg4w on 2012-08-14
> **vexorian said:**
> What functionality exactly? Will I be able to run Unity-"3d" without compiz?
"Unity 3D" describes how Unity is rendered under Compiz.  "Unity 2D" describes how Unity is rendered on systems with lower graphics capabilities than is required by Compiz.

One project, with graceful degradation.

---

### Post by vasa1 on 2012-08-14
> **rg4w said:**
> "Unity 3D" describes how Unity is rendered under Compiz.  "Unity 2D" describes how Unity is rendered on systems with lower graphics capabilities than is required by Compiz.

One project, with graceful degradation.
Let's see. I suspect computers that aren't adequately provisioned for hardware acceleration will find their CPU is having to work harder.

---

### Post by vexorian on 2012-08-14
^ That's probably what already happens with unity-2D.

---

