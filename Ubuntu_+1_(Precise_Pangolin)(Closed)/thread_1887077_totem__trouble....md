---
title: "totem : trouble... ?"
date: 2011-11-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-11-26
```
:~$ totem
failed to create drawable

Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context

Gdk-ERROR **: The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadGC (invalid GC parameter)'.
  (Details: serial 155 error_code 13 request_code 60 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap
```

---

### Post by madjr on 2011-11-26
what version?

new versions need clutter.

they said they were going to use an older version by default that doesnt need it. They dont want to have clutter by default in this lts.

---

### Post by mc4man on 2011-11-26
regarding totem version in PP
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-video-playback](https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-video-playback)

---

### Post by zika on 2011-11-26
> **madjr said:**
> what version?

new versions need clutter.

they said they were going to use an older version by default that doesnt need it. They dont want to have clutter by default in this lts.
totem 3.2.1-0ubuntu1~precise2

I looked into downgrading to 3.0.1-0ubuntu10(precise) but it involves a bunch of other packages...
We'll see..

---

### Post by madjr on 2011-11-26
> **zika said:**
> totem 3.2.1-0ubuntu1~precise2

I looked into downgrading to 3.0.1-0ubuntu10(precise) but it involves a bunch of other packages...
We'll see..

 is that the default in precise ?

(sorry am not testing 12.04 yet)

---

### Post by crdlb on 2011-11-26
[https://launchpad.net/ubuntu/+source/totem](https://launchpad.net/ubuntu/+source/totem)

Totem 3.2 is not in Precise. You must be using a PPA.

---

### Post by Harry33 on 2011-11-27
> **zika said:**
> totem 3.2.1-0ubuntu1~precise2

I looked into downgrading to 3.0.1-0ubuntu10(precise) but it involves a bunch of other packages...
We'll see..

The version 3.2.1-0ubuntu1~precise2 comes from the Gnome3 Team PPA (Ricotz).
Have you enabled also the Gnome-shell Testing PPA and installed clutter?
If not, then purge Gnome3 Team PPA.

---

### Post by zika on 2011-11-27
> **Harry33 said:**
> The version 3.2.1-0ubuntu1~precise2 comes from the Gnome3 Team PPA (Ricotz).
Have you enabled also the Gnome-shell Testing PPA and installed clutter?
If not, then purge Gnome3 Team PPA.
Yes I did ;(

```
$ sudo ppa-purge ppa:gnome3-team/gnome3
[sudo] password for zika: 
Updating packages lists
PPA to be removed: gnome3-team gnome3
Warning:  Could not find package list for PPA: gnome3-team gnome3

```What is more sad is that, I think, I spent most time in {Flux,Open}Box and in vanilla metacity (.Xsession), gnome-shell and similar dm do not even work at this moment on my machine... ;)
I'll struggle with that postponing reinstall as further as possible... ;)
I'll, just, be as brave tester as I possibly could... ;)

---

### Post by zika on 2011-11-27
> **zika said:**
> Yes I did ;(

```
$ sudo ppa-purge ppa:gnome3-team/gnome3
[sudo] password for zika: 
Updating packages lists
PPA to be removed: gnome3-team gnome3
Warning:  Could not find package list for PPA: gnome3-team gnome3

```What is more sad is that, I think, I spent most time in {Flux,Open}Box and in vanilla metacity (.Xsession), gnome-shell and similar dm do not even work at this moment on my machine... ;)
I'll struggle with that postponing reinstall as further as possible... ;)
I'll, just, be as brave tester as I possibly could... ;)

I've made it. For the time being I've divorced (with scars) from ricotz... ;) All 3 (was 4) PPA's...
Totem (with scars) work...

---

### Post by Harry33 on 2011-11-27
This is solved then?

---

### Post by zika on 2011-11-27
> **Harry33 said:**
> This is solved then?
Depends from which point Your are lookig at.
For me, for the time being, it is.
Generally, I feel it is not.
You want me to mark it „solved“?

---

### Post by Harry33 on 2011-11-27
> **zika said:**
> Depends from which point Your are lookig at.
For me, for the time being, it is.
Generally, I feel it is not.
You want me to mark it „solved“?

Just wanted to know whether you think this is solved.
If not, then could you clarify is this a totem issue or not (according to the heading of this thread).

---

### Post by zika on 2011-11-27
> **Harry33 said:**
> Just wanted to know whether you think this is solved.
If not, then could you clarify is this a totem issue or not (according to the heading of this thread).Didn't we got to agreement, proven by (among other) my purge of ricotz ppa's, that problem is between Totem and clutter...? It is not, strictly speaking, PP problem since those PPA's are not in PP, officially, so...
I'll mark it [Solved], it is easier...

---

### Post by Harry33 on 2011-11-27
> **zika said:**
> Didn't we got to agreement, proven by (among other) my purge of ricotz ppa's, that problem is between Totem and clutter...? It is not, strictly speaking, PP problem since those PPA's are not in PP, officially, so...
I'll mark it [Solved], it is easier...

Now that is OK with me.
However, you are right when you say there is problem with Totem and Clutter.
One problem is that they do not want Clutter to be part of the default 12.04 LTS setup.
This, in turn, means only a part of the released Gnome 3.4 will be pulled in.

---

### Post by ricotz on 2011-11-27
> **zika said:**
> ```
:~$ totem
failed to create drawable

Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context

Gdk-ERROR **: The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadGC (invalid GC parameter)'.
  (Details: serial 155 error_code 13 request_code 60 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap
```

 This doesn't look like a Totem or Clutter issue. It looks more like a broken x-driver which doesn't provider 3d acceleration. You probably couldn't ran gnome-shell or compiz either. But since you already reverted everything this seems to be finished then. ;)

---

