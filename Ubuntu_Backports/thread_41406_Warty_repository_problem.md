---
title: "Warty repository problem"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by robre77 on 2005-06-13
Hello everyone.
I'm having troubles with warty backports repository...
"apt-get update" claims it cannot find the "Packages.gz" file, i cannot find it anywhere.

Here are my /etc/apt/sources.list entries:
(as described in backports homepage)
----------------------- SNIP ---------------
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) warty-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) warty-extras main universe multiverse restricted
----------------------- SNIP ---------------

Where's my fault?

TIA
Roberto

---

### Post by jdong on 2005-06-13
it's my fault. Thanks for bringing this to my attention... I must've forgotten Warty after my new Packages.gz system kicked in.

---

### Post by CAE on 2005-06-13
Edit: D'oh, too slow. :)

I don't believe you're at fault. I think there was a change to how the mirrors picked up the package list (Packages.gz), and apparently the changes weren't done in the Warty sections, so it's not on the mirrors.

Maybe you should just do a dist-upgrade?

---

### Post by jdong on 2005-06-13
Ok, I've fixed this on the master server. It should start working from mirrormax in 60 minutes.

---

### Post by robre77 on 2005-06-14
[QUOTE=jdong]it's my fault. Thanks for bringing this to my attention... I must've forgotten Warty after my new Packages.gz system kicked in.[/QUOTE]
 
Thanks for fixing that little bug   :smile: 

Now, a good news for (especially) Italian users: a new backports mirror on:
**[http://cdn.mirror.garr.it/mirrors/ubuntu-backports/](http://cdn.mirror.garr.it/mirrors/ubuntu-backports/)**
taken directly from mirrormax.

Hope this is useful to everyone.

Roberto

---

