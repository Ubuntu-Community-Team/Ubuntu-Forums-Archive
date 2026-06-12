---
title: "Serpentine 0.5"
date: 2005-05-11
forum: Ubuntu Backports
---

### Post by J.K.Makowka on 2005-05-11
[http://s1x.homelinux.net/projects/serpentine/](http://s1x.homelinux.net/projects/serpentine/)

Already in breezy, but would be great for hoary (without adding the breezy rep. to hoary)

---

### Post by ow50 on 2005-06-03
I just noticed that this has been backported.

I get the following error trying to run it:
```
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 52, in ?
    app = SerpentineApplication ()
  File "/usr/lib/python2.4/site-packages/serpentine/__init__.py", line 59, in __init__
    self.__preferences = RecordingPreferences ()
  File "/usr/lib/python2.4/site-packages/serpentine/preferences.py", line 72, in __init__
    self.__update_speed ()
  File "/usr/lib/python2.4/site-packages/serpentine/preferences.py", line 102, in __update_speed
    assert speed > 0
AssertionError
```

---

### Post by jdong on 2005-06-03
strange... I don't get that.

Anyone else can reproduce this?


In any case, I'm holding this back from 6/3 promotions.

---

### Post by JDay on 2005-06-04
I get the same error.

---

### Post by Slo Mo Snail on 2005-06-04
For me it's working ;)

Seems to be some check whether your cdwriter supports speeds faster than 0 (without looking at the code... just an assumption)

Do you have one and can you access it as the user you run serpentine with?

---

### Post by ow50 on 2005-06-04
[QUOTE=Slo Mo Snail]Do you have one and can you access it as the user you run serpentine with?[/QUOTE]
Yes, I have a CD-writer. I should be able to access it as user. Running serpentine as sudo causes the exact same crash.

---

### Post by ow50 on 2005-06-08
It could well be that the problem is that serpentine doesn't recognize my burner. It took quite many versions of GnomeBaker as well before my burner was recognized.  Either way this is probably not a packaging problem, just an early development stage app with bad exception handling. So, jdong, feel free to move this to stable if works for others.

---

### Post by macleod199 on 2005-06-12
From the Serpentine homepage [http://s1x.homelinux.net/projects/serpentine/](http://s1x.homelinux.net/projects/serpentine/)

> Note: if you use Ubuntu you just need to install the package python-gnome2-extras, just search it and install it with Synaptic under System/Synaptic Package Manager or through the command line

This doesn't seem to fix the problem for me, but should this maybe be in its dependency list?

---

### Post by dodongo on 2005-06-12
FWIW, I grabbed this last night because I needed a burner for my FLAC files, and I had no problems with it.  Though the rough edges in the program are still evident, it did not crash on my box.

---

### Post by Mez on 2005-06-12
well, if it needs that package aswell, shouldnt that package be in the depends?

---

### Post by dlpfmVfH on 2005-06-16
[QUOTE=ow50]I just noticed that this has been backported.

I get the following error trying to run it:
```
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 52, in ?
    app = SerpentineApplication ()
  File "/usr/lib/python2.4/site-packages/serpentine/__init__.py", line 59, in __init__
    self.__preferences = RecordingPreferences ()
  File "/usr/lib/python2.4/site-packages/serpentine/preferences.py", line 72, in __init__
    self.__update_speed ()
  File "/usr/lib/python2.4/site-packages/serpentine/preferences.py", line 102, in __update_speed
    assert speed > 0
AssertionError
```[/QUOTE]

I still get the error...running as sudo or as normal user makes no difference,
installed the suggested package, and found out it was already installed...
gnomebaker, works, k3b works...but serpentine..doesn't...

can I change the preferences.py ?? and so what should be changed...

---

### Post by cogumbreiro on 2005-06-28
[QUOTE=ow50]I just noticed that this has been backported.

I get the following error trying to run it:
```
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 52, in ?
    app = SerpentineApplication ()
  File "/usr/lib/python2.4/site-packages/serpentine/__init__.py", line 59, in __init__
    self.__preferences = RecordingPreferences ()
  File "/usr/lib/python2.4/site-packages/serpentine/preferences.py", line 72, in __init__
    self.__update_speed ()
  File "/usr/lib/python2.4/site-packages/serpentine/preferences.py", line 102, in __update_speed
    assert speed > 0
AssertionError
```[/QUOTE]
 Hello there folks,

Serpentine 0.6.1 fixes that problem.

---

### Post by RaymondQE on 2005-06-28
I was having the same problem with serpentine 0.5 but when I changed the default_speed using the Gnome configuration editor (apps->nautilus-cd-burner->recording_speed), I stopped getting the error.  This might be a good workaround until the latest version is packaged.


  Anyways, great program cogumbreiro.  I love that you can load any gstreamer compatible music file and are able to burn it to a cd.

---

### Post by rwabel on 2005-07-09
I get the following error message:
<code>Traceback (most recent call last):
  File "/usr/local/bin/serpentine", line 2, in ?
    import gtk, sys, gobject, gnome, os
ImportError: No module named gtk</code>

what could the problem be?

---

### Post by tnasniv on 2006-02-26
Same problem here
```

vincent@ubuntu:/usr/bin$ serpentine
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 2, in ?
    import gtk
ImportError: No module named gtk
```

I'm under dapper

---

