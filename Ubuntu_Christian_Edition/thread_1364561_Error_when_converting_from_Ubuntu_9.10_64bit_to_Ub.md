---
title: "Error when converting from Ubuntu 9.10 64bit to UbuntuCE 64bit"
date: 2009-12-26
forum: Ubuntu Christian Edition
---

### Post by CD27 on 2009-12-26
The following packages have unmet dependencies:
  ubuntu-ce: Depends: wine-christian-repos but it is not going to be installed
E: Broken packages

---

### Post by david_kt on 2009-12-27
> **CD27 said:**
> The following packages have unmet dependencies:
  ubuntu-ce: Depends: wine-christian-repos but it is not going to be installed
E: Broken packages

Could you try:

```
sudo apt-get install wine-christian-repos
```

and post here the error.

DK

---

