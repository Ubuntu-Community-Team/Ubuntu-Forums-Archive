---
title: "Problema plugins Compiz en Lucid Lynx!"
date: 2010-05-05
forum: Software
---

### Post by el_eternauta on 2010-05-05
Hola gente, voy a ser lo más directo posible, la cosa es así.

Instalé en limpio Lucid Lynx, instalé códecs, Java, etc., todo iba perfecto hasta que instalé CCSM. El programa funciona bien pero no trae los plugins "Cube reflection", "3D windows", "animations Add-On" entre otros más que no viene al caso nombrar, pero más me importan los dos primeros y por eso quise instalarlos desde Synaptic, creyendo que si no se venían con CCSM deberían instalarse aparte. Busqué en Synpatic "compiz-fusion-plugins-extra" pero al querer instalarlos me daba un error así que decidí hacerlo por consola, ya que en teoría esto resolvería mi problema. Lo hice pero no fue así porque, si bien se instalaron los plugins extras que yo quería, al ir más tarde a "Gestor de actualizaciones" me salió esto:

 [IMG]http://i41.tinypic.com/2ily0dk.jpg[/IMG]

Si le doy en "Actualización parcial" (no tengo opciones) me desinstala los plugins extra que acabo de poner, y si no le doy me quedo sin poder actualizar el sistema porque de ahí no pasa.

¿Alguna idea de donde está el problema?.........Espero haberme explicado bien, muchas gracias por su tiempo. Saludos!

---

### Post by alfplayer on 2010-05-05
> **el_eternauta said:**
> Busqué en Synpatic "compiz-fusion-plugins-extra" pero al querer instalarlos me daba un error así que decidí hacerlo por consola, ya que en teoría esto resolvería mi problema.

Podés explicar esto? Qué error? Por qué pensar que resolvería el problema hacerlo por consola?

---

### Post by el_eternauta on 2010-05-06
Sí, por supuesto, a ver si puedo ser más claro. 

**1.** Tengo CCSM instalado en Lucid Lynx (instalación limpia) pero no tengo los plugins  "Cube reflection", "3D windows", "animations Add-On", entre otros.

**2.** Entonces, como siempre, voy a Synaptic e intento instalar (compiz-fusion-plugins-extra) pero me sale esto:

[IMG]http://i41.tinypic.com/2ily0dk.jpg[/IMG]

**3.** Ni idea de que es compiz-core-abiversion-blablabla así que no hago nada y voy al terminal a ver si puedo instalarlos desde ahí: *sudo aptitude install compiz-fusion-plugins-extra* y me sale esto:
```
~$ sudo aptitude install compiz-fusion-plugins-extra
[sudo] password for arry: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
Los siguientes paquetes están ROTOS:
  compiz-fusion-plugins-extra 
0 paquetes actualizados, 1 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B/2.499kB de archivos. Después de desempaquetar se usarán 9.990kB.
No se satisfacen las dependencias de los siguientes paquetes:
  compiz-fusion-plugins-extra: Depende: compiz-core-abiversion-20090619 que es un paquete virtual.
Las acciones siguientes resolverán estas dependencias

Desactualizar los paquetes siguientes:
compiz-core [1:0.8.6-0ubuntu1~ppa1 (lucid, now) -> 1:0.8.4-0ubuntu15 (lucid)]
compiz-fusion-plugins-main [0.8.6-0ubuntu1~ppa1 (lucid, now) -> 0.8.4-0ubuntu3
(lucid)]
compiz-gnome [1:0.8.6-0ubuntu1~ppa1 (lucid, now) -> 1:0.8.4-0ubuntu15 (lucid)]
compiz-plugins [1:0.8.6-0ubuntu1~ppa1 (lucid, now) -> 1:0.8.4-0ubuntu15 (lucid)]
libcompizconfig0 [0.8.4-0ubuntu3~ppa1 (lucid, now) -> 0.8.4-0ubuntu2 (lucid)]

La puntuación es 140

¿Acepta esta solución? [Y/n/q/?] 

```
**4.** Acepto, instalo y blablabla...(porque aparentemente resuelve solo mi problema). Termina la instalación y soy el hombre más feliz del mundo, con los plugins que quería ya instalados y funcionando. Pero......

**5.** Luego de configurarlos y toda la bola esa, cuando intento actualizar el sistema desde "Gestor de actualizaciones" me sale esto: 

[IMG]http://i41.tinypic.com/vp88r8.jpg[/IMG]

**6. **Y si le doy a "Actualización parcial" se arregla todo y ya puedo actualizar normalmente pero ese proceso me desinstala los plugins que instalé antes por consola, dejándome como al principio, como si no hubiera hecho nada. ¿Me explico ahora? 

**Resumiendo:**  Si vuelvo a instalar los plugins por consola vuelvo a tener el mismo problema con el "Gestor de actualizaciones" creándose así un circulo donde me instala los plugins por un lado pero me los desinstala por otro......y ya me está cansando. 

Espero haber sido más claro esta vez, saludos y muchas gracias por todo.

---

### Post by el_eternauta on 2010-05-06
***La solución es: ***

**1.** Desactivar todas las PPA's que podamos haber agregado a las que vienen por defecto y recargar.

[IMG]http://i41.tinypic.com/34havzp.png[/IMG]

**2. **Abrir **Gestor de paquetes Synaptic** y buscar "compiz"

**3. **Remover todo lo relacionado con "compiz", acá mis capturas:

[IMG]http://i42.tinypic.com/1zgxild.png[/IMG]

***Que sería:***

[IMG]http://i39.tinypic.com/238k2e.png[/IMG]

**"PRESTEN ATENCIÓN A LO QUE VAN A REMOVER, YO REMOVI 11 PAQUETES"**

Luego...

**4. ** Abrir un terminal *(asegurándonos de tener las PPA's desactivadas)* y tipear: 

**sudo apt-get update**

**5. ** Después de eso tipear: 

**sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-backend-gconf**

**6. ** Reiniciar el equipo, instalar CCSM y Emerald.

**Es todo.** Deberán tener Compiz con todos los plugins funcionando 100% como los tengo yo!

¡Saludos!

---

