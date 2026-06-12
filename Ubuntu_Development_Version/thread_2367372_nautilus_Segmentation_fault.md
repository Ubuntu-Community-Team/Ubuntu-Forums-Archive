---
title: "nautilus Segmentation fault"
date: 2017-07-29
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2017-07-29
After todays updates, when opening nautilus,
```
$ nautilus 
Segmentation fault (core dumped)

```
On both wayland and X11.
Further looks I get:
```
journalctl -q | grep -i nautilus
Jul 29 06:27:04 me-750-417c dbus-daemon[2402]: Activating service name='org.gnome.Nautilus'
Jul 29 06:27:04 me-750-417c dbus-daemon[2402]: Successfully activated service 'org.gnome.Nautilus'
Jul 29 06:27:05 me-750-417c kernel: nautilus[3036]: segfault at 5f315c80 ip 00007f098600a18a sp 00007ffe8f829cd0 error 4 in libgobject-2.0.so.0.5304.0[7f0985fd5000+51000]
Jul 29 06:31:47 me-750-417c kernel: nautilus[3999]: segfault at ffffffff8a44b980 ip 00007fc17b5e318a sp 00007ffd0d358e70 error 5 in libgobject-2.0.so.0.5304.0[7fc17b5ae000+51000]
Jul 29 06:32:29 me-750-417c kernel: nautilus[4079]: segfault at 23e3e900 ip 00007fa348c4418a sp 00007ffd70f702a0 error 4 in libgobject-2.0.so.0.5304.0[7fa348c0f000+51000]

```
Anyone else?

---

### Post by dino99 on 2017-07-29
Reported as lp:1707346 bug, with the cause & workaround.

---

### Post by #&amp;thj^% on 2017-07-29
> **dino99 said:**
> Reported as lp:1707346 bug, with the cause & workaround.

Thanks! is there a link to the report?
Found it NM [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1707346](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1707346)

---

### Post by rrnbtter on 2017-07-29
Greetings,
Same here. I have been using MC which also opens in su mode.

In addition purging deja-dup fixes nautilus.

---

### Post by #&amp;thj^% on 2017-07-29
> **rrnbtter said:**
> Greetings,
Same here. I have been using MC which also opens in su mode.

Did you get it sorted out?

---

### Post by rrnbtter on 2017-07-29
Greetings,
@1fallen; I don't know what you mean by "sorted out" but everything I'm doing would be considered work-a-rounds. My nautilus is fine. I don't use deja-dup but it integrates with nautilus and nautilus was broken due the the recent update of deja-dup. If you use deja-dup you can install the previous version.

Edit: I will add that since deja-dup only integrates with nautilus, other FM's are un-affected.

---

### Post by #&amp;thj^% on 2017-07-29
> **rrnbtter said:**
> Greetings,
@1fallen; I don't know what you mean by "sorted out" but everything I'm doing would be considered work-a-rounds. My nautilus is fine. I don't use deja-dup but it integrates with nautilus and nautilus was broken due the the recent update of deja-dup. If you use deja-dup you can install the previous version.

Edit: I will add that since deja-dup only integrates with nautilus, other FM's are un-affected.
Yep thats what I meant,,,,"deja-dup" good to hear.:)

---

### Post by rrnbtter on 2017-07-29
Greetings,
I would say that since Nautilus is already ported to wayland and works, but deja-dup is not. Hooking deja-dup into Nautilus creates a fault. Just in case you think that deja-dup is working, it is, but not with su.

---

### Post by #&amp;thj^% on 2017-07-29
I never use deja-dup so I won't miss it.;)
Sometimes I misread/misunderstand your posts...just wanted to know if you figured it out was all.
> Same here. I have been using MC which also opens in su mode.
All is well on my end.:D

---

### Post by ventrical on 2017-07-29
> **1fallen said:**
> I never use deja-dup so I won't miss it.;)
Sometimes I misread/misunderstand your posts...just wanted to know if you figured it out was all.

All is well on my end.:D

Same bug here .. but I had the added caveat  of having the screen just blackout for 2 seconds while the update was going on. 

Regards..

---

### Post by rrnbtter on 2017-07-29
Greetings,

> **1fallen said:**
> 
Sometimes I misread/misunderstand your posts...just wanted to know if you figured it out was all.


I'm a retired Windows OS tech. So my posts are 50% technical and 50% mis-informed.  Sometimes difficult for a linux person to wade through.  I feel like i'm starting to get this Ubuntu thing though.

---

### Post by JonPaul on 2017-07-29
There has just been an update to deja-dup in the last couple of hours. nautilus is now fine!

---

### Post by Cavsfan on 2017-07-31
This is fixed now isn't it, when deja-dup and nautilus were just updated?
I haven't tried using deja-dup but, I did notice it's installed.

I had that same problem before with the seq fault trying to open nautilus.

This morning I noticed I have several more sessions to login to and the regular Gnome boots into X11 now and works fine.
Have not tried any other sessions.

---

### Post by rrnbtter on 2017-07-31
Greetings,
The segment fault has been fixed. I don't know if it worked before that because I don't use it. However the Unity part of the package has been removed for Gnome Wayland users.  If it needs root it probably still has the no root access problem. If I'm wrong that is a good sign we are moving forward.

---

