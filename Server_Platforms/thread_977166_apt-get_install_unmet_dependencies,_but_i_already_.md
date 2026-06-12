---
title: "apt-get install unmet dependencies, but i already have newest version"
date: 2008-11-09
forum: Server Platforms
---

### Post by killerguppy101 on 2008-11-09
I'm trying to apt-get install apache2-threaded-dev, but keep getting unmet dependencies errors, which i followed to here:

apt-get install libpq-dev
The following packages have unmet dependencies:
libpq-dev: Depends: libpq5 (=8.3.1-1) but 8.3.3-0ubuntu0.8.04 is to be installed

apt-get install libpq5
libpq5 is already the newest version.

I'm pretty new to ubuntu, so I don't really have any idea where to start, but it looks like I should already have the dependencies required.  I've tried searching google as best I can, but to no avail.  I'm ultimately trying to get APXS2 on my system if that helps any.

---

### Post by loell on 2008-11-10
chances are the packager for **libpq-dev**, might have made a typo.

where it should be ** [COLOR="Red"]>=[/COLOR] ** and not just **[COLOR="Red"] = [/COLOR]** to meet the dependency.

or unless theres a compeling reason why its done that way.

---

### Post by killerguppy101 on 2008-11-10
So how can I fix this?  Every source I find says I need to recompile apache2 with the apache2-threaded-dev package to enable apxs, but I can't get the apache2-threaded-dev package.  Is there a way I can force it to download and install the package, and just ignore the error messages?  Like I sais, I'm new to ubuntu and linux altogether, so I'm not sure of my options.

---

### Post by loell on 2008-11-10
maybe you can fix it, by recompiling **libpq-dev**

1. download the source
```
apt-get source libpq5
```

2. download the necessary tools for re-packaging

```
ubuntu-dev-tools
```

3. edit the control file

```
gedit postgresql-8.3-8.3.4/debian$/control
```

change the part 

```
Depends: ${shlibs:Depends}, libpq5 (= ${binary:Version})
```

to

```
Depends: ${shlibs:Depends}, libpq5 ([COLOR="Red"]>[/COLOR]= ${binary:Version})
```

then save it.

4. rebuild

```
dpkg-buildpackage -b -uc
```

5. install the newly generated libp5 dev debs

---

### Post by killerguppy101 on 2008-11-12
Almost, but not quite.  I assumed you meant
```
apt-get install ubuntu-dev-tools
```

When i tried to rebuild, i had another mess of unmet dependencies.  I could install them all except one:
libpam-dev
and that appears to be for the same reason:
```
The following packages have unmet dependencies:
  libpam0g-dev: Depends: libpam0g (= 0.99.7.1-5ubuntu6) but 0.99.7.1-5ubuntu6.1 is to be installed

```

After some screwing around, i tried your method on this too, and that just brought up MORE unmet dependencies on that build...  I see a pattern forming...

---

### Post by loell on 2008-11-12
i don't know why even ubuntu-dev has unmet dependency for you, could it be that your package index database has been messed up? if so, then i'm afraid you'll gonna to reinstall :(

edit: this may even be the reason why libpq-dev is not installing, so reinstalling might also address  the original problem.

---

### Post by MJN on 2008-11-12
Post your APT source list (/etc/apt/sources.list)[1] as it looks like you have had hardy-updates enabled at one stage and hence have received updated packages (6.1 updates for libpam0g) from it. If it is no longer enabled then 'new' packages will be calling for dependencies from the same (old) versions (6) yet they've already been earmarked from the updated repository (6.1).

If that explanation didn't confuse you I don't know what will... ;-)

Mathew

[1] Or, if you want to crack on, go ahead and enable the hardy-update repositories (assuming they're not already), update the package list (sudo apt-get update) and give it another go. Note that this assumes that loell's well-intentioned suggestions haven't screwed things up! ;-)

---

### Post by loell on 2008-11-12
> **MJN said:**
>  Note that this assumes that loell's well-intentioned suggestions haven't screwed things up! ;-)

good riddance to those who listen to my advices, it will make there system unstable. it's been considered a blessing in disguise by many! :lolflag:

nah.. kidding.. 

It was there all along, in which I had no idea, until you brought it up :)

---

