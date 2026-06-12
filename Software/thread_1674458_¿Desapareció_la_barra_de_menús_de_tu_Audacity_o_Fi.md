---
title: "¿Desapareció la barra de menús de tu Audacity o FileZilla? Encontré la solución."
date: 2011-01-23
forum: Software
---

### Post by daggaz on 2011-01-23
Pues un día instalé Ubuntu Netbook Remix en mi Netbook, no me  gustó y cambié a la versión Desktop. Pero en esto Audacity y FileZilla  sufrieron un feo problema... El menú del programa desapareció, lo cual  me limitaba a tener que utilizar el teclado (cosa no tan problemática  cuando conoces todos los atajos).
Un buen día por pura casualidad me encontré con [éste post en italiano]("http://www.lffl.org/2010/12/ubuntu-scompare-la-barra-dei-menu-con.html"), y aunque no sé nada de italiano, entendí que era mi problema y mi solución.
Es simple:
 En una terminal se escribe:
 ```
export UBUNTU_MENUPROXY=0
``` Luego puedes lanzar el programa:
 ```
audacity
``` Al menos a mi me resolvió el problema.
 Saludos.

---

