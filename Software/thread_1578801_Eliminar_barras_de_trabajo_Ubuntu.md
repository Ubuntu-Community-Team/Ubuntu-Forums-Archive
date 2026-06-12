---
title: "Eliminar barras de trabajo Ubuntu"
date: 2010-09-21
forum: Software
---

### Post by pablondon on 2010-09-21
Hay una forma de eliminar todas las barras y dejar un programa que sea como el Cairo Dock sin necesidad de esconderla? 

Gracias

---

### Post by RafaelG on 2010-09-21
> **pablondon said:**
> Hay una forma de eliminar todas las barras y dejar un programa que sea como el Cairo Dock sin necesidad de esconderla? 

Gracias


Pablondon,

Simplemente eliminas la Barra haciendo **Click** **Derecho sobre barra > Eliminar Barra** y utilizas el Cairo Dock que mencionaste o el Gnome Do que tambien es muy buena alternativa para disparar tus diferentes aplicaciones o carpetas personales.

Saludos!

---

### Post by pablondon on 2010-09-21
Esque si borro una, siempre me queda otra barra, ese es el problema en realidad

---

### Post by themasterdark on 2010-09-22
No se pueden eliminar, solo esconderlas, saludos =)

supongo debes saber como ya que lo mencionaste anteriormente.

sino en google esta la info facilmente =D

---

### Post by Carlos C on 2010-09-24
Entiendo que se puede llegar a eliminar el último panel si quitas los permisos de ejecución de /usr/bin/gnome-pane. El problema de hacerlo radica en que ya no podrás acceder a la aplicación "Ejecutar una aplicación" cuando presionas ALT+F2

Saludos.

---

### Post by themasterdark on 2010-09-25
probé con los permisos en gnome-panel, pero de todos modos se ejecuta, así que bueno a ocultarlos solamente jaja 

Saludos =)

---

### Post by moreback on 2010-09-26
Si alguien quiere probar, podría editar los valores de** /desktop/gnome/session/required_components_list** con **gconf-editor**. Ahí hay una opción de "**panel**" que si miran en **/desktop/gnome/session/required_components/panel** contiene el valor **gnome-panel**. A lo mejor cambiando su valor al nombre del ejecutable del dock usado puede ser que hagan que no se ejecute más el panel de Gnome.

Saludos.

---

