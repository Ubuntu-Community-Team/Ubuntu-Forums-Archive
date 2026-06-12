---
title: "modifying debs"
date: 2009-08-23
forum: The Cafe
---

### Post by sandyd on 2009-08-23
is there an app that can modify the properties of deb files? i just need to edit the dependencies a bit because the previous creator put in pre-depends as one of the dependency types. however, they left the rest of the line blank which is confusing my apt repo

---

### Post by days_of_ruin on 2009-08-23
I think you would have to build a new one.
I could be wrong but I don't think debs are editable for security reasons.

---

### Post by praveesh on 2009-08-23
You can open the .deb using ark(the archive manager of kde. Installed by default in kUbuntu). You will see control.gz . Open it  . You will see a text file named control. Open it and edit the dependancies and save . Done.

---

### Post by 3rdalbum on 2009-08-23
> **praveesh said:**
> You can open the .deb using ark(the archive manager of kde. Installed by default in kUbuntu). You will see control.gz . Open it  . You will see a text file named control. Open it and edit the dependancies and save . Done.

I don't think this will work. Debian packages aren't just "ar" archives - they must be built with the dpkg-deb utility otherwise they won't install.

---

### Post by sandyd on 2009-08-23
i don't want to start a new thread for this, but how do you remove a deb using rerepopro?

---

### Post by FuturePilot on 2009-08-23
> **carlee said:**
> i don't want to start a new thread for this, but how do you remove a deb using rerepopro?

```
sudo reprepro -Vb . remove <dist> <packagename>
```

i.e.

```
sudo reprepro -Vb . remove jaunty brasero
```

---

### Post by sandyd on 2009-08-23
thanks!
apt repo all fixed now.

---

### Post by FuturePilot on 2009-08-23
> **carlee said:**
> thanks!
apt repo all fixed now.

You're welcome! :)

---

### Post by koenn on 2009-08-23
> **3rdalbum said:**
> I don't think this will work. Debian packages aren't just "ar" archives - they must be built with the dpkg-deb utility otherwise they won't install.
it works - I've modified debs before.
the intelligence is in the tools that you use to install them (apt, dpkg, debconf, ...), not in the .deb itself, they're really just archives with a specific dir tree and agreed-upon filenames inside.

you might have to work around the cecksums, but iirc you can just delete the checksum file or so.

---

