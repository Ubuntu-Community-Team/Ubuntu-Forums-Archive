---
title: "Repository Addresses"
date: 2005-05-16
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-16
Due to Subversion Repository issues, I've set up alternate access points for Backports. Please see [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php) for the latest, up-to-date information.


**Right now, MOST IMPORTANTLY**, I recommend you to switch to [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) (from [http://backports.ubuntuforums.org/backports)](http://backports.ubuntuforums.org/backports)). It won't go down if the repository decides to die.

---

### Post by codejunkie on 2005-05-16
this may seem like a dumb questions but do you mean replace 

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

with

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restricted

or just use just use the one repo like

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp)

---

### Post by jdong on 2005-05-16
[QUOTE=codejunkie]this may seem like a dumb questions but do you mean replace 

deb [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-backports main universe multiverse restricted

deb [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-extras main universe multiverse restricted

with

deb [http://backports.ubuntuforums.org/ubp]("http://backports.ubuntuforums.org/ubp") hoary-backports main universe multiverse restricted

deb [http://backports.ubuntuforums.org/ubp]("http://backports.ubuntuforums.org/ubp") hoary-extras main universe multiverse restricted
[]("http://backports.ubuntuforums.org/ubp")[/QUOTE]

This is correct.

---

### Post by jdong on 2005-05-16
See the URL: we now have a new mirror!

---

### Post by codejunkie on 2005-05-17
thanks,

---

### Post by paul cooke on 2005-05-17
[QUOTE=jdong]See the URL: we now have a new mirror![/QUOTE]now comes the dumb question... ;)

would this make the entries for the sources list the following:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

and would this work

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/)

---

### Post by sebflipper on 2005-05-17
I have added:
> deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restrictedTo the bottom of my **/etc/apt/sources.list** file, when I goto: *System -> Administration -> Synaptic Package Manager* I get this error:
> W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)Any idea's how to fix it?

---

### Post by harryc on 2005-05-17
Whenever I get that error a simple Synaptic reload packages fixes it.

---

### Post by sebflipper on 2005-05-17
Ah right, thats seems to have sorted it. :grin: There should be a little note to tell you to ignore the error and just press Reload.

---

### Post by Amaranth on 2005-05-17
[QUOTE=sebflipper]Ah right, thats seems to have sorted it. :grin: There should be a little note to tell you to ignore the error and just press Reload.[/QUOTE]
 If the computer could figure out when that is and isn't a big problem it wouldn't need you to run it. :)

---

### Post by jdong on 2005-05-17
> **paul cooke]now comes the dumb question...  said:**
> ftp://ftp2.caliu.info/backports/[/url] hoary-backports main universe multiverse restricted

deb [ftp://ftp2.caliu.info/backports/]("ftp://ftp2.caliu.info/backports/") hoary-extras main universe multiverse restricted

Correct. You always need the deb {url} {distribution} {sections} syntax.

---

### Post by ktogias on 2005-06-02
Hi,

It is 2 days now that I take 

Error [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
  401 Authorization Required

and

Failed [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz)   401 Authorization Required

.................................... (same for other files in [http://backports.ubuntuforums.org/ubp/](http://backports.ubuntuforums.org/ubp/))

when doing apt-get update.... Am I missing something?

---

### Post by ubuntu-geek on 2005-06-02
[QUOTE=ktogias]Hi,

It is 2 days now that I take 

Error [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
  401 Authorization Required

and

Failed [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz)   401 Authorization Required

.................................... (same for other files in [http://backports.ubuntuforums.org/ubp/](http://backports.ubuntuforums.org/ubp/))

when doing apt-get update.... Am I missing something?[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=37525](http://ubuntuforums.org/showthread.php?t=37525)

Should help you out.

---

