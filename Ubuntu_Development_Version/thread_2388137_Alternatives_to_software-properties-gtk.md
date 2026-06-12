---
title: "Alternatives to software-properties-gtk?"
date: 2018-03-28
forum: Ubuntu Development Version
---

### Post by &amp;KyT$0P# on 2018-03-28
Some months ago, I discovered that snapd contains forced phoning home, and have been purging all things snapd from all my systems ever since.

Today, I updated my Xubuntu 18.04, and discovered that snapd got installed again. :confused:

So I purged it again, which took out software-properties-gtk and software-properties-common. :(

I know at least some of the functionality of software-properties can be achieved with command-line tools, e.g. editing [FONT=Courier New]/etc/apt/sources.list[/FONT].  But what about the automatic update settings and Additional Drivers settings?  How to change those without software-properties?

---

### Post by kerry_s on 2018-03-28
snapd checks for updates, just like all the other software. are you not wanting to stay updated, security fixes, etc...?

---

### Post by &amp;KyT$0P# on 2018-03-28
> **kerry_s said:**
> snapd checks for updates, just like all the other software. are you not wanting to stay updated, security fixes, etc...?
If snapd had an option to **never make AUTOMATIC internet connections**, I wouldn't call it "phoning home" and I would have no problem with it.

In case it wasn't clear, I won't tolerate snapd on any of my systems until it includes such an option.  Period.

Do you have an answer to the questions I actually asked?

---

### Post by kerry_s on 2018-03-28
>  Do you have an answer to the questions I actually asked? 

have you tried reinstalling just those packages? does it pull in snaped?

---

### Post by &amp;KyT$0P# on 2018-03-29
> **kerry_s said:**
> have you tried reinstalling just those packages? does it pull in snaped?
Thanks for the answer.  It does want to pull in two snapd-related packages, although it doesn't seem to actually require snapd itself.
```
$ sudo apt-get --no-install-recommends install software-properties-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-10 linux-headers-4.15.0-10-generic
  linux-image-4.15.0-10-generic linux-image-extra-4.15.0-10-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  gir1.2-snapd-1 libsnapd-glib1 software-properties-common
Recommended packages:
  snapd
The following NEW packages will be installed:
  gir1.2-snapd-1 libsnapd-glib1 software-properties-common
  software-properties-gtk
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/137 kB of archives.
After this operation, 914 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by kerry_s on 2018-03-29
well those are only libraries, there not going to phone home.

---

### Post by monkeybrain20122 on 2018-03-29
For your purpose all you need is to remove snapd, which is the daemon and perhaps snapd-login-service, the only additional package that get removed with them would be gnome-software-plugin-snap.

The other packages with "snap" in them that cause your trouble  are libs which provide access to snapd (and dependencies for things you have to keep), with snapd gone there is nothing for them to access. You can keep them.

---

### Post by monkeybrain20122 on 2018-03-29
> **halogen2 said:**
> If snapd had an option to **never make AUTOMATIC internet connections**, I wouldn't call it "phoning home" and I would have no problem with it.

In case it wasn't clear, I won't tolerate snapd on any of my systems until it includes such an option.  Period.

Do you have an answer to the questions I actually asked?

Well how do you think the software updater prompts you for update without getting on the internet and check for updates?

---

### Post by kerry_s on 2018-03-29
> **monkeybrain20122 said:**
> Well how do you think the software updater prompts you for update without getting on the internet and check for updates?

i think what he's saying is in software properties you can choose how you want updates handled & when to check. snapd has no gui for settings.

i would think that it would follow the standard update route as the rest of the system, but i've never cared enough to check. :)

---

### Post by &amp;KyT$0P# on 2018-03-29
> **kerry_s said:**
> well those are only libraries, there not going to phone home.
> **monkeybrain20122 said:**
> For your purpose all you need is to remove snapd, which is the daemon and perhaps snapd-login-service, the only additional package that get removed with them would be gnome-software-plugin-snap.

The other packages with "snap" in them that cause your trouble  are libs which provide access to snapd (and dependencies for things you have to keep), with snapd gone there is nothing for them to access. You can keep them.

Great!  So as long as they continue not requiring snapd itself, I'm good to continue using software-properties-gtk.  Thanks kerry_s and monkeybrain20122 for your help! :KS

> **monkeybrain20122 said:**
> Well how do you think the software updater prompts you for update without getting on the internet and check for updates?
I emphasized the word "automatic" for a reason.

Again, if snapd could be set to **never AUTOMATICALLY** connect to the Internet, i.e. it only connects when I tell it to, I would just update it along with updating apt and I would have no problem with it.

---

### Post by zika on 2018-03-29
System{ctl,d} are very apt (pun intended) to control snap(d) as wll as updater and make them not to up{date,grade} anytning at a time You do not want it...

---

