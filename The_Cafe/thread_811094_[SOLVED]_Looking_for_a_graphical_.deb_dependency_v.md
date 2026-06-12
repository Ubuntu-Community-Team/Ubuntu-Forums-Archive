---
title: "[SOLVED] Looking for a graphical .deb dependency viewer"
date: 2008-05-28
forum: The Cafe
---

### Post by -Phi- on 2008-05-28
I've been wondering if such a program exists. What with all the libs and packages I've installed I'd like to see a visual representation of what I have installed depends on what.

I could imagine that I have things installed because some obscure program I don't use anymore depends on them, and deborphan won't pick them up because it thinks I want that obscure program.

Google and Synaptic haven't been helpful, at least not for the apt repository architecture. Has anyone heard of something like this?

- Phi

---

### Post by FuturePilot on 2008-05-28
```
sudo apt-get autoremove
```
?

Also in Synaptic if you click on the Status button it will organize packages into various categories one being Autoremovable.

---

### Post by xebian on 2008-05-28
> **-Phi- said:**
> I've been wondering if such a program exists. What with all the libs and packages I've installed I'd like to see a visual representation of what I have installed depends on what.

I could imagine that I have things installed because some obscure program I don't use anymore depends on them, and deborphan won't pick them up because it thinks I want that obscure program.

Google and Synaptic haven't been helpful, at least not for the apt repository architecture. Has anyone heard of something like this?

- Phi

One word -  aptitude

:guitar:

---

### Post by -Phi- on 2008-05-28
I've got all the autoremovable ones. That synaptic and aptitude do that is great, but it only applies to dependencies left over after you uninstall the "parent" program. I want to find out, say, whether I have a program still installed that uses a ton of QT libraries that no other programs use.

I picture it as a big colourful set of pyramids, with programs on top and all their dependencies below. Most of the pyramids would overlap since some dependencies are very commonly used. Some pyramids would be out on their own.

Maybe my picture is off.

- Phi

---

### Post by FuturePilot on 2008-05-28
If you know the name of the package you can highlight in Synaptic and click Properties and select the Dependencies tab. Something like that?

---

### Post by Daishiman on 2008-05-29
Look into debtree. It produces a text output to make dependency graphs with graphviz. Warning: graphs can be really really huge.

---

### Post by -Phi- on 2008-05-29
Debtree looks very much like what I'm looking for, thanks! I'll play around with it.

- Phi

---

### Post by -Phi- on 2008-08-05
Just in case anyone else comes looking for the same sort of thing, [GTKOrphan]("http://www.marzocca.net/linux/gtkorphan.html") turned out to be almost exactly what I was looking for.

---

