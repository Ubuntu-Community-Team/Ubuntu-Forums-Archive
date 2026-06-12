---
title: "Problema compialdor pascal y ubuntu"
date: 2009-11-09
forum: Software
---

### Post by ramiro_md on 2009-11-09
Buenas, esta mañana instalé el Free Pascal Compiler para hacer los trabajos de la facu. Bueno, el problema es que a pesar de compilar bien los códigos, cuando los ejecuto en la consola me devuelve lo siguiente:
```

* Free Pascal IDE Version 1.0.10 [2009/06/04]
* Compiler Version 2.2.4-3
Running "/media/Datos/Ramiro/Documentos/Facultad/ADP/Compilaciones/listas/merge"
/bin/sh: /media/Datos/Ramiro/Documentos/Facultad/ADP/Compilaciones/listas/merged
 Press any key to return to IDE

```
Y no puedo probar el programa. El .pas es compilado en una partición ntfs pero tengo los permisos para escribir en esa partición asique no sé bien que más podría ser.
ESpero que me peudan dar una mano. Saludos.

Nopta: en win$ compilan y los ejecuto lo más bien :S.

---

### Post by Mauro22 on 2009-11-09
Me da la impresion que la ruta es muy larga... los compiladores tienen problemas si la ruta supera los 256 caracteres....


Alguna vez te adubo bien, con esas rutas?

---

### Post by ramiro_md on 2009-11-09
> **Mauro22 said:**
> Me da la impresion que la ruta es muy larga... los compiladores tienen problemas si la ruta supera los 256 caracteres....


Alguna vez te adubo bien, con esas rutas?

Sisi, en debian tanto stable como testing me andaban bien, sin ir más lejos en hardy también solía andar je.
Voy a ver si compilo en el /home :).
Gracias.

---

### Post by guillermolisi on 2009-11-09
En el mensaje que citas veo que hay una pequeña diferencia que marco en color:
> Running "/media/Datos/Ramiro/Documentos/Facultad/ADP/Compilaciones/listas/merge"
/bin/sh: /media/Datos/Ramiro/Documentos/Facultad/ADP/Compilaciones/listas/merge[COLOR=Red]d[/COLOR]

Esta bien eso o sobra o falta una "d" en el path ?

---

### Post by ramiro_md on 2009-11-09
Guille yo también noté eso, pero cuando abro el .pas desde el compilador y lo ejecuto ya me devuelve eso :S

EDIT: Compilé desde el /home y funcionó. Un saldo.

---

