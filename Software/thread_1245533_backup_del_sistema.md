---
title: "backup del sistema"
date: 2009-08-20
forum: Software
---

### Post by tsueseres on 2009-08-20
hola cuales son los mejores programas para hacer respaldos de todo el sistema

---

### Post by dirty fingers on 2009-08-20
si con "todo" te referís a todo :P (mas que solo el /home) lo mejor es usar clonezilla. Muy similar a lo que seria norton ghost para windows.

---

### Post by tsueseres on 2009-08-21
> **dirty fingers said:**
> si con "todo" te referís a todo :P (mas que solo el /home) lo mejor es usar clonezilla. Muy similar a lo que seria norton ghost para windows.

y que tal esta el remastersys

---

### Post by EnriqueK on 2009-08-21
Si querés hacer un respaldo de toda una partición o de todo un disco, sin dudas recomiendo el clonezilla y mas concretamente la variante clonezilla-jaumty ya que es capaz de reconocer el nuevo sistema de archivos EXT4 -
[http://sourceforge.net/projects/clonezilla/files/](http://sourceforge.net/projects/clonezilla/files/)
El Remastersys si bien también sirve para respaldo del sistema, su función principal es el de crear un CD / DVD  para que pueda ejecutarse y/o instalarse en otra PC , pero esto tiene un limitante y es que para poder ser ejecutado en otra PC,  no respalda algunas configuraciones y sobretodo los drivers de la gráfica, nada de esto es trabajoso de retocar, pero tenés que hacerlo y lleva su tiempo.
También está la posibilidad de crear tu propio Script para hacer respaldos de algunas carpetas importantes como ser tu /home /etc y otras que veas conveniente.

---

### Post by kornykyano on 2009-08-21
Creo que lo mejor es **rsync** [http://rsync.samba.org/](http://rsync.samba.org/)

**apt-get install rsync**

Y si lo queres con GUI **Grsync**

**apt-get install grsync.**

Muy buena herramienta, diria que casi fundamental.

---

