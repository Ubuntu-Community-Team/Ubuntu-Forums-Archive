---
title: "problema con openoffice.org"
date: 2009-07-09
forum: Software
---

### Post by zhelo on 2009-07-09
bhueno chicos, queria actualizar mi openoffice 3 al 3.1 y me base en esta guia
> 

[http://www.tuxapuntes.com/drupal/node/1391](http://www.tuxapuntes.com/drupal/node/1391)

el problema es que me bajo puros paquetes malo :O
revise el post y vi que los tipos que posteaban tambien tenian erroes, asi que me dipuje a borrar lo que habia instalado mal

tuve que borrar el openoffice... borre los pauqtees malos para no tener problemas, y quise bajar openoffice por synatic pero...
me sale esto:
> No se puede marcar todos los pauqtes para la instalacion.
los siguientes pauqtes tiene dependencia no resoluble. Asegurese que estan añadidos y activados todos los repositos en prefercias

luego eso:

openoffice.org:
  Depende: openoffice.org-core (=1:3.0.1-9ubuntu3) pero se va a instalar 1:3.1.0-5ubuntu1~jaunty1
 Depende: openoffice.org-impress pero no va a ser instalado
 Depende: openoffice.org-draw pero no va a ser instalado
 Depende: openoffice.org-base pero no va a ser instalado
 Depende: openoffice.org-report-builder-bin pero no va a ser instalado
 Depende: openoffice.org-officebean pero no va a ser instalado
 Depende: openoffice.org-writer2latex pero no va a ser instalado
 Recomienda: openoffice.org-filter-binfilter pero no va a ser instalado

y no se instala
luego trato con agregar o quitar

i sale esto:

> No se pudo instalar «openoffice.org»

Esta aplicación entra en conflicto con otro software ya instalado. Para instalar «openoffice.org», debe desinstalar primero el software conflictivo.

Cámbiese al gestor de paquetes Synaptic para resolver este conflicto.alquien sabe que paso?

---

### Post by radixs on 2009-07-09
> **zhelo said:**
> [COLOR=Red]bhueno chicos, queria actualizar mi openoffice 3 al 3.1 y me base en esta guia

[/COLOR]

[COLOR=Red]el problema es que me bajo puros paquetes malo :O
revise el post y vi que los tipos que posteaban tambien tenian erroes, asi que me dipuje a borrar lo que habia instalado mal

tuve que borrar el openoffice... borre los pauqtees malos para no tener problemas, y quise bajar openoffice por synatic pero...
me sale esto:

[/COLOR][COLOR=Red]y no se instala
luego trato con agregar o quitar

i sale esto:

[/COLOR]alquien sabe que paso?
[COLOR=Red]
[/COLOR]

Aun tienes agregados los repos que agregaste a la sources.list?
Porque no revisaste los comentarios antes?

---

### Post by zhelo on 2009-07-09
> **radixs said:**
> Aun tienes agregados los repos que agregaste a la sources.list?
Porque no revisaste los comentarios antes?


los repositos  de sofware de terceros ya los borre, no se si seran los mismo que los de sources.list
[http://i29.tinypic.com/30j6ypi.png](http://i29.tinypic.com/30j6ypi.png)

---

### Post by radixs on 2009-07-09
> **zhelo said:**
> los repositos  de sofware de terceros ya los borre, no se si seran los mismo que los de sources.list
[http://i29.tinypic.com/30j6ypi.png](http://i29.tinypic.com/30j6ypi.png)

Mejor muestranos tu sources.list

```
sudo gedit /etc/apt/sources.list
```

---

