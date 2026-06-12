---
title: "Problema pascal =S"
date: 2008-07-07
forum: Software
---

### Post by ramiro_md on 2008-07-07
Gente, se que no tiene nada que ver lo que voy a preguntar con ubuntu,(aunque estoy usando fp en ubuntu =P) pero se que me pueden ayudar :$. Resulta que estoy haciendo unos practicos de la facu, y tengo q declarar una pila..lo que hago es lo siguiente:
"TYPE pila = stack of integer;"
Y me marca "stack" como indicador desconocido =O..que sucede ?? que hago mal ?? en las teorias estan declaradas asi ! =S..Help ! jejeje

---

### Post by Federick on 2008-07-07
Me suena que stack (pila) es una estructura de datos que tenés que implementar con una lista.
No es tan simple su declaración:
[http://holamundopascal.blogspot.com/2007/08/capitulo-7_24.html](http://holamundopascal.blogspot.com/2007/08/capitulo-7_24.html)

Pero igual me parece que lo que te piden es una pila con un vector.
TYPE pila= array[1..tanto] of integer;
[http://www.elo.utfsm.cl/~lsb/pascal/clases/cap23.pdf](http://www.elo.utfsm.cl/~lsb/pascal/clases/cap23.pdf)


Suerte!

---

### Post by Hernán-Amaya on 2008-07-07
Primero no existe una estructura llamada stack la tenes que crear vos. Si sabés como funciona una pila podes implementarla con un vector o con una estructura dinámica. cualquier cosa si queres mandame un privado para no hacer ruido en el foro

---

