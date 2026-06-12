---
title: "El Problema Firefox/Compiz Definitivo"
date: 2009-04-13
forum: Software
---

### Post by nemodot on 2009-04-13
Buenas, hace poco pregunte esto y me respondieron, pero linkeaba a un sitio que da error y no encuentro una alternativa en ningun nado.

Como corrigo el problema que tiene firefox cuando compiz está activado?

Me refiero al que la ventana de firefox ocupa toda la pantalla y no te da acceso a los paneles a menos que hagas F11 dos veces.

---

### Post by josecuervo86 on 2009-04-13
Hola, mira, yo la "solucion definitiva" la encontre en el compiz. Anda al **administrador de opcicones de Compiz** (Sistema-Preferenecias-Administrador de Opciones Compizconfig). Despues anda a **utilidades**, **Entorno de trabajo** y **desmarca** la opcion **Soportar legacy panatalla completa**.

Espero que te funcione

---

### Post by guisheca on 2009-04-14
Yo te voy a dar la solución definitiva para para firefox y todos los demás programas donde esto ocurra.
Tenés que ejecutar metacity primero que nada (apretá alt+F2 y escribí ```
metacity --replace
``` ), y con metacity como gestor de ventanas desmaximizá firefox y redimensionalo a un tamaño mas chico del que esté. Despúes volvé a ejecutar compiz ( ```
compiz --replace
``` ) y el problema tendría que estar solucionado.
La solución que postea josecuervo no la conocía, la próxima ves que me pase la voy a probar, parece mas sensata que la mía :p.
Saludos.

---

### Post by nemodot on 2009-04-14
Benditos sean los dos, gracias. :guitar:

---

