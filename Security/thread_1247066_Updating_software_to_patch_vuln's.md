---
title: "Updating software to patch vuln's"
date: 2009-08-22
forum: Security
---

### Post by Tobywuk on 2009-08-22
Hello,

Once a vulnerability is found in a piece of software, the vendor releases a patch. For windows and OSX users updating this software is easy, they just use the built in update function in that application.

How is the same done with ubuntu? I install most of my applications using apt-get but apt-get update/upgrade does not seem to install the latest versions of these pieces of software.  

I am assuming this is because it has not been updated in the repo's?
How do you stay on top of your patching in this scenario?

---

### Post by bodhi.zazen on 2009-08-22
Same way.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

The Ubuntu repositories are large and community maintained. There is some degree of testing before a new version is put in the repositories , however, versions are for the most part locked in. Ubuntu 8.04 comes with a set of applications and 8.10 has new applications , 9.04 is the latest, and 9.10 is testing.

There are some exceptions such as firefox. firefox 3.0.x is updated in Ubuntu 8.x and 9.04, but firefox 3.5.x is not, nor will it be in the "official" repositories.

There is a specific security repository as well.

Known vulnerabilities are patched, although the version number may not change. patches are released much faster in Linux then in Windows, ie hours to days rather then months to years.

At least that is an overview of how it works.

---

### Post by rookcifer on 2009-08-23
To touch on what bohdi said, one thing new Linux users have a hard time adjusting to is the notion of package managers and software repositories.  I see often where a new Linux user will go around downloading source tarballs and .debs, .rpms, etc., only to come to forums asking why the double click install didn't work.

Just keep in mind that all software is found, downloaded, and updated through the package manager (in the case of Ubuntu, aptitude).

```
sudo apt-get update
```

The above command will update *all* software on your machine.  This is actually much simpler than the Windows way, where you have to update all non-M$ applications individually.

---

### Post by Bachstelze on 2009-08-23
> **rookcifer said:**
> 
```
sudo apt-get update
```

The above command will update *all* software on your machine.

Wrong. This will only update the list of installable package. No package will actually be updated.

---

