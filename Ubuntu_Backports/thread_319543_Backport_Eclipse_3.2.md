---
title: "Backport Eclipse 3.2"
date: 2006-12-15
forum: Ubuntu Backports
---

### Post by marco.catunda on 2006-12-15
I've been developing a system using Eclipse IDE for Dapper server, the major motivation to use Dapper server is LTS support. But, at this moment, I would like to migrate all developer environment to Eclipse 3.2.  I don't think a good idea to update from dapper to edgy in our
development environment, because it will be diferent from production server (Dapper).

Is it feasible to backport Eclipse or is it a fat package?

Regards
--
Marco Catunda

---

### Post by berteh on 2007-01-09
vote +1 for a backport of eclipse 3.2 in dapper.

---

### Post by Rishi on 2007-01-09
Without backporting the Ubuntu package to Dapper, you should be able to run the Eclipse 3.2 binaries just fine, no? 

[http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/index.php](http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/index.php)

---

### Post by berteh on 2007-01-10
> **Rishi said:**
> Without backporting the Ubuntu package to Dapper, you should be able to run the Eclipse 3.2 binaries just fine, no?

Yes I do, sure, the binary of eclipse 3.2 runs perfectly on Dapper (at least with sun's java 5 sdk from the Ubuntu repository).

It's just a matter of installing it consistently with ubuntu's way of installing programs. I for instance put it in /usr/local/lib/eclipse3.2, with a hand made bash script that sets a few variables (mozilla_five_home a.o.), and an additional application-menu icon. works just great, but took me about 30 minutes to set up... and I'm ooooo so lazy ;o)

(I got the menu launcher and bash script from [http://doc.ubuntu-fr.org/applications/eclipse/hoary_breezy](http://doc.ubuntu-fr.org/applications/eclipse/hoary_breezy))

Thanks for your answer.

---

### Post by perez on 2007-01-13
+1 for eclipse 3.2

---

