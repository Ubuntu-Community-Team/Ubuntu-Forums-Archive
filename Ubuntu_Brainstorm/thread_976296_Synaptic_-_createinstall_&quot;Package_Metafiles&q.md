---
title: "Synaptic - create/install &quot;Package Metafiles&quot; for installation on offline computers"
date: 2008-11-09
forum: Ubuntu Brainstorm
---

### Post by irrdev on 2008-11-09
One of Linux's strongest, and weakest points, is its reliance on a package management system. For internet-connected computers, downloading packages from online repositories is relatively easy, and a excellent form of software management.

HOWEVER, offline Linux computers unfortunately suffer greatly from the package management system. It simply takes too much effort to manually and separately download a package and all of its necessary dependencies, transfer them to the offline computer, and then install the packages in the correct order. While APTonCD has been very successful in making this process easier, it still does not make offline package installation as easy as it should be.

I am proposing that Synaptic be given the option to create and install so-called "Package Metafiles". A Metafile would simply be a zip or tarball which contains selected packages and all of their dependencies. A user would select the packages to include from Synaptic's package list, and then click the "Create Package Metafile" option. Synaptic would download the selected packages and all of their dependencies, and then bundle them together. The user would then transfer the "Package Metfile" to the offline computer, where Synaptic would have an "Install Metafile" option to unpack and install all the packages from the "Package Metafile".

This "Package Metafile" feature would be extremely easy to implement, as it would be integrated directly into Synaptic itself. Ubuntu would become more viable as an offline OS, which would greatly benefit offices, schools and laptop users. Even home users frequently have some offline computers, and I am sure that this feature would be appreciated.

Sorry if I didn't explain this quite idea clearly. Any input or comments would be appreciated. The exact implementation of this idea isn't so important as the idea itself: **make offline installation of packages easier**. You can vote on this idea at Ubuntu Brainstorm: 

[[IMG]http://brainstorm.ubuntu.com/idea/15436/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15436/)

---

### Post by gnomeuser on 2008-11-09
As usual upstream is way ahead of you.

[http://blogs.gnome.org/hughsie/2008/10/09/service-pack-gui/](http://blogs.gnome.org/hughsie/2008/10/09/service-pack-gui/)

Now you just need to convince Ubuntu to join the 21th century and ship PackageKit by default.

---

### Post by irrdev on 2008-11-10
> **gnomeuser said:**
> As usual upstream is way ahead of you.

[http://blogs.gnome.org/hughsie/2008/10/09/service-pack-gui/](http://blogs.gnome.org/hughsie/2008/10/09/service-pack-gui/)

Now you just need to convince Ubuntu to join the 21th century and ship PackageKit by default.
Thanks **gnomeuser** for the link! I wasn't aware that the PackageKit developers have already implemented this functionability and made it accessible from the command-line. Unfortunately, as you pointed out, Ubuntu is unlikely going to switch to PackageKit anytime in the near future. I find this unfortunate, as PackageKit has many unique features not found with other package management systems. 

Since Ubuntu is not going to adapt PackageKit anytime soon, I think its important that this functionality be added to the package manager that Ubuntu _does_ come bundled with. Synaptic still has room for improvement, and this "Package Metafile" feature would be truly easy to implement.

If I have enough time over the coming few weeks, I may try my hand at creating a standalone application which implements this feature. Still, my time is limited, and I believe it would be far easier to integrate with Synaptic. Unfortunately, I am not very good at figuring out others' source code. Is there anyone else who is interested in implementing this feature for Ubuntu/Synaptic?

---

### Post by gnomeuser on 2008-11-10
> **irrdev said:**
> Thanks **gnomeuser** for the link! I wasn't aware that the PackageKit developers have already implemented this functionability and made it accessible from the command-line. Unfortunately, as you pointed out, Ubuntu is unlikely going to switch to PackageKit anytime in the near future. I find this unfortunate, as PackageKit has many unique features not found with other package management systems. 

Since Ubuntu is not going to adapt PackageKit anytime soon, I think its important that this functionality be added to the package manager that Ubuntu _does_ come bundled with. Synaptic still has room for improvement, and this "Package Metafile" feature would be truly easy to implement.

If I have enough time over the coming few weeks, I may try my hand at creating a standalone application which implements this feature. Still, my time is limited, and I believe it would be far easier to integrate with Synaptic. Unfortunately, I am not very good at figuring out others' source code. Is there anyone else who is interested in implementing this feature for Ubuntu/Synaptic?

Okay, once more, PackageKit is NOT a replacement for your existing package manager, it lies on top of it providing a common set of applications as well as a dbus interface. It is not about Ubuntu switching away from dpkg, it is about adding PackageKit to their default configuration and keeping it updated. Then they could gain all of this functionality plus more such as integration of package install in applications (think installing codecs, fonts, file handlers on demand when support is not present).

---

### Post by olskar on 2008-11-12
Nice feature!

Why is Ubuntu unlikely going to switch to PackageKit anytime in the near future?

---

### Post by gnomeuser on 2008-11-12
> **olskar said:**
> Nice feature!

Why is Ubuntu unlikely going to switch to PackageKit anytime in the near future?

They had the change to switch with Intrepid but did not. The developers in the blueprint seem more to think they are be forced by upstream to supply PackageKit since it has gained traction with them.
Additionally PackageKit in Ubuntu is way out of date, even the PPA carries 0.3.4/6 when 0.3.10 is out, so the commitment level seems very low.

I have a feeling this is yet another place where Ubuntu has to be dragged kicking and screaming to do things the upstream way. They sadly just don't seem interested.

You can vote for PackageKit here, hopefully that will interest the developers in making this a priority for Jaunty:

[[IMG]http://brainstorm.ubuntu.com/idea/64/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/64/)

---

