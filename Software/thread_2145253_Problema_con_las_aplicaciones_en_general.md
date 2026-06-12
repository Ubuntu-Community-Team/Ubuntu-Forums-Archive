---
title: "Problema con las aplicaciones en general"
date: 2013-05-14
forum: Software
---

### Post by maxinnn1 on 2013-05-14
Holis soy nuevo en el foro y nuevo en linux en general, comienzo a aprender poco a poco. Bueno tengo este problema hace poco cuando quiero instalar y desinstalar programas, tal como wine etc etc

me aparece esto

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 972, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1096, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

bueno no se como solucionarlo ya que no me deja instalar o desinstalar nada, diganme si nesesitan algo adicional

---

### Post by maxinnn1 on 2013-05-14
Ah me olvide tengo el ubuntu 11.10

---

### Post by MeduZa on 2013-05-15
Nunca vi ese error pero sigamos el tip que te da el system error:

proba esto:
desde synaptics desinstala mscorefonts

o sino desde terminal
sudo apt-get remove --purge mscorefonts & apt-get install mscorefonts

---

### Post by maxinnn1 on 2013-05-15
Gracias MeduZa, ya fue solucionado, instale actualizaciones y se arreglo, yo soy re novato en este tema pero voy aprendiendo leyendo cosas gracias igual

---

