---
title: "HoaryHedgeHog and MONO?"
date: 2005-05-24
forum: Repositories &amp; Backports
---

### Post by merrittr on 2005-05-24
I would like to run MONO and MonoDeveloper on my UBUNT HH machine unfortunatly:

after putting 
deb [http://debian.meebey.net/](http://debian.meebey.net/) ./
in sources.list

and typed apt-get install mono and got:

root@ubuntu:/etc/apt # apt-get install mono
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono: Depends: mono-common (= 1.1.6-3) but it is not going to be installed
        Depends: mono-jit (= 1.1.6-3) but it is not going to be installed
E: Broken packages



Help!

---

### Post by tread on 2005-05-24
Don't use the debian repository .. ubuntu backports has mono/monodevelop I think. You'll find more info in the 3rd party projects section of this same forum.

---

