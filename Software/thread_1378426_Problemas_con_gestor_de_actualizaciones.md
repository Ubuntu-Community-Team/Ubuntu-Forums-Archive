---
title: "Problemas con gestor de actualizaciones"
date: 2010-01-11
forum: Software
---

### Post by asterix77 on 2010-01-11
Estimados:

Les comento que intenté instalar un paquete con extensión .run, especificamente vodafone-mobile-conect-card-driver.run. Al correrlo, en forma automática se descargaron dependencias, las cuales se instalaron (fueron muchas), sin embargo a pesar de ello hubieron errores por lo que finalmente no se instaló (mucho mas tarde encontré un paquete .deb que si se instaló sin problemas). Lo curioso es que ahora me apareció el gestor de actualizaciones con nuevas actualizaciones, pero que no puede actualizarlas. Me aparece un cuadro de diálogo que dice lo siguiente:

No se pueden instalar todas las actualizaciones

Run a partial upgrade, to install as many updates  as possible

This can be caused by:

*A previous upgrade which didn´t complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu

Al aceptar la actualización parcial, al final de un largo escaneo de mi notebook, me aparece otro cuadro de diálogo en el que se me indica que se van a desinstalar 70 paquetes, instalar 7 paquetes nuevos y actualizar 46 paquetes.

Si llegara a aceptar me quedo sin SO, ya que se desintalaría open office, network manager, todos los linux-image más el generic, samba, evolution, banshee, etc, etc.

Creo que el error está en los paquetes que se descargaron cuando intenté ejecutar el archivo run, pero no sé cuales son para desinstalarlos, porque fueron muchos.


Les solicito su ayuda para poder resolver esto.  Uso karmic amd64

Gracias de antemano


PD: el archivo instalado run, me apareció en synaptic después de ejecutado, así es que lo eliminé por esta vía antes de instalar el deb.

---

### Post by Carlos C on 2010-01-11
Prueba con este comando:
```
sudo dpkg -C
```
Trata de copiar el error acá para que podamos identificar exactamente el paquete con problemas.

Saludos.

---

### Post by asterix77 on 2010-01-13
Gracias Carlos.

Bueno finalmente les cuento cual había sido mi problema. Al tratar de correr el paquete run, en primera instancia me arrojó problemas de dependencias que no se instalaban porque no se encontraban en el repositorio. Entonces me fui al repositorio de debian lenny, en el cual si estaban muchos de los que me faltaban; y como eran muchos simplemente para no bajarlos uno a uno lo agregué al repositorio, actualicé y descargué los paquetes necesarios (igual no me funcionó el programa por lo que seguí buscando hast encontrar el paquete .deb).

Al haber nuevas actualizaciones, (día siguiente), se me presentó el error. Lo que finalmente hice fue desmarcar el repositorio de debian, actualizar, correr el gestor de actualizaciones, con lo que ya el error desapareció.

Saludos y se agradecen los comentarios

---

