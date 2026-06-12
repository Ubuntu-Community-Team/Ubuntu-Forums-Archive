---
title: "Dudas de configuracion"
date: 2010-06-03
forum: Software
---

### Post by lisayepes on 2010-06-03
Buenas tardes me presento en sociedad mi nombre es Lisa.
Necesito configurar 3 maquinas en UBUNTU 10.04 para que compartan carpetas - archivos - e impresoras con maquinas en red Windows con instalación de Windows 7 y Windows XP.
La situación es la siguiente
Las Linux deben poder imprimir e ingresar a maquinas WIN 7 y con todas las win compartir archivos y carpetas mutuamente.
Tengo una conexión a internet por red wi fi que conecta sin problemas y las maquinas win forman una red de trabajo.
POR FAVOR sin consola y lo mas sencillo posible como puedo hacer para que esto se implemente.
Aguardo sus sabias respuestas.

Lisa

---

### Post by guillermolisi on 2010-06-03
Hola Lisa

Para que una maquina con Linux forme parte de una red de grupo Win tenes que usar Samba cuya parte cliente se incluye en la instalacion de Ubuntu.

Comparti recursos en las maquinas Win y en la que tiene Ubuntu, asi se publicaran y las veras como parte del grupo de trabajo. Si pones el nombre de una maquina Win en Nautilus y te da error, proba haciendo que la busque poniendole la direccion IP en lugar del nombre de maquina.

Las impresiones se deben hacer en impresoras de red, en impresoras que estan conectadas a PCs con Windows o en impresoras conectadas a maquinas con Ubuntu ?

---

### Post by ahtv on 2010-06-23
Lisa / Guillermo, yo necesito hacer lo mismo, ya monté la impresora, es una HP 5600 all in one, utilice SAMBA para darla de alta, mando la impresión de prueba, la impresora se mueve, hace todo como si fuera a imprimir y al final parece que se queda esperando datos por toda la eternidad....

entonces me supongo que es algo mas que la configuración de la impresora.

Tienen algo?

Gracias de antemano y Saludos
Adrián Torres

---

