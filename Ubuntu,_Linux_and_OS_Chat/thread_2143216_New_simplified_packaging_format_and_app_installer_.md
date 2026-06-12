---
title: "New simplified packaging format and app installer for Ubuntu"
date: 2013-05-08
forum: Ubuntu, Linux and OS Chat
---

### Post by slickymaster on 2013-05-08
It seems that Ubuntu is planning on a new packaging format and app installer which should make it easier for developers to get their software into Ubuntu, aiming to making it easier to build packages for Ubuntu: no dependencies between applications, no maintainer scripts and each app will be installed in its own directory.

See [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037074.html").

---

### Post by MadmanRB on 2013-05-08
seems risky as it could break debian compatibility.

---

### Post by mastablasta on 2013-05-08
took them long enough...

in windows and especially in opensoruce you have portable applicaitons.. usually a zip file of sorts. you can download and install on USb key, hard disk and such. you can easily have multiple verison installed next to eachother (just rename unzip/install folder). GTK based apps, QT based apps. you have it all. well KDE has it's own windows package manager, which took the linux way there. not sure it's it's a good idea. it's really silly we do not have such a thing in linux.

i thing it would be usefull. no more dependency hell and hunting for dependencies for applicaitons outside software center.

hmmm...
> Furthermore, the priority for this system at present is for Ubuntu
phone/tablet app packages, which haven't actually been built yet.

---

### Post by MadmanRB on 2013-05-08
Yes but one must tread carefully here, we dont want a format that will not be able to be repackaged for other distros.
If canonical develops a new format they better share the source code.

---

### Post by slickymaster on 2013-05-08
> **MadmanRB said:**
> seems risky as it could break debian compatibility.

Apparently the already existing packages won't change and Ubuntu will continue to use dpkg and apt, syncing with Debian and so on.

Also, and from Colin Watson's email in Ubuntu Devel mailing list, on the new package format:> 
[LIST]
[*]no dependencies between apps; single implicit dependency on the base system by way of a Click-Base-System field
[*]installs each app to an entirely separate directory
[*]entirely declarative: maintainer scripts are forbidden
[*]base package manager overhead, i.e. the time required to install a trivial package containing a single small file, is about 0.15 seconds on a newish x86 laptop and about 0.6 seconds on a Nexus 7 (and that's with the current prototype implementation in Python; a later implementation could be in C and would then be faster still)
[*]not limited to installing as root, although there may be similar constraints elsewhere to ensure that apps can't edit their own code at run-time
[*]packages built by feeding the intended output directory tree to a simple Python tool, plus a manifest.json file
[*]building packages requires only the Python standard library, with the intent that it should be possible to build these packages quite easily on non-Ubuntu or even non-Linux systems
[*]binary packaging format sufficiently similar to existing one that we could add support to higher-level tools with minimal effort
[*]strawman design for hooks into system packages, which will be entirely declarative from the app's point of view
[*]unit-tested from the start
[/LIST]


---

### Post by MG&amp;TL on 2013-05-08
Ah, finally. Something sane so developers don't have to waste time making packages.

---

### Post by cariboo on 2013-05-09
The new app installer is aimed at portable devices, smart-phones and tablets, there may be a bit of spillover to the desktop version, but I wouldn't count on any massive changes, as the suggestion will be a major pain to make work with out breaking the distributions.

---

