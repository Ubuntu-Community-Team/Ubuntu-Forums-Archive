---
title: "CloneZilla y EXT4"
date: 2009-05-11
forum: Software
---

### Post by EnriqueK on 2009-05-11
Quisiera saber si alguien a probado la última versión del CloneZilla y puede decir si este clonador de particiones reconoce el nuevo sistema de arcchivos ·EXT4

---

### Post by juancarlospaco on 2009-05-11
EXT4 se puede montar como EXT3, hay Clonezilla basado en Jaunty en SourceForge.

---

### Post by EnriqueK on 2009-05-11
Gracias por el dato, voy a probar como se comporta Clonezilla basado en jaunty.

---

### Post by z37a on 2009-05-11
> **juancarlospaco said:**
> EXT4 se puede montar como EXT3, hay Clonezilla basado en Jaunty en SourceForge.

Me parece que no, durante el periodo de jaunty en alpha y beta rompi al sistema varias veces y si intentaba recuperar desde un ubuntu 8.10 no podia montar las unidades!!!!

---

### Post by juancarlospaco on 2009-05-12
Me parece que si, lee la Documentacion...

---

### Post by sebastianabate on 2009-05-12
EXT4 se puede montar como EXT3 siempre y cuando no se usen las opciones específicas de EXT4. Esto quiere decir que si usás EXTENTS en tu EXT4 no lo vas a poder montar como EXT3.

Extracto sacado de [http://es.wikipedia.org/wiki/Ext4](http://es.wikipedia.org/wiki/Ext4)
** Compatibilidad hacia atrás**

 Ext4 es parcialmente compatible hacia atrás con ext3 ya que puede ser montado como una partición ext3 con la excepción de que si la partición ext4 usa extents, se pierde esta posibilidad. Extents están configurados por defecto desde la versión del kernel 2.6.23. Anteriormente, esta opción requería ser activada explícitamente (por ejemplo mount /dev/sda1 /mnt/point -t ext4dev -o extents).
 
 [B] 
[/B]

---

### Post by Ericyzfr1 on 2009-05-12
Se puede utilizar Clonezilla 1.2.2-2 con ext4. Functiona muy bien para me.

---

### Post by juancarlospaco on 2009-05-12
[**Clonezilla Jauntizado por aqui...**]("http://sourceforge.net/project/showfiles.php?group_id=115473&package_id=233347")

---

### Post by EnriqueK on 2009-05-12
Ya lo bajé y lo probé, al parecer faltan algunas opciones como ser el de poder elegir el grado de compresiónj, pero de todas maneras está fijado en las opciones que uso, así que todo bien.
Aprovecho de preguntar que antes de dar la orden de proceder a crear la imagen , el programa indica que en el futuro uno puede agilizar el proceso de definir las opciones mediante un comando que lo muestra en pantalla y además indican un archivo dentro de /tmp, lo que quisiera saber es como accedo al terminal para introducir estos comandos y como hago para copiae estos comandos desde un medio removible o de alguna partición del DD, sería buenísimo poder hacer esto, ya que con esto verdaderamente se agililizaría el processo de conformar las opciones.

---

