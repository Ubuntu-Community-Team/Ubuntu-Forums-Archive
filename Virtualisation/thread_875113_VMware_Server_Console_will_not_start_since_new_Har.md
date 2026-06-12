---
title: "VMware Server Console will not start since new Hardy update"
date: 2008-07-30
forum: Virtualisation
---

### Post by winger1312 on 2008-07-30
VMware Server console will start-up since the Linux headers update in Hardy.  Has anyone else had this problem?

---

### Post by fjgaude on 2008-07-30
Yes, yes... you have to re-run the:

```
sudo /usr/bin/vmware-config.pl
```

command.

Or if you used an any-any install then the **runme.pl** command from wherever you installed, used the any-any program.

---

### Post by winger1312 on 2008-07-30
Thanks that worked without a hitch!!!  Do not even know why I did not think of that

---

