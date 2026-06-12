---
title: "Problema con menú lugares"
date: 2008-10-20
forum: Software
---

### Post by sartrejp on 2008-10-20
Escribo a ver si alguien sabe cual puede ser el problema, o mejor aun, la solución.
Instalé la beta de Intrepid Ibex, y no me funciona el menú "lugares". Se despliega bien, pero cuando elijo una carpeta, no pasa nada, no abre nada.
Si entro en alguna de las carpetas del escritorio, puedo usar la barra lateral que da acceso a las demás, pero el menú no anda.
Si alguien tiene una sospecha aunque sea, será bienvenida

---

### Post by nahuel_89p on 2008-10-21
mmmm la verdad no sabria decirte especificamente a que se debe, pero intuyo que reinstalando el nautilus se soluciona.

---

### Post by WanderingKnight on 2008-10-21
> mmmm la verdad no sabria decirte especificamente a que se debe, pero intuyo que reinstalando el nautilus se soluciona.

Nop, seguramente no.

Creo que ya te conteste por lista de mails, pero [hay un bug reportado](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492) y un fix subido en la revision mas nueva de Nautilus en Intrepid:

> 

This bug was fixed in the package nautilus - 1:2.24.1-0ubuntu1

---------------
nautilus (1:2.24.1-0ubuntu1) intrepid; urgency=low

  * New upstream version:
    - Fix saving of spatial window geometry on close
    - Remove trailing spaces on filenames when copying to FAT file systems
    - Allow emblems that don't start with "emblem-" (lp: #55574)
    - On unmount close tabs that show the unmounted location
    - Fixed redraw issues with labels on zoom
    - Don't toggle sidebar splitter when dragging it
    **- Fix bookmark issue that sometimes led to locations not loading**
    - Don't show the "cancel" dialog after a timeout when displaying a dialog
      (lp: #238425)
    - Fix crashes and leaks
    - Don't change the default association when using a software which is not
      listed by default (lp: #260492)
  * debian/patches/90_correct_spatial_geometry.patch:
    - the change is in the new version

Fijate si podes actualizarte a esa version, si los repositorios todavia no lo tomaron podes probar bajando el .deb del trunk oficial.

---

### Post by sartrejp on 2008-10-22
Dejo la solución por si le pasa a alguien.No se bien porque, pero cuendo descargué las actualizaciones parciales de Ibex, las carpetas del menú lugares quedaron como que se abrían con Wine. En el bug reportado a otros les pasó con openoffice o con otras aplicaciones.
La solución (al menos para mí) fue crear una carpeta en el escritorio, subir hasta el /home hacer click derecho sobre la carpeta de usuario y elegir abrir con nautilus.
Gracias

---

### Post by timbar on 2008-10-26
> **sartrejp said:**
> Dejo la solución por si le pasa a alguien.No se bien porque, pero cuendo descargué las actualizaciones parciales de Ibex, las carpetas del menú lugares quedaron como que se abrían con Wine. En el bug reportado a otros les pasó con openoffice o con otras aplicaciones.
La solución (al menos para mí) fue crear una carpeta en el escritorio, subir hasta el /home hacer click derecho sobre la carpeta de usuario y elegir abrir con nautilus.
Gracias

Funcionó de esta forma, en mi caso se abría con k3b, seguí los pasos de sartrejp, pero en vez de "abrir con" tuve que ir primero a propiedades y dentro de ahí a "abrir con". Ahí estaba marcada la opción de abrir con k3b, le puse "Administrador de archivos" y problema solucionado. Gracias a todos.

---

