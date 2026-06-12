---
title: "Gwibber ne se lance pas"
date: 2011-06-06
forum: Tunisia Team
---

### Post by TheWhiteTiger on 2011-06-06
Bonjour les ubunteros
Encore fidèle à ma Ubunto 10.04 j'ai voulu travailler avec Gwibber,
sauf que ce dernier ne veux plu se lancer :confused:
J'arrive pas à démarrer la fonction de Micro-blogage non plu :(
Essayant de le faire en ligne de commande je reçois ceci :


```
iskander@iskander-laptop:~$ gwibber
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
Apache CouchDB needs a regular PID file: /home/iskander/.cache/desktop-couch/desktop-couchdb.pid
Child returned 1
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
WARNING:root:Reading pid file caused error.  [Errno 5] Erreur d'entrée/sortie: '/home/iskander/.cache/desktop-couch/desktop-couchdb.pid'
ERROR:root:Starting couchdb failed on try 0
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 132, in run_couchdb
    raise RuntimeError("Can not start couchdb.")
RuntimeError: Can not start couchdb.
```

Pouvez vous m'aider svp :roll:

---

### Post by Nizarus on 2011-06-07
regarde la solution proposée ici : 
[https://answers.launchpad.net/gwibber/+question/118886](https://answers.launchpad.net/gwibber/+question/118886)

---

