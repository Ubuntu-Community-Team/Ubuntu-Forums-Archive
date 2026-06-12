---
title: "Problema cambio icono menu"
date: 2008-08-13
forum: Software
---

### Post by Cristian CP on 2008-08-13
Hola lista, mi problema es que no puedo cambiar el icono del menu aplicaciones de gnome. Ocurre que instalo algun tema de iconos (x ej. gnome-brave) y me coloca el icono que trae ese tema, pero lo quiero cambiar por otro (el pie o el logo ubuntu). Abro la carpeta del tema en /home/usuario/.icons, carpeta scalable, reemplazo el icono start-here.svg, hago en terminal killall gnome-panel, y no me resulta, continua el icono que puso el tema inicialmente. ¿No deberia resultar o me estoy equivocando de carpeta y el icono esta en otro lado???
Saludos.

---

### Post by faktorqm on 2008-08-13
+1 al reclamo. yo me instale el paquete "linsta" modificado por mi y se me rie en la cara.... algun "themer" que sepa? salu2!!

---

### Post by Mauro22 on 2008-08-13
Para cambiar el icono del menu proba:
[B]
MODO 1:[/B]

```
Alt + F2
```

Ahi pones:

```
gconf-editor
```

Busca esta ruta:

Apps>Panel>objects

Va a ver tantas carpetas como objetos, el menu es la que en "Object_type" dice "menu bar"

Mas arriba de las propiedad dice "custom icon" y ahi pones la ruta al icono y luego mas abajo marcas Use Custom Icon.

Reiniciar el panel


**MODO 2:**

Los iconos se guardan en /usr/share/icons/ aunque tambien estan en .icons

---

### Post by pol666 on 2008-08-13
no modifiques el scalable modifica el 32x32 o 27x27 o el q este acorde al panel que uses

---

### Post by faktorqm on 2008-08-13
ammm ese conf editor me suena tan familiar.... es como ""el registro"" al fin y al cabo.... mmm no se si me gusta....

¿y como hago para achicar el alto de los elementos del menu? asi pongas fuente tamaño 4 a mi me deja el mismo tamaño. grax por la info, salu2!

---

### Post by Tosh78 on 2008-08-14
Mauro tiene razon, yo siempre instalo los iconos en USR-SHARE-ICONS porque los que pones en .icons quedan solo para ese usuario, por que no probas de ponerlo en icons?

---

### Post by Cristian CP on 2008-08-22
Gracias por las respuestas, todavía no lo pudo solucionar, debería intentar repetir algunas de las soluciones que me dieron pero la verdad no he tenido tiempo. Gracias y saludos.

---

### Post by santiagoward2000 on 2008-08-31
> **Mauro22 said:**
> Para cambiar el icono del menu proba:
[B]
MODO 1:[/B]

```
Alt + F2
```

Ahi pones:

```
gconf-editor
```

Busca esta ruta:

Apps>Panel>objects

Va a ver tantas carpetas como objetos, el menu es la que en "Object_type" dice "menu bar"

Mas arriba de las propiedad dice "custom icon" y ahi pones la ruta al icono y luego mas abajo marcas Use Custom Icon.

Reiniciar el panel


**MODO 2:**

Los iconos se guardan en /usr/share/icons/ aunque tambien estan en .icons

Hola!
Estuve probando cambiarlo con el gconf-editor, pero no me lo toma. Ya me fijé que el "Use custom Icon" esté marcado, y revisé la dirección (probé escribiendo toda la dirección para ver si no era el ~/ que molestaba), pero igual no lo cambia. :(

---

### Post by faktorqm on 2008-09-01
No se cambia de ninguna de las 2 maneras. Alguna otra? salu2!

---

