---
title: "nautilus-gksu. Does anyone know where this package went to?"
date: 2011-12-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2011-12-17
nautilus-gksu is not in the repository in 12.04. Does anyone know where it went to? Without it I can't install nautilus-actions-extra. I wanted to test to see if this would work in 12.04.

---

### Post by mc4man on 2011-12-17
nautilus-gksu is no longer being built, why never did get clear answer. The extension itself still works & doesn't need the package  to be installed, just the .so can be placed in /usr/lib/nautilus/extensions-3.0

IF you need the package itself to be be installed then I guess you could install the last one available though it requires libnautilus-extension1 as an install dep. (& was non-functional as installed starting in 11.10

Edit: 
you should contact the author - he can fix in any number of ways ranging from removing the gksu actions to providing the package or .so 

As quick test modified his source to not ck. for the nautilus-gksu package & not try to do the 11.10 'fix'. (I have the .so manually placed in /usr/lib/nautilus/extensions-3.0

The deb then produced installed & works fine in short test of the gksu actions, screens show

---

### Post by ranch hand on 2011-12-18
> **mc4man said:**
> nautilus-gksu is no longer being built, why never did get clear answer. The extension itself still works & doesn't need the package  to be installed, just the .so can be placed in /usr/lib/nautilus/extensions-3.0

IF you need the package itself to be be installed then I guess you could install the last one available though it requires libnautilus-extension1 as an install dep. (& was non-functional as installed starting in 11.10

Edit: 
you should contact the author - he can fix in any number of ways ranging from removing the gksu actions to providing the package or .so 

As quick test modified his source to not ck. for the nautilus-gksu package & not try to do the 11.10 'fix'. (I have the .so manually placed in /usr/lib/nautilus/extensions-3.0

The deb then produced installed & works fine in short test of the gksu actions, screens show
Yes that is like the Thunar "Custom Actions" that have been around since Debian Etch.  I like it better as I can put what I want in the menu such as here.  Keep in mind that I am, among other things, a Blacksmith.

---

### Post by zika on 2011-12-18
Did You look at: [https://launchpad.net/~dr3mro/+archive/nautilus-actions-extra]("https://launchpad.net/%7Edr3mro/+archive/nautilus-actions-extra") ...?
There is .deb even for Precise...
I did not, yet try it because:
1. I try not to use Nautilus since I'm on {Flux,Open}Box...
2. I'm kind of CLI guy...

---

### Post by irv on 2011-12-18
> **zika said:**
> Did You look at: [https://launchpad.net/~dr3mro/+archive/nautilus-actions-extra]("https://launchpad.net/%7Edr3mro/+archive/nautilus-actions-extra") ...?
There is .deb even for Precise...
I did not, yet try it because:
1. I try not to use Nautilus since I'm on {Flux,Open}Box...
2. I'm kind of CLI guy...

Even the deb file will not work because the nautilus-gksu is no longer part of the nautilus.

---

### Post by mc4man on 2011-12-18
> **irv said:**
> Even the deb file will not work because the nautilus-gksu is no longer part of the nautilus.
Never was part of nautilus, nautilus-gksu is a nautilus extension from the gksu source and still is included in gksu
It's been decided by someone(s) not to build/install the extension anymore for some reason.

(actually a ways back saw a nautilus dev comment that nautilus should not be run graphically as root at all, though gksudo nautilus is still used.

---

### Post by zika on 2011-12-19
> **irv said:**
> Even the deb file will not work because the nautilus-gksu is no longer part of the nautilus.Yes, but You know, now, which e-mail to use... ;)

---

### Post by irv on 2011-12-26
I thought I would just this comment to this thread because it has to do with Nautilus. Yesterday could not get Nautilus to work at all because I was missing some files after update/upgrade. This morning after doing the update/upgrade everything is working again. It installed some files I was missing.
I thought I would post this in case anyone else was having this problem.

---

### Post by jbicha on 2011-12-27
> **irv said:**
> I thought I would just this comment to this thread because it has to do with Nautilus. Yesterday could not get Nautilus to work at all because I was missing some files after update/upgrade. This morning after doing the update/upgrade everything is working again. It installed some files I was missing.
I thought I would post this in case anyone else was having this problem.

Open a new thread for new problems/conversations. :-)

And try to avoid running nautilus as root.

---

### Post by ronacc on 2011-12-27
> **jbicha said:**
> Open a new thread for new problems/conversations. :-)

And try to avoid running nautilus as root.

absolutely ! never do anything that will make your task easier .

---

### Post by mc4man on 2011-12-27
As far as nautilus as root - comment 1 in a semi-unrelated bug report, though obviously people can do as they please though not always as long as they please.
[https://bugzilla.gnome.org/show_bug.cgi?id=654184](https://bugzilla.gnome.org/show_bug.cgi?id=654184)

---

### Post by irv on 2011-12-28
> **jbicha said:**
> Open a new thread for new problems/conversations. :-)

And try to avoid running nautilus as root.

I made this comment here because it does in a way related to this thread that I started. Even though the update installed the missing files, "nautilus-gksu" is still missing and it looks like it will stay missing.

---

### Post by kansasnoob on 2011-12-28
> **jbicha said:**
> Open a new thread for new problems/conversations. :-)

And try to avoid running nautilus as root.

IMHO 'nautilus-gksu' did help prevent users from running nautilus as root :)

I particularly liked using it from time to time while grub 2 was a new thing because I'd frequently need to search for various settings. Once I found what I thought I wanted I could simply click back one level in Nautilus, then select Open as Admin, and then make any edit :)

I think that's no less safe than running a command that locates that file/folder with gksu or gksudo, and certainly safer than opening Nautilus with gksu :)

I've now become very accustomed to searching for files and folders with "ls" and "cat" so I don't miss it but I can see a valid need or at least a valid desire for 'nautilus-gksu'.

---

### Post by jbicha on 2011-12-28
I agree that a root file browser is useful to a lot of people. I never really used nautilus-gksu so I'm not really sure what it provided.

---

