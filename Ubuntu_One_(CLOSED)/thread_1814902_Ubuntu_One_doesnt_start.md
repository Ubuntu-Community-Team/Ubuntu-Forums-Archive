---
title: "Ubuntu One doesnt start"
date: 2011-07-30
forum: Ubuntu One (CLOSED)
---

### Post by YfoMp5QBh2 on 2011-07-30
Hi All,

Using Ubuntu 10.10 with gnome. I can't get my UbuntuOne to start! I've searched the forums briefly but couldn't find my problem.

I've tried the conventional method of starting by going to system->preferences->Ubuntu One, and also by clicking the Ubuntu One logo in the top right hand corner under the envelope icon. None of these start Ubuntu One.

I ran this in the terminal```
/usr/lib/ubuntuone-client/ubuntuone-syncdaemon
```

Which gave this output
```
spadge2356@SPADGE2356:~$ /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
ERROR:root:Typelib file for namespace 'Unity' (any version) not found
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gi/importer.py", line 52, in find_module
    repository.require(namespace)
RepositoryError: Typelib file for namespace 'Unity' (any version) not found
ERROR:root:Typelib file for namespace 'Unity' (any version) not found
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gi/importer.py", line 52, in find_module
    repository.require(namespace)
RepositoryError: Typelib file for namespace 'Unity' (any version) not found
Another instance is running
spadge2356@SPADGE2356:~$ ^C
spadge2356@SPADGE2356:~$ 


```

Can anyone give me any guidance as to what's wrong? For the time being I'm getting by with dropbox but would really need my Ubuntu One back.:(

Thanks All,
SPADGE_2356

---

### Post by YfoMp5QBh2 on 2011-07-31
BUMP. anyone?

---

### Post by YfoMp5QBh2 on 2011-08-01
Buuuump!

---

### Post by duanedesign on 2011-08-04
Are you using the version of Ubuntu that came with 10.10 or are you using a version from a PPA?

looks like you need to install the package gir1.2-unity-3.0

thank you,
duanedesign

---

### Post by exfrank on 2012-12-25
i faced the same problem this did the trick for me
i can tell u command line way 
this will sync ur synced folders
firstly:  u1sdtool --list-folders
secondly:  u1sdtool --subscribe-folder=Folder-id

---

