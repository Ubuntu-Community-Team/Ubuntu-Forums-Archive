---
title: "Update question"
date: 2012-02-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by exploder on 2012-02-12
Anyone else having a problem with the Gwibber update wanting to remove the ubuntu-desktop package? Everything else has updated fine except this but I have not seen anyone else mention this particular issue.

---

### Post by vasa1 on 2012-02-12
> **exploder said:**
> Anyone else having a problem with the Gwibber update wanting to remove the ubuntu-desktop package? Everything else has updated fine except this but I have not seen anyone else mention this particular issue.

Not PP but older ... [http://ubuntuforums.org/showthread.php?t=1884912](http://ubuntuforums.org/showthread.php?t=1884912). Here, wanting to remove Gwibber meant removing ubuntu-desktop package!

---

### Post by xyzzyman on 2012-02-12
It's just waiting for a dependancy to hit the repo. Take a look at the sticky at the top of the +1 forum about 'partial upgrades'. You are advised to just wait until the dependancy appears and let it install then without uninstalling anything.

---

### Post by exploder on 2012-02-12
I see the problem now. The other packages associated with gwibber are 3.3.3-Oubuntu1 but the package that will not install is version 3.3.3-Oubuntu2. I am guessing that future updates will fix this and the application still works the way it is.

---

### Post by ernestj on 2012-02-12
I did it and lost the desktop. It was a fresh install, so I just installed it again, but avoided the partial upgrade. I do update, however.

ernie

---

### Post by xyzzyman on 2012-02-12
> **exploder said:**
> I see the problem now. The other packages associated with gwibber are 3.3.3-Oubuntu1 but the package that will not install is version 3.3.3-Oubuntu2. I am guessing that future updates will fix this and the application still works the way it is.

Yeah, it'll just keep running the current of everything.

The reason this happens is the developers are using newer versions of files that may not have been compiled and uploaded to your repositories mirror yet. That's why sometimes you'll see some people were able to upgrade but you couldn't. 

Be kind to the servers though and don't 'sudo apt-get update' every 30 seconds. Bandwith = money. It all comes in due time.

---

### Post by ventrical on 2012-02-13
> **xyzzyman said:**
> Yeah, it'll just keep running the current of everything.

The reason this happens is the developers are using newer versions of files that may not have been compiled and uploaded to your repositories mirror yet. That's why sometimes you'll see some people were able to upgrade but you couldn't. 

Be kind to the servers though and don't 'sudo apt-get update' every 30 seconds. Bandwith = money. It all comes in due time.


How true .. I get usage charges up here in Canada!:(

---

