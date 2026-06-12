---
title: "Distribution Releases - Changes?"
date: 2009-02-24
forum: The Cafe
---

### Post by Dekkon on 2009-02-24
Is there actually innovative changes when there is a new version of a distribution, these are the common changes with a new release: 
[list]
[*]Window Theme Improvements - New wallpaper
[*]Bug Fixes
[*]New Updated Software, e.g. Kubuntu updating too KDE 4.2
[*]Possible new Software(Automatic Proprietory Drivers in Ubuntu)
[/list]
Take a look here: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

You notice in practicably every release there is a new theme, new wallpaper, new software installed by default, or in Repo. **All of which can easily be implemented through updates.** 


[center]**_Questions_**[/center]
[list]
[*]Why are there releases if there aren't major system wide changes? 

[*]Why go through the process of upgrading when you can just update, slowly causing less problems, then one major problem every six months? 

[*]Stable software is stable software correct? Why do we wait six months for it to be updated? 
[/list]

Don't take this seriously, I'm just a very curious person who likes to ask and question the judgment of people decisions. Don't flame me, I am actually asking **honest questions**, this isn't to knock developers.

---

### Post by 4th guy on 2009-02-25
Bumping this but I think you meant to say: 
"Don't take this **the wrong way**, I'm just a very curious person who likes to ask and question the judgment of people decisions."

---

### Post by jacksaff on 2009-02-25
It has to do with quality control and how well tested you want your distro to be. In particular, new kernels and major subsystems often get upgraded between releases.

Some distros do a rolling release - they never release a new version, just have permanent updates. Debian's 'sid' branch works this way, as do (I think) gentoo and arch.

This model is good for desktop users who can troubleshoot their own system, but bad for everyone else. It makes it hard to provide support for the distro as everyone will have slightly different systems. 

As ubuntu is backed by a company that sells support a rolling release is not really on. It could be possible to have the developing version keep going this way and branch it off a couple of months before release. Debian do this but they often end up frozen for months before they decide the release is near enough bug free. So I doubt ubuntu could do this either given their six month cycle.

---

### Post by gnomeuser on 2009-02-25
It also greatly depends on the distribution, e.g. look at the feature list for the upcoming Fedora 11 release.

[https://fedoraproject.org/wiki/Releases/11/FeatureList](https://fedoraproject.org/wiki/Releases/11/FeatureList)

---

### Post by mc4100 on 2009-02-25
> **Dekkon said:**
> Is there actually innovative changes when there is a new version of a distribution, these are the common changes with a new release: 
[list]
[*]Window Theme Improvements - New wallpaper
[*]Bug Fixes
[*]New Updated Software, e.g. Kubuntu updating too KDE 4.2
[*]Possible new Software(Automatic Proprietory Drivers in Ubuntu)
[/list]
Take a look here: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

You notice in practicably every release there is a new theme, new wallpaper, new software installed by default, or in Repo. **All of which can easily be implemented through updates.** 

This system is implemented in several distributions, it's known as a [Rolling Release]("http://en.wikipedia.org/wiki/Rolling_release") model. The benefits are clear: perpetually updated software, but with the drawback of instability. Solving problems, creating new ones. Other distros, like Ubuntu, choose to release over a certain time-frame (one which is in sync with the GNOME cycle) which allows for a 'freeze' so that the new software can be tested and fixed and made more stable. 


> [list]
[*]Why are there releases if there aren't major system wide changes? [/list]

There are, the kernel will update to provide new drivers, implementations of new ideas and concepts (such as GEM and KMS). And upcoming in Jaunty is a whole new notification system.
> [list][*]Why go through the process of upgrading when you can just update, slowly causing less problems, then one major problem every six months? 
[/list]
"Causes less problems" is simply your opinion
> [list][*]Stable software is stable software correct? Why do we wait six months for it to be updated? [/list]
If you can learn one thing from pulseaudio, it's that stable software is **not** stable software. In a prefect world ...

Don't forget that releases make it easier to distribute a distribution. A random snapshot of packages and updates might not work for everyone, they might have caught it at a bad time, when a bad bug stopped a whole series of chips functioning ... and any disk would certainly go out of date very quickly (though this is true for all software, point releases, which have been tested, help solve this problem with Ubuntu).

---

