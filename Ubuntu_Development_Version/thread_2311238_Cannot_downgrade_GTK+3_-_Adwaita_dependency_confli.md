---
title: "Cannot downgrade GTK+3 - Adwaita dependency conflict"
date: 2016-01-25
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2016-01-25
Well, I think I am NOT simply being too stupid here:

```
user@my-lubuntubox:~$ sudo apt-get install --reinstall adwaita-icon-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 70 not to upgrade.
<snip>
Preparing to unpack .../adwaita-icon-theme_3.18.0-2ubuntu1_all.deb ...
Unpacking adwaita-icon-theme (3.18.0-2ubuntu1) over (3.18.0-2ubuntu1) ...
Setting up adwaita-icon-theme (3.18.0-2ubuntu1) ...
```

Read as: adwaita-icon-theme **v3.18.0-2** now installed and working.

```
user@my-lubuntubox:~$ sudo apt-get install libgtk-3-common=3.18.6-1ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. 
<snip>
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libgtk-3-common : Depends: adwaita-icon-theme (>= 3.18) but it is not going to be installed
                   Recommends: libgtk-3-0 but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

OK, from the beginning: I have to downgrade GTK+3 again as the devel package is obviously breaking one or two applications here (causing weird crashes, etc)
So it's back from 3.19.x (gnome3-staging PPA) down to 3.18.6.
However, this Adwaita thing is making me pull out bunches of hair!
Clearly says that libgtk-3-common (most essential dep of libgtk-3-0) needs adwaita-icon-theme >= v3.18.

But this IS 3.18.0-2ubuntu1, for Christ's sake!! So it should be accepted.
I really do smell a bug here, not 'PEBKAC' (as it occurred in the past a few times)

Also, **--force-depends **seems to be impossible whenever a downgrade is forced by the equality sign ( = ).

---

### Post by mc4man on 2016-01-25
Must be a Lubuntu thing (or local). Don't get what you are trying to achieve but downgrading 3.19 to 3.18 works ok here in Ubuntu
ex. (ignore gschema stuff as I've not yet fixed that file for my using nautilus-3.14 in 16.04 instead of the (self moderated )  3.18 nautilus

> $ sudo apt-get install libgtk-3-common=3.18.6-1ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libtcl8.6
Use 'sudo apt autoremove' to remove it.
The following packages will be DOWNGRADED:
  libgtk-3-common
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 50 not upgraded.
Need to get 0 B/205 kB of archives.
After this operation, 23.9 MB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: warning: downgrading libgtk-3-common from 3.19.7-0ubuntu1~xenial0 to 3.18.6-1ubuntu1
(Reading database ... 227027 files and directories currently installed.)
Preparing to unpack .../libgtk-3-common_3.18.6-1ubuntu1_all.deb ...
Unpacking libgtk-3-common (3.18.6-1ubuntu1) over (3.19.7-0ubuntu1~xenial0) ...
Processing triggers for libglib2.0-0:amd64 (2.47.4-1) ...
No such key 'open-folder-on-dnd-hover' in schema 'org.gnome.nautilus.preferences' as specified in override file '/usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override'; ignoring override for this key.
Setting up libgtk-3-common (3.18.6-1ubuntu1) ...

What version of gtk-3 do you have?

---

### Post by syntaxerror74 on 2016-01-25
Oh, thanks for agreeing to do a 'live' testcase...(didn't expect nor demand that!)
I still HAVE 3.19.7 (3.19.7-0ubuntu1~xenial0), but due to insufficient stability I want to go back to 3.18.6, as said.

Hang on...!
Could you give me exact version of adwaita-icon-theme that **you **have installed? (must be different from mine)
Maybe it's just a minor difference that will stop it from complaining about the adwaita dep...

---

### Post by mc4man on 2016-01-25
adwaita-icon-theme  3.18.0-2ubuntu1

If you used the ppa in full & want to go back I'd suggest - 
re-enable staging ppa if disabled, also the main GNOME3 if you used.
run an upgrade
install ppa-purge
use ppa-purge on both ppa's  to go back to 16.04 repo packages.

---

### Post by syntaxerror74 on 2016-01-25
> **mc4man said:**
> adwaita-icon-theme  3.18.0-2ubuntu1
Hey, that's mine too!

> If you used the ppa in full & want to go back I'd suggest - 
re-enable staging ppa if disabled, also the main GNOME3 if you used.
run an upgrade
install ppa-purge
use ppa-purge on both ppa's  to go back to 16.04 repo packages.

Good suggestions, all of them..however I'm going to try something else before:

force installation from the back door, i. e. via dpkg -i and a libgtk3-common package downloaded separately.
As the concepts of APT and dpkg differ a lot, there will be no restriction of not being able to use --force option(s).
That's because with dpkg, I can force the version simply by specifying the appropriate package file (which I have to have on my hard disk, of course)

---

### Post by syntaxerror74 on 2016-01-26
**FIXED IT!**

```
$ sudo apt-get install libgtk-3-bin=3.18.6-1ubuntu1
```

Although I still think it's simply wrong behavior that you have to start guessing what it *actually* wants, this muzzled the dependency detection engine...once and for all. *SIGH*

That's why I posted so much output, to give you guys some certainty that it definitely didn't mention anything about wanting **libgtk-3-bin**...ever.
It's just about such nasty little blockers as these, which would often enjoy to send you out on a wild-goose chase, also in the office, and sometimes for longer than 1 day.

(Thanks mc4man for your efforts.)

---

### Post by mc4man on 2016-01-26
Sometimes it's better to try aptitude in such cases, it may have been more verbose.

---

### Post by syntaxerror74 on 2016-01-26
Agreed. But alas, I've simply got a "command-line fetish". :biggrin:

---

