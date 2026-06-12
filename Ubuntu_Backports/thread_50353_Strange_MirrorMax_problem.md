---
title: "Strange MirrorMax problem"
date: 2005-07-20
forum: Ubuntu Backports
---

### Post by tzutolin on 2005-07-20
Hello, everyone

I did a fresh install today and then apt-get update.  

Synaptic said it failed with mirrormax but after reloading I can still see the backport package like sun-j2sdk...etc. Can anyone explain this problem?  \\:D/

---

### Post by codejunkie on 2005-07-20
[QUOTE=tzutolin]Hello, everyone

I did a fresh install today and then apt-get update.  

Synaptic said it failed with mirrormax but after reloading I can still see the backport package like sun-j2sdk...etc. Can anyone explain this problem?  \\:D/[/QUOTE]

sometimes the repos just go down for matinance and such the only thing you can do  is add a few extra backport repos to your /etc/apt/sources.list file and comment them out until you need them like in this case, and when one repo is down comment it out and use another.

---

### Post by ShaneAu on 2005-07-20
[QUOTE=codejunkie]sometimes the repos just go down for matinance and such the only thing you can do  is add a few extra backport repos to your /etc/apt/sources.list file and comment them out until you need them like in this case, and when one repo is down comment it out and use another.[/QUOTE]
 It's not down. I see what tzutolin is talking about infact, not sure why though. I will look into it  soon. Plently of traffic flowing out from Apache still - 1.1 MB/second.

---

### Post by ProdigySim on 2005-07-22
I'm getting the very same thing... It's weird.
I can still get the packages, but I don't seem to be getting any new ones.

---

### Post by ShaneAu on 2005-07-22
Ok. Now It's finally the end of the week, I can have a look at this problem - right now. :).

---

### Post by ShaneAu on 2005-07-22
Ok, I think it's because the main archive server doesn't contain a "Packages.bz2" file only "Packages.gz", I get HEAPS of 404 errors for requests for Packages.bz2, even though it doesn't really effect the updating process, you see the "failed" message in Synaptic Package Manager or "Ign" in command line "apt-get update".

That is all I can see as an issue, I think it would be good to get it fixed up as it will stop confusion.

This is a job for the person that manages the backports archive on the main server.

(Which is not me, I manage the main public server, not the MAIN server - which is only accessable by the mirrors to sync as fast as possible.)

---

### Post by jdong on 2005-07-22
Umm, sure, I'll make bz2's, if it REALLY makes you happy...

---

