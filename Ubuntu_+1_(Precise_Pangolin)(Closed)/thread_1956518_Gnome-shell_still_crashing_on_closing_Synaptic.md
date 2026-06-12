---
title: "Gnome-shell still crashing on closing Synaptic"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2012-04-11
As soon as SPM is closed GS stops responding for a few seconds then crashes and reloads.
This has been going on here for a few weeks now and on two separate installations.
Running 2 fully updated 64 bit installs here.

Bug report here
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/978727](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/978727)

Anybody else seeing this?

---

### Post by ronacc on 2012-04-11
its been freezing on me when synaptic closed , I never waited long enough for it to decide to restart itself , just put it down to all the updates and rebooted using a term .Doing my morning update now I'll wait and see if it restarts itself .

---

### Post by lovinglinux on 2012-04-11
I have experienced such crashes when installing and upgrading, either through Synaptic or via terminal.

---

### Post by ronacc on 2012-04-11
after this mornings updates GS did not freeze on closing synaptic on my 64bit sys . If you haven't updated in a few hours try again now .

---

### Post by sgage on 2012-04-11
> **Quackers said:**
> As soon as SPM is closed GS stops responding for a few seconds then crashes and reloads.
This has been going on here for a few weeks now and on two separate installations.
Running 2 fully updated 64 bit installs here.

Bug report here
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/978727](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/978727)

Anybody else seeing this?

I have had various freeze/crash/reloads during software updates with Synaptic, but I wouldn't say they were associated with closing it.

I have been finding GS to be more crashy in general the past couple of days. We'll see how it goes after today's updates.

---

### Post by Harry33 on 2012-04-11
I have experienced gnome-shell crashing and then automatically restarting for a long time now.
It really seems to be connected to the use of Synaptic some how, either only using Synaptic or perhaps closing it.

---

### Post by ricotz on 2012-04-11
This is caused by the dpkg-trigger to update icon-theme caches. 
The problem is fixed in git master and will be released with 3.4.1. 

[http://git.gnome.org/browse/gnome-shell/commit/?id=00091a2acb40a3237b9abf90fbc42ffd010c7780](http://git.gnome.org/browse/gnome-shell/commit/?id=00091a2acb40a3237b9abf90fbc42ffd010c7780) [http://git.gnome.org/browse/gnome-shell/commit/?id=0a7968a2e55cb9c7063d65663d5bff504724f7a8](http://git.gnome.org/browse/gnome-shell/commit/?id=0a7968a2e55cb9c7063d65663d5bff504724f7a8)

---

### Post by Quackers on 2012-04-11
Thanks all. I seem to be consistently finding the same as Harry33.
Have now run today's updates via synaptic - and GS didn't crash :-) 
We'll see.

Thanks ricotz for the cause and the likely fix :-)

---

### Post by Quackers on 2012-04-12
After more investigation it seems that GS is crashing after using synaptic, but only when I next move the pointer to top left. 
It isn't synaptic closing that upsets GS, it's just once synaptic is closed the next movement of the pointer to top left (to get the menus etc) crashes GS.

---

### Post by dino99 on 2012-04-12
> **Quackers said:**
> After more investigation it seems that GS is crashing after using synaptic, but only when I next move the pointer to top left. 
It isn't synaptic closing that upsets GS, it's just once synaptic is closed the next movement of the pointer to top left (to get the menus etc) crashes GS.

Look at post #7 above  (have to wait for upgrade)

---

### Post by Quackers on 2012-04-12
dino99, I saw that but am not sure it is the same problem. 
Have updated the bug report.

---

### Post by dino99 on 2012-04-12
> **Quackers said:**
> dino99, I saw that but am not sure it is the same problem. 
Have updated the bug report.

Ricotz seems have no doubt, so i trust him :)

---

### Post by Quackers on 2012-04-12
That's true :-)

---

