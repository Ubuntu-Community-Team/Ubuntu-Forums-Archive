---
title: "cvsd - permissions problem?"
date: 2005-07-10
forum: Server Platforms
---

### Post by aCiD2 on 2005-07-10
Hi,

I've just got cvsd using apt-get, and created a user for myself, and a repo. But, when I try and create a module with Eclipse I get an error.

cvs add: cannot mkdir /cvsroot/MyTeamProject: Permission denied.

Any ideas? Presumably cvsd has to be run with root priveliges?

---

### Post by mriya3 on 2005-09-15
I had the same problem, and I solved it by changing the group of the cvs repos directory in /var/lib/cvsd

```
cd /var/lib/cvsd
sudo chgrp -R cvsd yourreposdir
```

---

