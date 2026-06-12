---
title: "como acer un ejecutable"
date: 2008-10-24
forum: Software
---

### Post by tsueseres on 2008-10-24
quiero acer un ejecutable de jdownloader esto es con lo que lo abro pero no se como acer el ajecutable

java -jar -Xmx512m /home/luis/programas/JDownloader/JDownloader.jar

---

### Post by juanman on 2008-10-24
1) Abris un editor de textos, por ej, gedit y escribis adentro:
```

#!/bin/bash
java -jar -Xmx512m /home/luis/programas/JDownloader/JDownloader.jar

```

La primera linea indica el programa q va a ejecutar el script, en este caso bash, q es un intérprete de órdenes (tambien llamado shell), el mismo q se ejecuta por defecto cuando abris una terminal.

2) Guarda el archivo en tu home (/home/usuario) con el nombre de jdownloader

3) Hay q darle permiso de ejecucion al archivo. Lo podes hacer desde nautilus con boton derecho -> y en permisos tilda las casillas de ejecucion (tambien se puede hacer desde consola con chmod +x ~/jdownloader)

4) Ahora ya es ejecutable, lo podes ejecutar escribiendo la ruta completa (~/jdownloader). O tambien lo podes mover a las carpetas de los ejecutables, para q lo puedas llamar solo escribiendo jdownloader desde cualquier lugar. Para esto, escribi en consola:
```
sudo mv ~/jdownloader /usr/bin/
```

Y leeesto

---

### Post by tsueseres on 2008-10-25
> **juanman said:**
> 1) Abris un editor de textos, por ej, gedit y escribis adentro:
```

#!/bin/bash
java -jar -Xmx512m /home/luis/programas/JDownloader/JDownloader.jar

```

La primera linea indica el programa q va a ejecutar el script, en este caso bash, q es un intérprete de órdenes (tambien llamado shell), el mismo q se ejecuta por defecto cuando abris una terminal.

2) Guarda el archivo en tu home (/home/usuario) con el nombre de jdownloader

3) Hay q darle permiso de ejecucion al archivo. Lo podes hacer desde nautilus con boton derecho -> y en permisos tilda las casillas de ejecucion (tambien se puede hacer desde consola con chmod +x ~/jdownloader)

4) Ahora ya es ejecutable, lo podes ejecutar escribiendo la ruta completa (~/jdownloader). O tambien lo podes mover a las carpetas de los ejecutables, para q lo puedas llamar solo escribiendo jdownloader desde cualquier lugar. Para esto, escribi en consola:
```
sudo mv ~/jdownloader /usr/bin/
```

Y leeesto


gracieas

---

### Post by juanman on 2008-10-25
[QUOTE=tsueseres]gracieas[/QUOTE]

Apreta en la medallita abajo a la derecha de mi post, q lo quiero alcanzar a faktor :lolflag:

---

### Post by pol666 on 2008-10-25
Hacer :$

---

### Post by EnriqueK on 2008-10-25
Click secundario sobre el escritorio, en el menú contextual -> Crear un Lanzador , en el cuadro de opciones aparecen:
1.- Tipo : No sabría decir exactamente cual corresponde, probá primero con **Aplicación** , después en caso de no funcionar elige **Aplicación en terminal** .
2.- Nombre: es a voluntad, podrías ponerle JDownloader
3.- Comando: java -jar -Xmx512m /home/luis/programas/JDownloader/JDownloader.jar

Quedaría un último paso (opcional) que es pulsar sobre la imagen y así editar el ícono que tendrá el lanzador, le puedes poner cualquiera de la lista que se abre o poner el que corresponde cuya ruta sería /home/luis/programas/JDownloader/jd/img/jd_logo.png
(esto de la ruta del ícono tendrías que verificarlo, pero creo que es esa de acuerdo con los datos que diste).

Otra posibilidad es poner el lanzador en menú Aplicaciones, para hacer eso , click secundario sobre el menú Aplicaciones  -> Editar los menús -> Elige una categoría por ejemplo Accesorios -> +Elemento Nuevo , lo que sigue son los mismos pasos explicados para crear el lanzador en el escritorio.

---

