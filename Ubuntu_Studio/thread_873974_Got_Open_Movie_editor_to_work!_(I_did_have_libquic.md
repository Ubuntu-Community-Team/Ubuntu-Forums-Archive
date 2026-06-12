---
title: "Got Open Movie editor to work! (I did have libquicktime.so.0 error)"
date: 2008-07-29
forum: Ubuntu Studio
---

### Post by nitromanrc on 2008-07-29
Hey guys, I was having problems with OME (from the repos), when i tried starting it I was getting this:```
openmovieeditor: error while loading shared libraries: libquicktime.so.0: cannot open shared object file: No such file or directory

```

and here is the fix

```
$ cd /usr/lib
$ sudo ln libquicktime.so.1 libquicktime.so.0
```

this might be a dirty fix, I haven't had a whole lot of time to test the stability, but it at least gets it started

---

### Post by skipx on 2008-09-07
Thanks!, also works for Pure Data with GEM library, but then opposite..
(ubuntu 8.0.4 hardy)
I always use ln -s instead of just ls..

```
$ sudo ln [COLOR="Red"]-s[/COLOR] libquicktime.so.[COLOR="Red"]0[/COLOR] libquicktime.so.[COLOR="Red"]1[/COLOR]
```

---

### Post by simon_ives on 2008-10-01
I recently heard somewhere about OME so thought I'd give it a go and experienced the same problem from the Repos.  The following worked:
```
$ sudo ln -s libquicktime.so.0 libquicktime.so.1
```
The following didn't:
```
$ sudo ln libquicktime.so.1 libquicktime.so.0
```

---

### Post by Evil_Donkey on 2008-10-01
Try this:
```
sudo ln /usr/lib/libquicktime.so.1 /usr/lib/libquicktime.so.0

```
That worked fine for me. Make sure you have libquicktime1 installed

```
sudo apt-get install libquicktime1
```

---

