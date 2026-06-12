---
title: "dependencies error!! cant't install any software in kali linux please help!!!!!!"
date: 2017-10-15
forum: Ubuntu/Debian BASED
---

### Post by dilkhan895 on 2017-10-15
I just installed kali linux.Now i want to install some softwares butt won't let me.
```

apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gstreamer1.0-plugins-base : Breaks: gstreamer1.0-plugins-bad (< 1.11.90) but 1.4.4-2.1+b1 is to be installed
 libgstreamer-plugins-base1.0-0 : Breaks: gstreamer1.0-plugins-bad (< 1.7.1) but 1.4.4-2.1+b1 is to be installed
 libgstreamer1.0-0 : Breaks: gstreamer1.0-plugins-bad (< 1.11.1) but 1.4.4-2.1+b1 is to be installed
 vlc : Depends: vlc-plugin-base (= 2.2.6-6) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
please help me to fix this. I've treid apt-get update & also updated the reposotories & tried apt-get upgrade

please haelp me!!!

---

### Post by Perfect Storm on 2017-10-15
Moved to Ubuntu/Debian BASED forum.

---

### Post by ian-weisser on 2017-10-15
Floundering with random apt commands won't help.

Re-read the error message carefully.
The error message tells you exactly what package is the problem, and why it's a problem

You seem to have a version conflict. You are tying to install a version of a package that is incompatible with your release of Ubuntu. This typically happens when you install software from an unwise source.

Figure out what you were tying to accomplish that resulted in the incompatible package trying to be installed...and undo/uninstall that entire process. Return your system to the state before you started. There's no single magic command for that - it requires you to search your memory and whatever instructions you might have been following.

---

