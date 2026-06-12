---
title: "TrueCrypt - Hidden Volume Protection"
date: 2010-01-22
forum: Security
---

### Post by cforput on 2010-01-22
I installed TrueCrype 6.3a on my 8.1 Ubuntu. Everything went fine until I got to the part where I need to protect my hidden volume from damaged caused by writing to the outer volume (these instructions: [http://www.truecrypt.org/docs/hidden-volume-protection](http://www.truecrypt.org/docs/hidden-volume-protection) ). I can't find the checkbox to "Protect hidden volume from damaged caused by writing to outer volume". The closest thing I can find is an option to "Protect hidden volume when mounting outer volume". Intuitively these don't sound the same to me. There are 2 difference between my setup and the instructions; 1) the instructions appear to be written for Windows and not Linux. 2) I am using a file volume and not a partition volume.

Does anyone know where the option is to protect the hidden volume when writing to the outer volume?

---

### Post by adam814 on 2010-01-22
I'm guessing they're the same option.  I think it's an option you have to enable each time you mount the volume (otherwise why have an outer volume if it gets labeled as outer?).  I wouldn't use the outer volume that much just to be sure I didn't overwrite anything in the hidden volume.

---

### Post by doas777 on 2010-01-22
sounds the same to me. I wonder how much space you lose in the internal volume, by enabling it.

---

