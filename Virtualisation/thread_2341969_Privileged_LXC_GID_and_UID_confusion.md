---
title: "Privileged LXC GID and UID confusion"
date: 2016-11-02
forum: Virtualisation
---

### Post by izznogooood on 2016-11-02
So, Im confused (What else is new). I´ve decided to dive in to LXC as this suits my needs as of this moment.

I am running a Privileged container (mediaserver) and mounting through "lxc.mount.entry".
This works fine but thats a coincidence as my user and the lxc user has the same UID (at least thats my theory) 

Take a look at this:

LXC
[ATTACH=CONFIG]271926[/ATTACH]

HOST
[ATTACH=CONFIG]271925[/ATTACH]


I´m guessing the same goes for GID?

So the question is: Is there a way to force the LXC to use a different ID or in anyway separate them from the main system ID´s so I could have more control.

---

