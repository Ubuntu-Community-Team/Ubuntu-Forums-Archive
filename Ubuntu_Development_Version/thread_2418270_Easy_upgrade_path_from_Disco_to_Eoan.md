---
title: "Easy upgrade path from Disco to Eoan"
date: 2019-05-04
forum: Ubuntu Development Version
---

### Post by mrfelker on 2019-05-04
I guess Ubuntu 19.10 eoan hasn't quite made it to the upgrade servers since all my attempts to use variations of upgrade-manager failed.   However by just using "sudo gedit /etc/apt/sources.list and changing all instances of "disoc " tp "eoan" (without quotes. Rebooting and running "sudo apt-get update && sudo apt-get -y dist-upgrade" did the job quite nicely.   Looks like a lot of development on the kde side at the moment but I haven't used that desktop yet.  I'm hoping I can upgrade without re-installing until next April but you never know.

---

### Post by cariboo on 2019-05-04
Next time use this to do the upgrade:

```
sudo sed -i 's/disco/eoan/g' /etc/apt/sources.list
```

then

```
sudo apt update && sudo apt dist-upgrade
```

---

### Post by mrfelker on 2019-05-06
The real point is that Ubuntu linux can be upgraded to a new version just by editing (or using sed) a single text file.   Compare and contrast to Windows (which I only run these in a VM).

---

