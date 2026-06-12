---
title: "Force upgrades from a repository"
date: 2007-10-22
forum: Repositories &amp; Backports
---

### Post by newtonfn on 2007-10-22
Hi,

I'v added to my sources.list two repositories that have the same program. Actually "medibuntu" and "download.skype.com"

I'v installed some packages from medibuntu and previously i'v installed skype from the other repository.

Now, the update manager keep telling me that i have a pending upgrade, because it's believe that the skype on medibutu's repositories are newer than the other (in fact are the same)

I want to ignore the skype package from medibuntu repository... how can i accomplish that?

Sorry about my English.

---

### Post by bapoumba on 2007-10-24
It probably has to do with the version number in the medibuntu repositories. You can comment the medibuntu repos in your sources.list, or pin the current package version with synaptic.

---

### Post by newtonfn on 2007-10-24
Thanks bapoumba,

How can I pin the current package with synaptic but allow futhers updates from a specified repositories to the same package ? The closest thing, that's seems to work, that I found in synaptic is Force Version, but that will not let me upgrade the package anymore.

---

### Post by bapoumba on 2007-10-24
> **newtonfn said:**
> Thanks bapoumba,

How can I pin the current package with synaptic but allow futhers updates from a specified repositories to the same package ? The closest thing, that's seems to work, that I found in synaptic is Force Version, but that will not let me upgrade the package anymore.
True. The other solution is to install the medibuntu one (you said they were identical) and subsequently upgrade from medibuntu when a new version is available.
Package managers will always install the highest version from the repos specified in the sources.list.

So if you want to keep the "download.skype.com" package, comment the medibuntu repos (you can uncomment them on the spot once to upgrade some other packages).

In any case, all my third party repos are commented for day-to-day upgrades or installs. I uncomment for specific upgrades, or installs, and comment them right after that (same thing for the backports).

---

### Post by newtonfn on 2007-10-26
After several days without internet I could do a little more research and solve my problem. (connectivity in my country is a nightmare)

Thanks the tip about "pin a package" and thanks Google and this forum I discovered that I could create a file called /etc/preferences where I can set a priority to sources and/or packages

I have created the file /etc/apt/preferences with the following text
```

Package: * 
Pin: release l=Medibuntu
Pin-Priority: 400

```

That  tells apt that the Medibuntu repository have lower priority than others repositories. Then, if a package exist in other repository apt will try to install (or update) from them... if I request a package that only exist in Medibuntu, then will be installed from Medibuntu.

More information can be found goggling for "apt pin"
A site that was very useful for me is: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.es.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.es.html)

Finaly, thank bapoumba for your assistance and patience.
Fernando

---

### Post by bapoumba on 2007-10-27
Hey, that is a very elegant solution :)
Many thanks to you for sharing it. I knew you could pin a package version, but never looked how to set a priority to a repo. Learning new things everyday ^^

---

