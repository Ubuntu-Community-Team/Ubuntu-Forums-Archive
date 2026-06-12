---
title: "Firefox 3 soporte p/enlaces ed2k a Amule"
date: 2008-06-05
forum: Software
---

### Post by lega on 2008-06-05
Hola, seguí [esta guía]("http://www.guia-ubuntu.org/index.php?title=Firefox#Soporte_para_el_protocolo_eDonkey2000_.28ed2k.29") que es de Firefox 2 pero no pude hacer que andara en F3b5
> 1. Debes instalar el paquete amule-utils para proporcionar el soporte de enlace ed2k al aMule.

2. Abre Firefox y en la barra de direcciones escribe lo siguiente:

about:config

3. En la lista Nombre de Preferencia haces click con el botón derecho del ratón y elige Nuevo -> Lógico. Ahora hay que crear una nueva preferencia cuyo Nombre de la Preferencia será el siguiente:

network.protocol-handler.external.ed2k

asignándole el valor True.

4. Hacemos nuevamente click con el botón derecho y Nuevo -> Cadena. Como Nombre de la Preferencia ponemos:

network.protocol-handler.app.ed2k

5. Se nos pedirá el path de la aplicación, que en el caso del aMule varía dependiendo de la versión de Ubuntu:

    * En Ubuntu 6.06: /usr/bin/ed2k
    * En Ubuntu 6.10: /usr/bin/amule
    * En Ubuntu 7.04: /usr/bin/ed2k
    * En Ubuntu 7.10: /usr/bin/ed2k 

Listo, ahora podemos hacer clic en los archivos y se añadirán automáticamente a la cola de descargas de aMule.


En Hardy probé con las dos opciones /usr/bin/ed2k , /usr/bin/amule y no paso naranja, alguien que tenga funcionando esta opción me podrá decir como hizo?

Gracias, saludos

---

### Post by faktorqm on 2008-06-05
Para mi es el mismo procedimiento, pero para averiguar eso, busca a donde esta el amule.

```
whereis amule
```

y ahi te tira las posibles ubicaciones. si probas y no anda, busca la opcion que mas se parezca pero con otro programa para saber si la "clave" que estas poniendo esta bien escrita. capaz cambia en el ff3 y es, en lkugar de puntos con guiones bajo... Salu2!

---

