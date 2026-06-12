---
title: "upgrading?"
date: 2005-05-07
forum: Repositories &amp; Backports
---

### Post by lmellen on 2005-05-07
:) Does "aptitude update" & "aptitude upgrade" automatically update the system, or will I have to eventually burn a new disc for the next release?  I have hoary (Kubuntu) now. Excellent OS!! 
                                                                  Thanks -- larry

---

### Post by kvidell on 2005-05-07
[QUOTE=lmellen]:) Does "aptitude update" & "aptitude upgrade" automatically update the system, or will I have to eventually burn a new disc for the next release?  I have hoary (Kubuntu) now. Excellent OS!! 
                                                                  Thanks -- larry[/QUOTE]
 You'll update the name of the release in your /etc/apt/sources.list file then:
```
sudo apt-get update && sudo apt-get dist-upgrade
```- Kev

---

