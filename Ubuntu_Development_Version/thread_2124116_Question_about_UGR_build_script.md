---
title: "Question about UGR build script"
date: 2013-03-09
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-03-09
I just ran the script, and my final iso 1.1GiB in size, is this what anyone else is seeing?

```
ls -l *iso
-rw-rw-r-- 1 cariboo cariboo [COLOR="#FF0000"]1135677440[/COLOR] Mar  9 17:28 raring-ubuntu-gnome-amd64-20130310.iso
```

---

### Post by cariboo on 2013-03-10
**Update**: I just created an i386 iso, which is what I really needed, and the size is 928MiB.

---

### Post by sgage on 2013-03-10
I haven't run the script in a few days, but I seem to recall that my iso was in the mid-800's MB. I could be mis-remembering though. I don't have that image around any more to check.

Maybe I'll run the script today - if I do I'll let you know what I come up with.

---

### Post by sgage on 2013-03-10
Here's my result from a just-completed run of the UGR script on today's daily build:

```
iso-build-script# ls -la raring-ubuntu-gnome-amd64-20130310.iso 
-rw-r--r-- 1 root root 988848128 Mar 10 10:24 raring-ubuntu-gnome-amd64-20130310.iso
```

I think I must have been remembering the size of stock daily build, not the UGR iso...

---

### Post by jbicha on 2013-03-10
Well we did [add]("https://launchpad.net/ubuntu/+source/ubuntu-gnome-meta/+changelog") Software Center, Update Manager, Firefox, LibreOffice, and GNOME Documents but dropped a few games, gnome-package-kit ("Software"), GNOME Fallback, Epiphany, Abiword, and Gnumeric so the size will be larger than 12.10 (as the added stuff takes up more space than the things we removed).

I don't think we want to go above 1GB though. If we are, we should look at dropping some more stuff.

---

### Post by kansasnoob on 2013-03-10
> **jbicha said:**
> Well we did [add]("https://launchpad.net/ubuntu/+source/ubuntu-gnome-meta/+changelog") Software Center, Update Manager, Firefox, LibreOffice, and GNOME Documents but dropped a few games, gnome-package-kit ("Software"), GNOME Fallback, Epiphany, Abiword, and Gnumeric so the size will be larger than 12.10 (as the added stuff takes up more space than the things we removed).

I don't think we want to go above 1GB though. If we are, we should look at dropping some more stuff.

Do you think we might be able to get an official Ubuntu GNOME Raring Beta by March 28th which is the scheduled final beta release date for Ubuntu?

That would give us about 4 weeks to test and fix bugs for the final release on April 25th :)

---

### Post by cariboo on 2013-03-10
The size of the iso in my first post was a second attempt to build the iso, as the first attempt wouldn't boot. I didn't clean out the archives directory on the second attempt, could that have been the problem? Before I built the i386 iso, I removed all the AMD64 packages from the archive and the iso size was under 1GiB

---

