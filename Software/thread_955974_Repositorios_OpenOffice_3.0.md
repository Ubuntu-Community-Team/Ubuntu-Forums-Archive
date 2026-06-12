---
title: "Repositorios OpenOffice 3.0"
date: 2008-10-22
forum: Software
---

### Post by gmunioz on 2008-10-22
Hola estos son los repositorios para actualizar OpenOffice a la versión 3.0 solo en Hardy o Intrepid

Para Hardy
> 
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main


Para Intrepid
> 
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main


Saludos. Gabriel.

---

### Post by guisheca on 2008-10-22
Huuu grosísimo!!! muchas gracias!!! me re sirve

---

### Post by sebastianabate on 2008-10-22
Alguno pudo usar estos repositorios? Porque a mi me figuran vacíos los archivos Packages y Packages.gz de este repositorio para Hardy (los de Intrepid están bien).

Tengo configurado apt para que se saltee el proxy transparente de Fibertel, pero igual me figuran vacíos estos archivos; aunque puedo bajar los .deb individualmente (pero prefiero actualizar con apt)

---

### Post by guisheca on 2008-10-22
> **sebastianabate said:**
> Alguno pudo usar estos repositorios? Porque a mi me figuran vacíos los archivos Packages y Packages.gz de este repositorio para Hardy (los de Intrepid están bien).

Tengo configurado apt para que se saltee el proxy transparente de Fibertel, pero igual me figuran vacíos estos archivos; aunque puedo bajar los .deb individualmente (pero prefiero actualizar con apt)

Yo no se si esto tiene algo que ver con lo que decis, pero ya agregué los repos y no se como se supone que actualice, no me sale nada del openoffice 3 para instalar ni actualizar ni nada.
Tengo hardy.

---

### Post by santiagofrias on 2008-10-22
A mi tampoco, recién agregué los repositorios pero de actualización...nada
Sigue figurando como OpenOffice 2.4
Si alguien sabe algo más avisen.

---

### Post by sebastianabate on 2008-10-22
No, a mi no me dice que tengo algo para actualizar.
Si abrís synaptic y elegís el botón "origins", te aparece el Openoffice 3 entre los paquetes que están en ppa.launchpad.net/main? porque se supone que tiene que aparecer en ese apartado, pero a mi me aparecen otros paquetes (de otros repositorios de ppa que tengo configurados) pero nada de Oo.

---

### Post by santiagofrias on 2008-10-22
Es verdad, a mi tambien me aparecen otros paquetes pero nada de Oo.
Pueden verlo en la imagen a ver si alguien nos dice que puede estar ocurriendo
Saludos

---

### Post by majatu on 2008-10-22
Como los repos no estan todabia yo lo actualice siguiendo una guia que postie en otro theread:

El thread original es:
[http://ubuntuforums.org/showthread.php?t=947032&page=2]("http://ubuntuforums.org/showthread.php?t=947032&page=2")

Haganlo tranquilos que les va a andar de 10!

Saludos

---

### Post by guisheca on 2008-10-22
Ma si, ya lo actualicé manual nomas como dijo majatu y que san pu*** se lo lleve. Por cierto, arranca a los ped**** !!!
Saludos.

---

### Post by guisheca on 2008-10-22
Alguien mas no tiene las transiciones 3D en el impress como yo?? prometí mostrarlas mañana en una exposición, me empiezo a poner nervioso[-o<[I]

edit: ya fue, instalé las transiciones en el 2.4 despues veo como soluciono lo otro.
Tamañana[/I]

---

### Post by sebastianabate on 2008-10-23
Bueno, después de hacer un exhaustivo trabajo de investigación, agregando y quitando el susodicho repositorio del apt, borrando el cache de paquetes, hasta intenté colgarme de la conexión inalámbrica de un vecino para descartar que la culpa fuera de Fibertel, y sin llegar a ninguna conclusión, se me ocurrió entrar a la página del ppa propiamente dicho [https://launchpad.net/~openoffice-pkgs/+archive]("https://launchpad.net/%7Eopenoffice-pkgs/+archive"), y me encuentro con esto:

> **PPA for OpenOffice.org Scribblers**

                                          
        **URL: [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)**

                          OpenOffice.org 3.0.0 - INTREPID ONLY

[Grito a mi mismo] ES ÚNICAMENTE PARA INTREPID ESE PPA, SALAME!!!!!! [/Grito a mi mismo]

Entonces, cuando estaba a punto de aplastarme los "dedos" con la puerta, se me ocurrió probar nuevamente con los .deb de la página oficial. Había descartado esta opción porque con estos .deb no hay integración con el escritorio (una vez instalados no reemplazan a los anteriores, y hay que volver a asociar los formatos de archivos con los ejecutables que se instalan en /opt/openoffice.org3/programs); pero me fijé con qué ejecutable estaban asociados los formatos de Oo, y me encuentro con que es un script que está en /usr/bin/ooffice, cuyo contenido para la versión 2.4 es

```
#!/bin/sh
/usr/lib/openoffice/program/soffice  "$@"
```lo cambié por

```
#!/bin/sh
#/usr/lib/openoffice/program/soffice  "$@"
/opt/openoffice.org3/program/soffice  "$@"
```y listo, ahora cuando le doy un doble click a algún archivo asociado con Oo, o elijo alguna de sus aplicaciones del menú, arranca el Oo3.

NOTA: no hay que instalar .deb que está en la carpeta desktop-integration del archivo bajado de la página oficial, y yo no desinstalé el Oo2.4 porque según leí también desinstala el paquete ubuntu-desktop, y es necesario para actualizar a Intrepid cuando sea el momento. Y lo que más contento me pone es que mis "dedos" están intactos.

---

