---
title: "Brasero 0.7.0"
date: 2007-12-30
forum: Repositories &amp; Backports
---

### Post by exploder on 2007-12-30
Does anyone think that Brasero 0.7.0 will be backported for Gutsy? It is available for Hardy and Gutsy seems to meet the requirements for installation. I have not found a deb package yet for Gutsy.

---

### Post by m_gasior on 2008-01-01
[http://files.akl.lt/baltix-knoppix/Ubuntu/Baltix-Ubuntu_packages/dists/gutsy/brasero/](http://files.akl.lt/baltix-knoppix/Ubuntu/Baltix-Ubuntu_packages/dists/gutsy/brasero/)

---

### Post by exploder on 2008-01-01
Thank you very much for finding that! Thank you!

---

### Post by paulle on 2008-01-03
thank you too.

---

### Post by syxbit on 2008-01-05
i'm running 64bit
i noticed i could just download it from hardy repos, but will this work in gutsy?
i may just try to compile it

---

### Post by syxbit on 2008-01-05
just compiled it
i really like the improvements.

---

### Post by meho_r on 2008-01-05
I compiled it too. Nice. Any idea how to get playlist option (when creating audio CDs)? It's compiled without it when going through standard compiling procedure...

---

### Post by steeleyuk on 2008-01-12
The improvements to this really should make it available by default into Hardy. Its got to be the easiest to use burning application available on Linux although I'd like to see it catch up with K3B in terms of some features.

---

### Post by Bri0 on 2008-01-15
Gives me this error for the .deb.

Error: Dependency is not satisfiable: libpango1.0-0

What to do? :confused:


Thanks

---

### Post by steeleyuk on 2008-01-15
libpango is in the Gutsy main repository so it should install. Just try an apt-get install libpango1.0-0 and see what happens. Maybe it got uninstalled for some reason...

---

### Post by Bri0 on 2008-01-15
^
No its installed. I even reinstalled (libpango1.0-0) but it still gives me the error.

---

### Post by m_gasior on 2008-01-15
Try to install libpango1.0-0_1.18.3-0ubuntu1 (gutsy-updates)

Add to you repo list:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main universe restricted

---

