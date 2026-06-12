---
title: "python 2 end of support"
date: 2019-12-27
forum: Security
---

### Post by jsvidyad on 2019-12-27
Hello,
  
    I use Ubuntu 18.04. Python 2 end of support date is January 1, 2020. Python 2 is installed on my system and I was wondering if Ubuntu will be providing security updates to Python2 after that date through the repositories. If Ubuntu won't provide security updates after that date, should I purge Python 2 from my system in order to keep my system secure? I currently do have a few programs that depend on Python 2 and would rather not have them purged unless absolutely necessary.

---

### Post by deadflowr on 2019-12-27
> Python 2 is installed on my system and I was wondering if Ubuntu will be providing security updates to Python2 after that date through the repositories. 
All packages from the main repository are guaranteed support for the full 5 years. End of life upstream means all fixes have to be done in-house.
Case in point, the 4.15 linux kernel that ships with 18.04's original release will be supported the full 5 but hasn't been supported upstream since around the time 18.04 was released.
> should I purge Python 2 from my system in order to keep my system secure?
Python is fairly core to the system, especially for the Desktop release.
So I wouldn't recommend removing it as that can break everything.

---

### Post by kevdog on 2019-12-27
You could just install pyenv and do things that way..just another option

---

