---
title: "passing mount options to autofs5 via init script"
date: 2010-05-07
forum: Server Platforms
---

### Post by FISHMANPET on 2010-05-07
At work we use autofs4, and we also take advangate of the -DOSNMAE=blah and -DOSREL=blah for our automount maps.  We're moving some systems to autofs5 and I can't for the life of me figure out how to pass these options properly.  There's no 'localoptions' in the init script anymore as there was for autofs4.  I've tried adding the flags to the OPTIONS variable in /etc/default/autofs.  That adds them to the global autofs process but then nothing in the automounter mounts.  

So how do I pass options to the autofs5 automounter?

---

### Post by eclypse80 on 2010-05-24
I'm also curious as to how this is done in /etc/default/autofs. I've tried various things to no avail.

An alternative is to add them in /etc/auto.master, like so:

/mymountpoint      my.map.name noacl

The example above should then include 'noacl' in the list of options for all shares under that autofs map.

---

### Post by FISHMANPET on 2010-05-24
I posted to the autofs mailing list and got the answer I was looking for.  All I had to add was this to /etc/default/autofs:
OPTIONS="-DOSNAME=name -DOSREL=rel"

---

### Post by eclypse80 on 2010-05-27
Thanks, I see your thread:

[http://linux.kernel.org/pipermail/autofs/2010-May/006084.html](http://linux.kernel.org/pipermail/autofs/2010-May/006084.html)

I think you omitted -O in your reply here? Regardless, here's what I had to do to pass the noacl and sec=sys options to my machines:

OPTIONS="-O noacl,sec=sys"

---

