---
title: "AC Profile Message"
date: 2012-08-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mparillo on 2012-08-21
After I sign-in, but before my 12.10 Plasma desktop fully loads (and before I hear the chime) an alert flashes up too quickly for me to read. It is not a normal alert at the bottom, but at the top and it references a profile 'AC' and DPMS Control , that I think has something to do with power settings.
I am running a daily build kept up to date on VMWare Player.

Anybody else see this?

---

### Post by lucazade on 2012-08-21
try to find the message in .xsession-errors.. give a look also in dmesg.
Probably the virtualmachine is not fully acpi compilant.

---

### Post by ventrical on 2012-08-21
I haved Kubuntu and the KDe desktop working on different machines here. All is well so far. One install is on a system using a Nvidia graphics card and that has been affected by the holding of the nvidia-current problem. All my Intel based graphics adapters are working just spiffy, Kubuntu, Unity 3D , etc..

---

### Post by mparillo on 2012-08-21
> **lucazade said:**
> try to find the message in .xsession-errors.. give a look also in dmesg.
Probably the virtualmachine is not fully acpi compilant.
Thank you, but I could not find it in .xsession-errors.
I would look in dmesg stored, but I cannot find it. Where is it?

P.S. I caught more of the notification. It referred to DPMS Control, which might come from: [http://www.x.org/releases/X11R7.6/doc/libXext/dpmslib.html](http://www.x.org/releases/X11R7.6/doc/libXext/dpmslib.html)

---

### Post by mparillo on 2012-08-21
This is [confirmed]("http://ubuntuforums.org/showthread.php?t=1988221").

---

### Post by mparillo on 2012-08-21
> **mparillo said:**
> This is [confirmed]("http://ubuntuforums.org/showthread.php?t=1988221").

So I opened a bug on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1039582").

---

### Post by mparillo on 2012-08-22
> **mparillo said:**
> This is [confirmed]("http://ubuntuforums.org/showthread.php?t=1988221").

It looks to be an upstream bug:
[https://bugs.kde.org/show_bug.cgi?id=302846](https://bugs.kde.org/show_bug.cgi?id=302846)

---

### Post by mparillo on 2012-09-13
> **mparillo said:**
> It looks to be an upstream bug:
[https://bugs.kde.org/show_bug.cgi?id=302846](https://bugs.kde.org/show_bug.cgi?id=302846)

As noted there, the warning stopped now that I have been updated to Platform Version 4.9.1.

Marking thread as solved.

---

