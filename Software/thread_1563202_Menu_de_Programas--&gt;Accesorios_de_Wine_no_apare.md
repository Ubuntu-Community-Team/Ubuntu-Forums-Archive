---
title: "Menu de Programas--&gt;Accesorios de Wine no aparece"
date: 2010-08-28
forum: Software
---

### Post by topito2 on 2010-08-28
Hola,

Decidi actualizar la version de Wine 1.0.1 en mi systema Ubuntu 9.04, por lo que la removi siguiendo con el comando de terminal:

sudo apt-get remove wine 
 
luego removi la carpeta .wine en mi directorio HOME
 
rm -rf .wine 
 
Finalmente, removi la entrada Wine en el menu de Aplicaciones con el Editor de Menus

luego actualice los repositorios instale la version de Wine 1.2 sin ningun problema, pero cuando voy a Aplicaciones--->Wine no aparece la entrada de Programas-->Accesorios

[IMG]http://img291.imageshack.us/img291/1417/myscreenshot1z.png[/IMG]

Que debo hacer para que vuelva a aparecer el menu de Programas--->Accesorios en Wine para correr Notepad comodamente?

he reinstalado Wine varias veces y no se resuelve el problema

Agradezco cualquier ayuda que puedan darme

---

### Post by guillermolisi on 2010-08-29
El procedimiento recomendado es utilizar la opcion "Remover Completamente" para que elimine los paquetes que forman parte de Wine inclusive con sus arvhicos de configuracion.

Borrar entradas de menu, directorios y archivos a mano es una tarea complementaria que deberia hacerse si aun persisten problemas funcionales.

Si tenes instalado Wine, repeti la desinstalacion removiendolo completamente y volve a instalar.

Conta como te fue.

---

### Post by granjero on 2010-08-29
yo eliminé wine así

[http://www.taringa.net/posts/linux/5484346/Eliminar-Wine-por-completo.html](http://www.taringa.net/posts/linux/5484346/Eliminar-Wine-por-completo.html)

y después instalé de nuevo y funciono todo ok

salud!

---

