---
title: "Problemas con Compiz"
date: 2009-02-11
forum: Software
---

### Post by nemodot on 2009-02-11
Buenas, tengo dos problemas con compiz que no sé como solucionar.

El primero se debe a un amigo que tiene un cuestionable gusto estético y un día vino a casa y me instalo emerald, el cual adorna los bordes de las ventanas cuando tenés Compiz activado. A mi no me gustó y lo desinstale desde el Synaptic (lo busque y eliminé). El problema es que ahora cuando activo Compiz no tengo borde de ventana. :( Como puedo hacer para volver a tener todo como antes de instalar emerald?

El segundo problema que tengo con Compiz es que a veces cuando abro el firefox este me ocupa toda la pantalla incluidos los margenes superior e inferior de tal forma que no podes acceder al borde superior para cerrar o minimiazar la ventana, es realmente incomodo y todavía no le encuentro corrección. 

Un saludo!

---

### Post by sajnox on 2009-02-11
> **nemodot said:**
> Buenas, tengo dos problemas con compiz que no sé como solucionar.

El primero se debe a un amigo que tiene un cuestionable gusto estético y un día vino a casa y me instalo emerald, el cual adorna los bordes de las ventanas cuando tenés Compiz activado. A mi no me gustó y lo desinstale desde el Synaptic (lo busque y eliminé). El problema es que ahora cuando activo Compiz no tengo borde de ventana. :( Como puedo hacer para volver a tener todo como antes de instalar emerald?

Entras en el settings manager de compiz y en windows decorations donde dice emerald escribis metacity --replace


> 
El segundo problema que tengo con Compiz es que a veces cuando abro el firefox este me ocupa toda la pantalla incluidos los margenes superior e inferior de tal forma que no podes acceder al borde superior para cerrar o minimiazar la ventana, es realmente incomodo y todavía no le encuentro corrección. 

Un saludo!

Aca (0) esta la solucion a ese problema, me volvio loco un par de dias

(0) [http://www.tomechat.cl/linux/?p=157](http://www.tomechat.cl/linux/?p=157)

---

### Post by nemodot on 2009-02-11
Dice "emerald" pero en /usr/bin/emerald

Reemplace por /usr/bin/metacity --replace pero no se activa compiz y vuelve a <<Nimguno>> en efectos de escritorio.

---

### Post by luks911 on 2009-02-11
> **nemodot said:**
> Dice "emerald" pero en /usr/bin/emerald

Reemplace por /usr/bin/metacity --replace pero no se activa compiz y vuelve a <<Nimguno>> en efectos de escritorio.

Me parec que el problema es el "--replace", probá de dejar solo
```
/usr/bin/metacity
```
Cualquier cosa avisá, que llego a casa y puedo chequear cómo lo tengo.

---

### Post by nemodot on 2009-02-11
No, eso no funciona, pero pude corregirlo al final. Hice click en la escobilla que restaura los valores por defecto y ya esta. :)

Solved!

---

### Post by luks911 on 2009-02-11
Cierto, 
```
/usr/bin/compiz-decorator
```

Saludos

---

### Post by sajnox on 2009-02-12
Perdon te dije metacity y con eso estas desactivando compiz y usas metacity

La linea es (o por lo menos eso recuerdo)

gtk-window-decorator --replace

---

