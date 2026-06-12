---
title: "Eliminar programa compilado"
date: 2008-11-21
forum: Software
---

### Post by erdosain9 on 2008-11-21
Hola pues quería saber cómo se elimina un programa que instalé compilandolo creo... lo que hice fue "sudo python setup.py install"... y con eso se mando todo un choclo... ahora quiero eliminarlo... cómo hago???
Saludos y gracias

---

### Post by Hernán-Amaya on 2008-11-21
fijate en el readme o leeme del programa, tiene que tener algún unisntall o alguna forma de desinstalar,

---

### Post by arielcabral on 2008-11-21
Por la poca info de versión que das, puede que se resuelva con:

sudo apt-get autoremove python

Espero que sirva

---

### Post by chalito on 2008-11-21
Hmm eso borraría a python. Si entendí bien, él instaló un programa cuyo installer corría en python.

Por lo pronto lo mejor es leer la documentacion del programa a ver si dice explicitamente como desinstalarlo. Si no dice nada, podrias probar haciendo:
sudo python setup.py

como cuando se instaló, pero sin el "install" al final. eso probablemente te diga que opciones soporta setup.py. Con algo de suerte existe un "sudo python setup.py uninstall" o algo así

---

### Post by Hei Ku on 2008-11-21
Lo mas razonable es que se desinstale con:

sudo python setup.py uninstall

Pero los craneos de python que tenemos en el foro nos pueden orientar mejor.

---

### Post by arielcabral on 2008-11-22
Así es Hei Ku, pero no siempre sucede así y erdosain9 no nos ha dado info suficiente...

---

### Post by hictio on 2008-11-22
A todo esto, que programa es??? La intriga me carcome :D

---

