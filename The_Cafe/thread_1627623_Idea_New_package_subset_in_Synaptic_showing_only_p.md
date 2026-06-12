---
title: "Idea: New package subset in Synaptic showing only packages not part of default set"
date: 2010-11-21
forum: The Cafe
---

### Post by czr114 on 2010-11-21
Synaptic is a great app, but there is one key feature I feel it is missing.

It would be great to have some sort of functionality to display only the set of packages resulting from the subtraction of default packages from the complete installed set, which would show only those packages installed by the user after the installation of the OS itself.

There are many uses for viewing that subset. In particular, those of us who install many additional packages could view and export that list to make for much faster installations on clean systems. If the list of user-installed packages could be isolated from the total install base, and exported to a list, a complete reinstallation of all user-installed packages could be accomplished with one invocation of apt-get on a clean system.

Not only would this make for ease of post-install system modification, by eliminating the need to hunt down and check every custom package desired, but it will also eliminate much hassle from needing to go back and reinstall those rarely used CLI utilities which are often forgotten after installation.

Is this something which might be worth adding to the brainstorm? Might it be better suited to a 100 cuts ticket?

---

### Post by czr114 on 2010-11-22
Nobody?

---

### Post by forrestcupp on 2010-11-22
It's a good idea, but I don't think it will happen.  Synaptic is used for more than just Ubuntu, and every distro it's used in has a different set of default packages.  Even different versions of the same distro have different default packages.  It would probably take a lot to get everyone to figure out a way to start flagging every package to tell if it is default or not.

---

### Post by czr114 on 2010-11-22
Practically speaking, it isn't difficult to run 'dpkg --list-selections' on a fresh system and save the output, for use in later comparison or upgrade.

That list can then be fed back in with --set-selections for later installation of the desired packages.

All which would be needed from Synaptic would be the inclusion of the default list at the time the distro ships (which shouldn't be hard), and an interface component to export/import lists as necessary.

This isn't new functionality. Everything can be done with dpkg right now. That is a bit daunting for newer users who can't navigate outside of Synaptic or the software center.

Exporting a package snapshot for later importing would make transitions from one clean install to another significantly easier for those who won't go through the underlying functionality.

It would also have uses in rapid deployment situations in which several standard installations are being made, but for whatever reason, the deployer isn't creating a standard image or using dpkg natively.

With Ubuntu being about ease of use, the ability for even an entry level tech helper to create a standard package set, export it from one configured machine, and import it to multiple targets, would help greatly in getting Ubuntu installed at small businesses, schools, charities, and other similar organizations.

---

### Post by cariboo on 2010-11-22
The big problem with that is that synaptic won't be installed by default after the Software Center is finished. I believe it is scheduled to be dropped for the next LTS release.

---

### Post by czr114 on 2010-11-22
They're taking away Synaptic in Natty?

---

### Post by madjr on 2010-11-23
> **czr114 said:**
> They're taking away Synaptic in Natty?

next lts, thats 12.04

anyway, the software center has history now, so is half way there.

also i seen some scripts that do this.

and **aptoncd** does this in a way too, by making a backup of all your post install packages.

linuxmint backup i think also does this.

there is even a tool for people without internet that also does something similar.

so yea it might be useful to integrate it software center sometime

---

### Post by forrestcupp on 2010-11-23
> **czr114 said:**
> Practically speaking, it isn't difficult to run 'dpkg --list-selections' on a fresh system and save the output, for use in later comparison or upgrade.

Nice.  They could have easily just added that to the installation.  Too bad you thought of that at the end of Synaptic's relevancy with Ubuntu.

---

