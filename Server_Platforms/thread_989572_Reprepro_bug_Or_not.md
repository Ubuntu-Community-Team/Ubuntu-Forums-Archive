---
title: "Reprepro bug? Or not?"
date: 2008-11-21
forum: Server Platforms
---

### Post by jesushero on 2008-11-21
I'm using reprepro for my own ubuntu repository of my software. It works fine and does everything I want it to do, except for one detail. When I try to upload two packages with the same package-name and version number, for the same architecture, but for a DIFFERENT version of ubuntu, it comes up with an error telling me I'm trying to re-upload an existing package.

Example:
```
sudo reprepro --includedeb hardy pd-extended_0.40.3-1_hardy_i386.deb
```

Then after that:
```
sudo reprepro --includedeb gutsy pd-extended_0.40.3-1_gutsy_i386.deb
```

And it just won't do it. The reason why I need two different ones is the different library dependency names. Is this just a reprepro bug/limitation? Or is there an actual way around it? The reason is that reprepro RENAMES the files, omitting the codename section. They all go to the same pool directory, so the gutsy and the hardy packages would end up having the exact same name! 

Any ideas?

---

