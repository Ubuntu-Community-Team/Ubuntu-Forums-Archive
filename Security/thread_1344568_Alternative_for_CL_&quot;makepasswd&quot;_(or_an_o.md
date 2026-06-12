---
title: "Alternative for CL &quot;makepasswd&quot; (or an option)"
date: 2009-12-03
forum: Security
---

### Post by krimzonstarr on 2009-12-03
Hi, hopefully this will be a short and sweet post, and a short and sweet answer. I have recently fallen in love with the CLI program "makepasswd." Unfortunately, I want something that can do special characters as well, beyond Aa-Zz/0-9. I can't seem to get "makepasswd" to do that, and I would like to include !@#$ etc. Note, I do not want a "Password Safe" program, or graphical utility. Thank you in advance for anyone's input!

EDIT
[http://ubuntuforums.org/showthread.php?t=299823&highlight=password+generator]("http://ubuntuforums.org/showthread.php?t=299823&highlight=password+generator")

Looks like insomnia and wandering around the always fun ubuntuforums answered my question, but I like variety... If anyone has any other suggestions, I would be happy to hear them!  :KS

---

### Post by Sarmacid on 2009-12-03
I've used pwgen and it's been good so far, it's also on the repos```
sudo apt-get install pwgen
pwgen -sy 30
```

---

### Post by krimzonstarr on 2009-12-03
> **Sarmacid said:**
> ```
sudo apt-get install pwgen
pwgen -sy 30
```

Thank you! This is a much nicer alternative, and blazing fast.

---

