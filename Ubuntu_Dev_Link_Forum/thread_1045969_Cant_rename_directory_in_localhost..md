---
title: "Cant rename directory in localhost."
date: 2009-01-21
forum: Ubuntu Dev Link Forum
---

### Post by CastilleV on 2009-01-21
I installed LAMP a few weeks ago, and moved a folder to the /var/www/ folder.
Only realizing I didn't rename it, and I tried to fix things using the terminal.

Is there some way I can rename it?

---

### Post by amauk on 2009-01-21
mv /path/to/old_name /path/to/new_name

---

### Post by CastilleV on 2009-01-21
> **amauk said:**
> mv /path/to/old_name /path/to/new_name

Already tried that, I get a permission denied.

---

### Post by amauk on 2009-01-21
use sudo
(gives you root privileges)

sudo mv /path/to/old_name /path/to/new_name

---

### Post by CastilleV on 2009-01-21
> **amauk said:**
> use sudo
(gives you root privileges)

sudo mv /path/to/old_name /path/to/new_name

Hey! :D It worked! Thanks!
Damn confusing terminal! But, its what I like about linux.

---

### Post by Tek-E on 2009-02-20
Question... Why is it you get the same results using the su command?
Is su just a shorter version for sudo?

---

### Post by Tek-E on 2009-02-20
Eeek nevermind. I just looked up the answer. And they arent necessarily the same command. :/  Embarresment!

---

