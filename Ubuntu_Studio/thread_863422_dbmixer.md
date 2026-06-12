---
title: "dbmixer"
date: 2008-07-18
forum: Ubuntu Studio
---

### Post by GoCool on 2008-07-18
I have installed dbmixer by going to Synaptic Package Manager and selecting dbmix. Now how to run it?

When I give dbmixer in the terminal I get this error

> 
DBMixer ERROR: could not create shared memory for system data.
 Hint: Make sure that dbfsd has been started.
 errno: : No such file or directory
DBMixer: could not detach memory segment.: Invalid argument

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkObject'

Gtk-CRITICAL **: file gtksignal.c: line 724 (gtk_signal_connect): assertion `object != NULL' failed.


Any help?

---

### Post by sydney-troz on 2008-08-24
Run

dbfsd

---

### Post by afrodeity on 2009-05-01
> **sydney-troz said:**
> Run

dbfsd

tried this with Hardy. Terminal.

```
init_audio: cannot open device "/dev/dsp": Device or resource busy
Could not open main audio device.: Illegal seek
```

---

### Post by afrodeity on 2009-05-18
I gave up on DBmixer, its broken, and found a really cool mixer called Mixxx. It is in the repository

```
 sudo apt-get install Mixxx
```

---

