---
title: "Problem in installing files"
date: 2011-12-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by navaleshubham10 on 2011-12-02
when install the following updates 
1:libunique-1.0-0 (size: 24 kb)
2:libx86-1 (size: 9 kb)
3:libzeitgeist-1.0-1 (size 42 kb)
 

it shows some error while installing. 
please help me 


my ubuntu release version is:

Description:    Ubuntu precise (development branch)
Release:    12.04
:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by BC59 on 2011-12-02
This is normal for a release on the very early stages of development. And the most interesting is the more changes you make to the original system, the most problems you have.

Did you try ?```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by oldos2er on 2011-12-03
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by 3vi1 on 2011-12-03
> **navaleshubham10 said:**
> 
it shows some error while installing. 
please help me 


Please post the error message.  You can probably find them in /var/log/apt/term.log.

---

