---
title: "packages have unmet when try install apache2 server ?! + PreDepends: dpkg (&gt;= 1.17.14"
date: 2015-09-03
forum: Server Platforms
---

### Post by momaiaz on 2015-09-03
i try to install Apache server but  :

------------------

```
sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : PreDepends: dpkg (>= 1.17.14)
E: Unable to correct problems, you have held broken packages.
```

---

### Post by QIII on 2015-09-03
Hello!

Which release of Ubuntu are you using?

When was the last time you did 
```
sudo apt-get update
sudo apt-get upgrade
```

or 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Please use code tags when posting text from the terminal:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by momaiaz on 2015-09-03
```

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

```

---

### Post by momaiaz on 2015-09-03
I did 
```

sudo apt-get update
sudo apt-get dist-upgrade

```

still the same

---

### Post by ian-weisser on 2015-09-03
> **momaiaz said:**
> 
The following packages have unmet dependencies:
 apache2 : PreDepends: dpkg (>= **1.17.14**)

Let's see what rmadison says about dpkg in 14.04:
```

$ rmadison dpkg
 dpkg | 1.17.5ubuntu5     | trusty           | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 dpkg | **1.17.5ubuntu5.4**   | trusty-security  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 dpkg | **1.17.5ubuntu5.4**   | trusty-updates   | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

There's your problem.
You seem to have tried to add non-Ubuntu software that demands a different (higher) version of dpkg than Ubuntu provides...but didn't provide the package itself...or the new package was not installable. That's called a *version conflict* and it falls under "you have requested an impossible situation" in the error message.

This is the risk you take when adding non-Ubuntu software.
Happily, fixing the problem is not difficult.

My recommended solution is to remove the offending non-Ubuntu source, uninstall all software from that source, purge the packages in your cache from that source, rebuild your dpkg database without that source, and try to get back to a functioning package manager.

You will not be able to install or remove any packages, including security updates, until you repair your system.

It's not difficult to do, and it's a good learning experience.

---

### Post by momaiaz on 2015-09-03
> **ian-weisser said:**
> Let's see what rmadison says about dpkg in 14.04:
```

$ rmadison dpkg
 dpkg | 1.17.5ubuntu5     | trusty           | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 dpkg | **1.17.5ubuntu5.4**   | trusty-security  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 dpkg | **1.17.5ubuntu5.4**   | trusty-updates   | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

There's your problem.
You seem to have tried to add non-Ubuntu software that demands a different (higher) version of dpkg than Ubuntu provides...but didn't provide the package itself...or the new package was not installable. That's called a *version conflict* and it falls under "you have requested an impossible situation" in the error message.

This is the risk you take when adding non-Ubuntu software.
Happily, fixing the problem is not difficult.

My recommended solution is to remove the offending non-Ubuntu source, uninstall all software from that source, purge the packages in your cache from that source, rebuild your dpkg database without that source, and try to get back to a functioning package manager.

You will not be able to install or remove any packages, including security updates, until you repair your system.

It's not difficult to do, and it's a good learning experience.

Yes ,, i added some external resources ...

Her what i did to fix it ,, i remove all external resources and clean packages and cache ,,
that not help << but i added kali sana resources of packages not security
then update and install apache2 and it works fine :D

---

### Post by ian-weisser on 2015-09-03
> **momaiaz said:**
> Her what i did to fix it ,, i remove all external resources and clean packages and cache ,,
that not help << but i added kali sana resources of packages not security
then update and install apache2 and it works fine :D

I am happy you seems to be satisfied with the solution you found.
Adding *more* non-Ubuntu software is usually not a recommended solution. It usually means your system is fragile, vulnerable to breakage from untested updates.
Do keep regular backups of your server's data.

---

### Post by momaiaz on 2015-09-03
> I am happy you seems to be satisfied with the solution you found.
Adding *more* non-Ubuntu software is usually not a recommended solution.  It usually means your system is fragile, vulnerable to breakage from  untested updates.
Do keep regular backups of your server's data.

aha ,, do you have better solution ?? .. Please tell my in simple way ,, Thx

---

### Post by ian-weisser on 2015-09-03
> **momaiaz said:**
> aha ,, do you have better solution ?? .. Please tell my in simple way ,, Thx

See post #5.

---

### Post by momaiaz on 2015-09-03
> **ian-weisser said:**
> See post #5.

Thank you ,,, :)

---

