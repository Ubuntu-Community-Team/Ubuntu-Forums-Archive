---
title: "Broken Packages/Depends: not installable."
date: 2006-08-06
forum: Repositories &amp; Backports
---

### Post by snowblind on 2006-08-06
First of all thank you for taking the time to at least read about my issues. Second of all if i do resolve this issue I will post here how to fix it for anyone else searching in the future. Thirdly I have done alot of searching and not come up with a solution specific to my problem.
------

Now to the issue: Simply put my dependancies seem broken. Yesterday i tried to install banshee via apt-get and well see for yourself.

```

snowblind@SnowMachine:~$ sudo apt-get install banshee
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

The following packages have unmet dependencies.
  banshee: Depends: mono-jit (>= 1.0) but it is not installable
           Depends: libdbus-1-cil (>= 0.60) but it is not installable
           Depends: libgconf2.0-cil (>= 2.7.90) but it is not installable
           Depends: libglade2.0-cil (>= 2.7.90) but it is not installable
           Depends: libglib2.0-cil (>= 2.7.90) but it is not installable
           Depends: libgnome2.0-cil (>= 2.7.90) but it is not installable
           Depends: libgtk2.0-cil (>= 2.7.90) but it is not installable
           Depends: mono-classlib-1.0 (>= 1.0) but it is not installable
E: Broken packages

```

Everything I try to install now gives me a similar message with different dependancies.

I have tried sudo apt-get -f install/upgrade/dist-upgrade which does nothing.

Any advice or resolutions for this issue will be greatly appreciated.

---

### Post by snowblind on 2006-08-06
[http://www.ubuntuforums.org/showpost.php?p=1153974&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1153974&postcount=6)

That post solved my issue.

---

