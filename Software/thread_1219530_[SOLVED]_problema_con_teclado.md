---
title: "[SOLVED] problema con teclado"
date: 2009-07-21
forum: Software
---

### Post by garijon on 2009-07-21
Hola, tengo una netbook asus eeepc 1000ha, me vino con XP, pero tan pronto pude le instalé ubuntu.
El problema que estoy teniendo es que a pesar que puse que tengo un teclado español (tiene tanto ñ como ç), no me aparecen las tildes cuando tipeo. cuando escribo ´e, no me aparece é.
Probé con todas las variantes de teclado español que encontré con dead tilde, sin ded keys, sin aclaración, etc.
Eligiendo teclado español, las teclas mapean perfecto con las del teclado, el único problema que tengo son las tildes. 
Estoy usando ubuntu jaunty y todos los cambios de configuración los hice usando la gnome y las preferencias de teclado.
Si alguien me puede ayudar realmente se lo agradecería muchísimo.
Saludos

---

### Post by guillermolisi on 2009-07-21
Seguro que esta presionando la tecla del acento y no la del " ' "  que se parecen pero no son lo mismo ?

---

### Post by garijon on 2009-07-21
Si Guillermo, la tecla que estoy probando es efectivamente "´".
Como evidencia adicional, tampoco esta funcionando correctamente la dieresis.
ni ´, ni ¨ esperan a una vocal para acentuarla, sino que se muestran directamente al ser presionadas.
Gracias por la respuesta!
Alguna idea adicional :( ?

---

### Post by NickCis on 2009-07-21
Proba la distribucion del teclado "Latam", no es la española, si no la latinoamericana.

Saludos.

---

### Post by garijon on 2009-07-21
Gracias por la sugerencia.
Lo había probado y lo probé nuevamente, pero el problema con las tildes persiste.
Probé con todas las opciones de teclado en español de hecho y no hubo caso.
En ningún caso funcionan las tildes y dieresis :confused:
Lo dejé en español de nuevo, porque es el único en el cual todas las teclas concuerdan.
Saludos

---

### Post by guillermolisi on 2009-07-22
Recuerdo (uso teclado LATAM standard y todo el software en Ingles pero no tengo problema alguno con los acentos) que cuando se selecciona un teclado hay varias opciones adicionales.

Esto lo ves en Gnome en Preferences - Keyboards. solapa Layouts y ahi deberias ver un boton de Layout options.

Ademas revisa si esta correctamente elegido la marca/modelo del teclado (primera opcion en la solapa Layout).

Tenes, al pie, un campo para probar como resulta la combinacion elegida sin tener que abrir y cerrar ventanas para probar (como en otros sistemas operativos).

---

### Post by garijon on 2009-07-22
Guillermo, yo también uso el sistema operativo en inglés.
Probé todas las opciones dentro de layout tanto de teclado español como latinoamericano. En ningún caso funciona ni con dead tilde, ni con español o latam a secas y hasta probé con without dead keys y obvio no pasó nada.
En la primera parte tengo seleccinado como modelo "asus laptop" (tengo una asus eeepc).
La única opción que encontré para hacer tildes, es poner el teclado en US International y usar el altGr + tecla para hacer las tildes, pero la verdad que no es buena opción, hay muchas teclas que no concuerdan con las del teclado.
Algo más que se les ocurra ?

---

### Post by staar on 2009-07-22
probaste instalar el soporte de idioma para español?

saludos

---

### Post by guillermolisi on 2009-07-22
> **staar said:**
> probaste instalar el soporte de idioma para español?

saludos

Ojo que si esto le cambia el idioma a Español hay que advertirlo ya que dijo utilizar el software en Ingles.

---

### Post by garijon on 2009-07-23
Lo solucioné !!!!
Ante todo quería dar gracias a todos los que me dieron una mano, muchas gracias por las pilas y la buena onda !
El problema no venía por el lado del teclado sino del soporte de idiomas, dentro de Language (donde tengo seleccionado english united States) hay un checkbox que dice "use input method engines (IME) to enter complex characters"
Ese checkbox lo tenía tildado y solo tuve que desactivarlo para que las tildes se comporten como debían. (ojo que toma el cambio cuando te logueas de nuevo.)
En fin, gracias a todos de nuevo.
Saludos,

---

